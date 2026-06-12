---
title: "PCTV HD Pro Stick (801e) &lt;Getting it to work&gt;"
date: 2008-07-11
forum: Multimedia Software
---

### Post by pdx77 on 2008-07-11
I have a pinnacle PCTV HD PRo Stick (801e) and I'm having trouble getting it to work in 8.04, has anyone been able to get this to work correctly?

---

### Post by pdx77 on 2008-07-21
anyone have any ideas?

---

### Post by xc3RnbFO8P on 2008-07-22
Read this:
[http://ubuntuforums.org/showthread.php?t=602039]("http://ubuntuforums.org/showthread.php?t=602039")

---

### Post by pudland on 2008-08-25
I recently purchased the 801e pro stick.

The newer models are not em28xx chips.  They are DibCom...

I just set up WinXP via sunXvmVirtualBox and it picked up 300+ channels on ClearQAM.  I havn't tried the viewer yet.  I'll keep you posted.

---

### Post by pudland on 2008-08-25
just tried it.

pctv viewer claimed i only had half the cpu i actually have and dropped all frames, audio was very choppy.  I'll work on it more later.

---

### Post by euphgeek on 2008-11-09
I found a site that has instructions on how to get this device to work:

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_(801e)]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_(801e)")

The end result of this is I can get my computer to recognize that the stick is there and kaffeine gives me the Digital TV option, but when I try to scan for channels, it just hangs for a long time and does nothing.

Does anyone have any suggestions?  I've tested my device using the instructions at [http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device]("http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device"), and I can get output using azap, but the output won't play.

---

### Post by xc3RnbFO8P on 2008-11-10
This card is now supported in Ubuntu 8.10 (kernel 2.6.27)
To be sure you got the supported card (**usb ID 2304:0227**).
To check this, do **lsusb** in Terminal.
[http://www.heise-online.co.uk/open/Kernel-Log-Linux-2-6-27-Released--/features/111671/8]("http://www.heise-online.co.uk/open/Kernel-Log-Linux-2-6-27-Released--/features/111671/8")
Just install **Kaffeine**.

---

### Post by euphgeek on 2008-11-10
Ringi,
Are you sure we're talking about the same hardware?  The stick I have has a usb ID of 2304:023a.

---

### Post by xc3RnbFO8P on 2008-11-10
No we are not talking about the same hardware.
usb ID **2304:0227** is supported.
Read this:
[http://devinjh.livejournal.com/140981.html]("http://devinjh.livejournal.com/140981.html")

---

### Post by euphgeek on 2008-11-10
So this card is not natively supported in 8.10.  Darn.

Do you have any idea on how I can get it to work?  My system recognizes it and kaffeine gives me the Digital TV option, but I can't scan for channels or get a signal.  The device works perfectly under Windows.

---

### Post by sandmannc40 on 2010-01-10
I have this device I have not been able to get to work yet!.  Key word is yet.  It is just like everything else practice, practice, practice.  If you don't do it you will never learn it.

---

### Post by toddr on 2010-01-11
I have it working, or at least partially. I installed Kaffeine and it worked great at tuning in over the air digital tv. I don't have cable so I havn't tried that. What I really want to do next is plug a camcorder into the add-on dongle. Anyone have success doing this?

---

### Post by toddr on 2010-01-15
After doing some research, I found that all analog decoding for this device is not supported, including the supplied dongle.:( Hopefully there will be some more work done on the drivers.

---

