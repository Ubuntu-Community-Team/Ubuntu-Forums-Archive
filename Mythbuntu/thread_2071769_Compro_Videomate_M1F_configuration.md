---
title: "Compro Videomate M1F configuration"
date: 2012-10-16
forum: Mythbuntu
---

### Post by rudioos on 2012-10-16
Hi
 
I'm trying to configure a Compro Videomate M1F that uses the saa7134 kernel module with a fresh installation of Mythbuntu. From what I can see from lspci and lsmod the card is pickedup and configured correctly by the kernel, so no compiling or patching is necassary. I have also manually un- and loaded the modules. I have tried configuring the card and remote via the Mythbuntu control pannel and also used the following wiki
[http://www.linuxtv.org/wiki/index.php/Compro_VideoMate_Vista_M1F](http://www.linuxtv.org/wiki/index.php/Compro_VideoMate_Vista_M1F)
 
With or without lirc / inputlirc, I have two buttons working on the remote at all times. I have removed the lirc config files, shutdown and uninstalled lirc / inputlirc and the same two buttons still work, Playbutton exits MythTV and pause and record moves up and down. So something is overiding the lirc configuration even with the Mythbuntu control pannel IR configuration set to no remote. This probably comes from the kernel module loaded, but overrides any lirc configuration or should I say attemp to configure the remote correctly.
 
Secondly, I cand get the backend side configured as Mythtv doesn't see the tv card, even with the kernel modules loaded.
 
Any help or guidance will be appreciated

---

### Post by nickrout on 2012-10-17
Have you read this page?

[http://www.linuxtv.org/wiki/index.php/Compro_VideoMate_Vista_M1F](http://www.linuxtv.org/wiki/index.php/Compro_VideoMate_Vista_M1F)

---

