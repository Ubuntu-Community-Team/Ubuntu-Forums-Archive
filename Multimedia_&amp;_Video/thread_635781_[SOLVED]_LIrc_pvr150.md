---
title: "[SOLVED] LIrc pvr150"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by mandyfester on 2007-12-09
Hello

After an epic battle I recently successfully got my Hauppauge pvr 150 using the post below:
[http://ubuntuforums.org/showthread.php?t=587732&highlight=gutsy+lirc_pvr150]("http://ubuntuforums.org/showthread.php?t=587732&highlight=gutsy+lirc_pvr150") 

The problem is that I always had 2 devices showing inthe /dev/lirc:
/dec/lirc0 and /dev/lirc1

My hauppauge was registered to lirc1 but if I set the device in the hardware.conf file located in /etc/lirc I had no problems.

Now for no reason on each boot the /dev/lirc1 has disappeared and if I try and use /dev/lirc0 lircd returns with the message

[HTML]lircd-0.8.2[5475]: lircd(userspace) ready
lircd-0.8.2[5475]: accepted new client on /dev/lircd
lircd-0.8.2[5475]: could not get file information for =/dev/lirc1
lircd-0.8.2[5475]: default_init(): No such file or directory
lircd-0.8.2[5475]: caught signal
Terminated
[/HTML]
 
I checked dmesg and it has the following text so it seems as though the hauppauge is begin detected.

[HTML][   42.091074] lirc_dev: IR Remote Control driver registered, at major 61 
[   42.137070] lirc_pvr150: chip found with RX and TX
[   42.137309] lirc_dev: lirc_register_plugin: sample_rate: 0
[   42.171812] lirc_pvr150: firmware of size 302355 loaded
[   42.172223] lirc_pvr150: 743 codesets loaded
[   42.206753] lirc_pvr150: Hauppauge PVR-150 IR blaster: firmware version 1.3.0
[/HTML]

Any help is appreciated.

Thanks

Andy

---

### Post by mandyfester on 2007-12-10
For some reason the device now shows.

Hmmm. I have a media pc with freevo installed. With Feisty everythiong worked realy well but when I upgraded to Gutsy it has been a real pain, so much in fact that during a moment of weakness I seriously considering installing Windows Media Centre.

---

