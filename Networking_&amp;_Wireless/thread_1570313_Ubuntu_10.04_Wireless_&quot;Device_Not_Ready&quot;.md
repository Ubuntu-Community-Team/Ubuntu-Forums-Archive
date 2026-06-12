---
title: "Ubuntu 10.04 Wireless &quot;Device Not Ready&quot;"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by nwu on 2010-09-08
I installed a dual-boot of Ubuntu 10.04 64-bit with Windows 7 on my Dell Latitude E6510. I have an Intel Centrino Advanced-N 6250 wireless card and a 512 MB Nvidia NVS 3100M graphics card.

At first I noticed that Ubuntu booted to a blank screen; I fixed this by editing the boot options in GRUB (as I found online).

To fix this permanently though (and enable greater than 800 x 600 resolution), I needed to download some graphics drivers. However, I then noticed that my wireless wasn't working. It shows "disconnected" at first and then "device not ready" after I disable and enable wireless. Moreover, the "WiFi" light on my laptop is off while running Ubuntu.

It seems like I'm missing some drivers to use my wireless card. Any ideas? Thanks so much.

---

### Post by Humanity to others on 2010-09-08
First you connect thru wired network. If your laptop Internet ready, select system menu->administration->hardware drivers

Ubuntu will automatically search and show drivers for your laptop

---

### Post by dirghrabadia on 2010-09-08
Do you mean you have a seperate installation, or have you installed WUBI on Win 7?

---

### Post by nwu on 2010-09-08
Yes, this is a separate installation (on a new partition).

And right now I do not have an ethernet cable, but if you are sure that will work I can go buy one.

---

### Post by grahammechanical on 2010-09-08
You say the "WiFi" light on the laptop is off while running Ubuntu. Is there a hardware switch such as a function key that has to be pressed to switch the WiFi electronics on the motherboard on?  It might be reset when the laptop is switched off.

Regards.

---

### Post by bkratz on 2010-09-08
This may be of some help (interest)

[http://ubuntuforums.org/showthread.php?p=9584806](http://ubuntuforums.org/showthread.php?p=9584806)

---

### Post by nwu on 2010-09-08
Thanks both of you; I did see this thread before and tried it (I found the switch on my laptop to turn wireless on / off), but it didn't solve my problem. (I tried both turning it off and on while in Windows and then again in Ubuntu.)

Any other ideas? Would greatly appreciate it.

---

### Post by bkratz on 2010-09-08
> **nwu said:**
> Thanks both of you; I did see this thread before and tried it (I found the switch on my laptop to turn wireless on / off), but it didn't solve my problem. (I tried both turning it off and on while in Windows and then again in Ubuntu.)

Any other ideas? Would greatly appreciate it.

Dell seems to sometimes have problems reading the state of the wireless switch.  Look through this thread and pay particular attention to posts 20 and 21 or so.

[http://ubuntuforums.org/showthread.php?t=1423477&page=3](http://ubuntuforums.org/showthread.php?t=1423477&page=3)

---

### Post by nwu on 2010-09-08
Thanks bkratz; I tried the "sudo rmmod -f dell-laptop" command, but it gave me the error that dell-laptop wasn't defined. (Only "dell-wmi" was defined; rmmod-ing that didn't help either.)

And "rfkill list" seems to indicate that everything is unblocked. :/

Any other ideas? Of course, thanks a lot for your help so far.

---

### Post by nwu on 2010-09-13
Bump. Anyone know what might be going on with my wireless?
The issue is completely blocking me from using Ubuntu, so I would really appreciate any help. Thanks!

---

### Post by nwu on 2010-10-12
A note for anyone else who had a similar problem to mine:
I just upgraded to Ubuntu 10.10, and it looks like the problem is fixed. :)

---

