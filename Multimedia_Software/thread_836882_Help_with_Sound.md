---
title: "Help with Sound"
date: 2008-06-21
forum: Multimedia Software
---

### Post by liekWTFmang on 2008-06-21
Hello everyone. I need some help with my speaker. As I just switched from Windows to Ubuntu, my speaker doesn't work regularly, as if when I just turn it on. Can anyone please help me out?

---

### Post by mastermindg on 2008-06-22
Welcome to Ubuntu!

Much more than Windows, Linux users require a much broader understanding of the environment in which they dwell.

In order to effectively diagnose your problem, we require more information. For instance:

Your Computer model, configuration, i.e. Dell Inspiron ... 

copy the output from these commands into your reply:

lspci
asoundconf
uname -r

This will give us a base with which to start diagnosing.

---

### Post by liekWTFmang on 2008-06-22
lspci

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
02:0d.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
02:0f.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)

asoundconf

Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card CARD
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio

uname - r

2.6.20-15-generic

Thats about it.

---

