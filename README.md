### Discord Url Durum

```js
const Discord = require('discord.js');
const client = new Discord.Client();

client.on('presenceUpdate', (oldPresence, newPresence) => {
  const url = 'eis';       // durumlarında gözükecek url adı.
  const roleid = '';      // durumuna url alanlara verilecek rol id.

  const hasTargetStatus = newPresence.activities.some(activity => activity.name === url);

  if (hasTargetStatus) {
    if (!newPresence.member.roles.cache.some(role => role.id === roleid)) {
      newPresence.member.roles.add(roleid).catch(console.error);
    }
  } else {
    if (newPresence.member.roles.cache.some(role => role.id === roleid)) {
      newPresence.member.roles.remove(roleid).catch(console.error);
    }
  }
});
