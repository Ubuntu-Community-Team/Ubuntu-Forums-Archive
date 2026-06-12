---
title: "Buffalo PCMCIA card setup issue"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by dabigoreo on 2009-07-11
Laptop - Dell E5400, Intel Core2 Duo @ 2GHz, 1GB RAM, 80GB HD 
Wireless Adapter - Buffalo WLI-CB-G54HP B/G PCMCIA (Broadcom) 
Ubuntu 9.04 (64bit) 

I apologize if this has already been covered in another thread. Whats weird is if I run Ubuntu from the CD, I can download and install the Broadcom restricted driver, activate it, and wireless works fine. The minute I installed a permanent copy of Ubuntu to my hard drive, I can no longer get the wireless working...period! I ran into this behavior before and ditched my first linux attempt because of this. I don't understand why it would work from the CD and not from the hard drive. Whats even weirder is when I run system test, it says it sees the broadcom wireless adapter but I can't get the hardware driver installer to recognize it. Any help would be greatly appreciated, I really want to come over from the dark side (windoze) and have always admired Ubuntu for its user friendliness. Btw, I am a noob when it comes to linux so bear with me when it comes to running commands for information. Thanks.   :confused:

---

### Post by Crafty Kisses on 2009-07-11
I know you said you had the Buffalo WLI-CB-G54HP B/G PCMCIA (Broadcom), but I'd like to see the results of these commands, and then I can help you further:
```
lspci
lsusb
ifconfig
iwconfig
lshw -C network
```

---

### Post by dabigoreo on 2009-07-11
Thanks for the guidance Codename. Believe it or not, I booted into Ubuntu, ran the hardware drivers utility and BAM - now it is prompting me to activate the Broadcom B43 driver??? After a couple failed attempts at downloading the driver it finally got it. Go figure. The only thing I can think of that was different from before is that I booted up with the adapter in place instead of waiting for the OS to load then popping in the adapter. If this is the culprit why would that matter??? Oh well, its working now but another issue started acting up lol - the OS would not let me eject a CD! Something about authorization? I will bear the pain of learning a new OS but noob permissions is too much! :lolflag:

---

