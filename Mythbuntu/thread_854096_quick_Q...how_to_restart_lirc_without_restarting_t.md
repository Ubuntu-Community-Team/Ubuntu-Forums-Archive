---
title: "quick Q...how to restart lirc without restarting the comp?"
date: 2008-07-09
forum: Mythbuntu
---

### Post by zeltak on 2008-07-09
Hi all

i have been making some changes to my lirc config files (located at /Home/User/.lirc) and i cant get the system to apply the changes until i restart the computer. its quite annoying since i make alot of changes and want to see each one and how it effects the system, can anyone tell me if there is a CLI command to refresh/re-read the lirc file without restarting?

thx

Zeltak

---

### Post by jablack on 2008-07-09
Type "sudo /etc/init.d/lirc restart". Should restart Lirc and reread your configs.

---

### Post by zeltak on 2008-07-09
thx for the answer

unfortunately  i can say for 100% it does not work. ive changed the .lirc file, restarted lirc with the sudo /etc/init.d/lirc restart, it seems to restart but it dosent work...after i restart the computer...Works like a charm...very strange...does anyone know another way?

thx

Zeltak

---

### Post by freymann on 2008-07-09
> **zeltak said:**
> thx for the answer

unfortunately  i can say for 100% it does not work. ive changed the .lirc file, restarted lirc with the sudo /etc/init.d/lirc restart, it seems to restart but it dosent work...after i restart the computer...Works like a charm...very strange...does anyone know another way?


 You can restart lirc the way indicated, but if you've got MythFrontEnd running when you do that, you still have to exit frontend and then go back into it, so it can renew its handles on lirc.

 That's still better than having to reboot the entire box.

---

### Post by maxim99 on 2008-07-09
I found that a restart might not be needed when changing config files. I was change what the buttons do for mplayer, and I simply restarted mplayer.

The config files I was changing were located in:

/home/user/.lirc

---

