---
title: "Sound problem during 3D games"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by tux2000 on 2007-03-26
Hi,

hope someone can help me :)

I'm a new Ubuntu 6.10 user and very happy with Ubuntu. Looks great, works great... I'm very happy with it...

But I have one little problem with my sound. All sounds work fine, but when I start a 3D application (a game like Neverball) my sound sounds ugly (like overmodulated).

**Alsamixer said: **

C-Media PCI CMI8738 - Chip CMedia PCI

**asoundconf list said:**

Names of available sound cards:
CMI8738 

**cat /proc/interrupts said:**

0: 50354 XT-PIC timer
1: 63 XT-PIC i8042
2: 0 XT-PIC cascade
5: 1155 XT-PIC CMI8738
7: 0 XT-PIC parport0
8: 3 XT-PIC rtc
9: 1 XT-PIC acpi
10: 242 XT-PIC eth0
11: 12756 XT-PIC radeon@pci:0000:01:00.0
12: 4131 XT-PIC i8042
14: 6630 XT-PIC ide0
15: 3119 XT-PIC ide1 

I try a lot of stuff I found here and on other websites (like the PCM hint). But I don't works and the sound is still okay, except the sound with 3D games.

I have a 900MHz fast and old PC. Vector Linux's Live-CD works fine with sound and Neberball, so my hardware seems to be okay.

---

