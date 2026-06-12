---
title: "Black screen after login"
date: 2013-12-02
forum: Multimedia Software
---

### Post by anbuck on 2013-12-02
[COLOR=#000000]I have an MSI GE40 latop with an Nvidia GeForce GTX760M. When running the nouveau drivers, Ubuntu doesn't recognize external monitors regardless of whether they are attached to the SVGA port or the HDMI port. When I install the proprietary Nvidia drivers (have tried various versions including 319 or 319-updates), I only see my mouse cursor on black screen after I login. All I want to be able to do is use external monitors. How can I accomplish this?[/COLOR]

[COLOR=#000000]Thanks![/COLOR]

---

### Post by papibe on 2013-12-02
Hi anbuck.

Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Also, have you tried booting using the nomodeset option? (here's [how]("http://ubuntuforums.org/showthread.php?t=1613132")).

Regards.

---

### Post by anbuck on 2013-12-02
Hey papibe, 

Here's the output:
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:10e3]
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06) 

I think it's an Nvidia Optimus device and it isn't detecting the Nvidia GPU, just the Intel.  I have looked in the BIOS and there is no way to enable or disable either of the GPUs.

Yes, I have tried it both with and without nomodeset.  I actually had to use nomodeset to get Ubuntu to install.

Thanks for your help!

---

### Post by anbuck on 2013-12-05
If anyone has any suggestions for me, I would greatly appreciate them!  If I can't get external monitors working, I'm going to have to switch to Windows. :(

---

### Post by anbuck on 2013-12-12
This problem was fixed in the latest round of package updates!

---

### Post by milo4 on 2013-12-31
Hi anbuck,

How did you install Ubuntu on the ge40? I'm about to do this thursday, but it seems the only option is using bios/legacy boot. That seems suboptimal.. (I did find this forum post: [http://forums.gentoo.org/viewtopic-p-7470000.html#7470000](http://forums.gentoo.org/viewtopic-p-7470000.html#7470000), but thats seems quite complicated)


Thanks in advance,

Milo

---

### Post by anbuck on 2014-01-03
I used legacy mode and it works great. What's so bad about legacy mode?

---

