---
title: "Firewire port with Soundblaster Audigy 2 ZS doesn't work"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by americanknight on 2007-09-24
My firewire port with my Sound Blaster Audigy 2 ZS doesn't work.  My exterior hard drive won't mount, and I get no signal when I plug in my video camera for capturing.  However the sound works just fine, and everything is functional in the Alsa mixer, so the problem is just the firewire port. Does anyone know where I can get a driver for this or what needs to be done?

Thanks

---

### Post by steefjeqv on 2007-09-24
Hi,

This might help : [http://www.linux1394.org/eth1394.php]("http://www.linux1394.org/eth1394.php")

These drivers should be installed by default on your Ubuntu system but you'll have to use terminal.

For example :
 sudo modprobe eth1394
If you want to use you're firewire as a network device.

sudo modprobe dv1394
If you want to use your DV.

Hope this helps.

Greetings,
Steven

---

