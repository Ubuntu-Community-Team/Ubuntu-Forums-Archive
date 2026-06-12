---
title: "NGS Robbie 2.0 USB 2.0 Internet Cam"
date: 2005-12-12
forum: Multimedia &amp; Video
---

### Post by littlegreenman on 2005-12-12
Hi everyone.

I need your help to get my webcam working in L inux. I bought this webcam, which works in XP if I install the drivers included in the CD, but I don't know how to get it working in Ubuntu (Breezy Badger).

First of all, I am not a newbie, but not far off that... Let's say that I am like the first animals that left the ocean to populate the earth... I know already how to crawl... but that is preety much all.

1st step: 
Went to Device Manager and saw
USB 2.0 Device Manager > Silicon Integrated ... > USB 2.0 PC Camera

So it knows there is a USB camera attached.

2nd step:
go to [http://www.linux.com/howtos/Webcam-HOWTO/hardware.shtml](http://www.linux.com/howtos/Webcam-HOWTO/hardware.shtml) and cannot figure it out....
I run lsmod and don't see the things they say I should be seeing...

I search Mr. Google with the name of the camera and Ubuntu and I get a spanish post of somebody asking for help, but nobody really helping...

So I thought to turn to you, the creme de la creme of the Ubuntu world... I think flatery goes a long way :D

Please help... I would love to use my webcam in ubuntu... cause I hate having to switch to XP for that....

Thanks all for your help...

Diogo


Add - on: run xawtv and I get:

diogo@PC-DO-DIOGO:~$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.12-10-k7)
can't open /dev/video0: No such device
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Dispositivo inexistente
v4l2: open /dev/video0: Dispositivo inexistente
v4l: open /dev/video0: Dispositivo inexistente
no video grabber device available

"Dispositivo inexistente" in english is something like No such device

---

### Post by littlegreenman on 2005-12-13
Hi,

I've sent an email to the company and they've told me the chipset used by the webcam is SQ930C.

Also there is a document here [http://www.sq.com.tw/product/IC/resources/sq930c/SQ930C_ASICBrief_V1.3_2005Apr22.pdf](http://www.sq.com.tw/product/IC/resources/sq930c/SQ930C_ASICBrief_V1.3_2005Apr22.pdf)  with the details about this chipset.

Can anyone help me? Please?

---

### Post by jobezone on 2005-12-13
You and me couldn't find any driver for that chipset, but since there are specifications for it, you try asking (or even paying) for someone to develop a driver for it.

Or, you could return the webcam, and buy one wich is well supported.

Boa sorte ;)

---

