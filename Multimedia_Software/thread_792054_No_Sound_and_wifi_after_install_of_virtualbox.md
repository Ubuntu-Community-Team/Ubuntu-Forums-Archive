---
title: "No Sound and wifi after install of virtualbox"
date: 2008-05-12
forum: Multimedia Software
---

### Post by JustinAlf on 2008-05-12
I have never had this happen before, but I'm stuck.  I installed Virtualbox and all of the kernals that I could install for it.  After a reboot, I lost my sound and wifi abilities.  I have since uninstalled Virtualbox and have gotten rid of the Virtualbox virtual kernals associated with it.  Still, no wifi and no Sound.  For the sound, it tells me that I am missing the gstreamer plugin.  Whats going on!?

---

### Post by ulli.winter on 2008-05-16
same problem here....
:(

---

### Post by Sirchristopher on 2008-05-19
Me too

---

### Post by ulli.winter on 2008-05-20
i've posted my problem to the virtualbox page:
[http://forums.virtualbox.org/viewtopic.php?p=23611#23611](http://forums.virtualbox.org/viewtopic.php?p=23611#23611)

if you want to participate somehow....

---

### Post by thecowking on 2008-05-20
I had an identical problem last night, when I did a modprobe for my wifi module, it came up blank. So I checked grub during boot and found that Virtualbox had somehow (probably my fault) set a -386 kernel as default. I booted up, did a gksudo gedit /boot/grub/menu.lst and commented out the offending kernel. Fixed the problem,I got my wifi and my sound back after another reboot.

---

### Post by ulli.winter on 2008-05-20
thanks cowking!
worked!

actually i removed the generic kernel in paket manager and did a sudo update grub

---

### Post by Sirchristopher on 2008-05-20
Thanks, fixed me right up!

---

### Post by thecowking on 2008-05-21
Ah good to hear :)

---

