---
title: "Every time I restart, my sound stops working."
date: 2008-07-29
forum: Multimedia Software
---

### Post by erans on 2008-07-29
I can fix the problem by reinstalling the ALSA drivers from a fresh kernel, but this is extremely annoying. If I log off/log in, my sound will stay in tact. If I do I full hardware reboot, I have to reinstall the ALSA drivers. 

Any ideas?

---

### Post by gjoellee on 2008-07-29
Install alsa > sudo apt-get install alsa and then go to System->Preferences->Sessions->Session Options and click on Remember Currently Running Applications, reboot and see if it good now...

---

### Post by redbeardmcg on 2008-07-29
Take a look at my post snd_ice1724 needs to be re-inserted to work. This may be a similar issue. Try using the steps I posted and see if this resolves the issue without re-installing alsa. You will of course want to use the proper alsa snd module for your card. What type of card do you have (lspci)?

---

