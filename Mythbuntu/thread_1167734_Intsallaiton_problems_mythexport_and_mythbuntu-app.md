---
title: "Intsallaiton problems mythexport and mythbuntu-apple-trailers"
date: 2009-05-23
forum: Mythbuntu
---

### Post by malaTG on 2009-05-23
Hi everyone,

Recently upgraded to Jaunty and I have a number of problems with my myth installation.

1. When I try to upgrade mythexport it asks me for a password but I don't know which password it means?

2. When it tries to set the settings for   "mythbuntu-apple-trailers" I get the message

> No entry for terminal type "unknown";
using dumb terminal settings.

and it stays there until I kill it.

3. I have found some different information on how to enable VDPAU for mplayer. Is there some really good guide? I have tried with the command

> mplayer -vo vdpau -vc ffh264vdpau 

but I only get sound.

Thx in advance!

/mala

---

### Post by Triptol on 2009-05-23
1. Probably your root MYSQL account (the default one is empty, so unless you have changed it just hit enter). It could also be your mythconverg password. You can find that one in: /etc/mythtv/mysql.txt. And when nothing works, it will be your own password (the one you use for your mythtv user).

2. Can't tell what is wrong, but your terminal is somehow broken. You might want to try another terminal (try pressing ctrl+alt+f1 to switch to a terminal only screen. ctrl+alt+f7 will get you back)

3. Can't tell for mplayer, but the vdpau support in Mythtv will only arrive in 0.22. If you have a look at the daily/weekly sticky thread you will find that someone posted packages for 0.21 with vdpau support.

---

### Post by rhpot1991 on 2009-05-25
> **Triptol said:**
> 1. Probably your root MYSQL account (the default one is empty, so unless you have changed it just hit enter). It could also be your mythconverg password. You can find that one in: /etc/mythtv/mysql.txt. And when nothing works, it will be your own password (the one you use for your mythtv user).

Root MySQL password is correct, though I thought this bug was fixed, what version of MythExport?

---

