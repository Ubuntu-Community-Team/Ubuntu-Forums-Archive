---
title: "Can't connect to Internet with static address"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by gfansher on 2010-06-24
i'm having this same exact problem. i use a static ip....i can connect to my network, see other pc's, etc....but cannot connect to internet. for some reason, when i enter my gateway address, it goes to 0.0.0.0 as soon as i hit ok....not sure but, i'm guessing my problem revolves around this.
 
any/all help greatly appreciated.....geoff

---

### Post by gfansher on 2010-06-24
also....i've seen messages saying i need to add some command lines into the etc/network---> folder but, it will not allow me to change any of those settings or save the log with any changes....says i'm not the owner.

---

### Post by Iowan on 2010-06-24
Moved to a new thread from [here]("http://ubuntuforums.org/showthread.php?t=1485733"). Is Samba also involved (somehow)?
Use **sudo nano** or **gksudo gedit** to get permission to save edits. Where did you set up the static address - Network Manager, or are you trying to edit */etc/network/interfaces*?

---

