---
title: "Wubi (Monitor Out Of Range)"
date: 2008-12-23
forum: Multimedia Software
---

### Post by EncryptedFile on 2008-12-23
I have been lurking these forums for the past 2 weeks looking for an answer to my problem, and all I've found is unanswered posts that have done nothing, but made those users who wanted to try out, and possibly switch to Ubuntu do the exact opposite.
Hopefully this is not one of those posts.

I'm trying out Kubuntu through the Wubi installer, but after the first reboot my 19" wide screen Hanns-G (HW191D) goes out of range.
In winblowze xpee it runs smoothly at 1440x900@75Hz.
I even tried plugging in an old 4:3 1024x768 dell LCD to see if that would work, and it still said out of range...
Someone please help me get it running correctly so I can use Kubuntu on my main desktop as I already have Kubuntu set up on my laptop*, and custom built secondary desktop** without any problems (other then the monitor going out of spec for a few minutes the first time I tried installing it), and I'd really like to see how it performs on my recently built main PC***.

*
Gateway MT6452
AMD Turion 64 X2 Mobile TL-52
1596.1 MHz/1600 MHz
DDR2, PC2-5300 (333 MHz), 2048 MBytes, Nanya Technology

**
AMD Athlon 64 X2 Dual Core Processor 4800+ 1MB L2 Cache (per core 2MB total) Socket 939 Processor (2437.14 MHz)
ASRock 939Dual-SATA2 Socket 939 ULi M1695 ATX AMD Motherboard
Corsair PC-3200 DDR400 ram 2048 MB/2 Gigs
ATI Radeon x1800XT 512mb GDDR3 core:625mhz mem:1500mhz


***
AMD Phenom x4 9850 BLACK EDITION 2.5GHz 4 x 512KB L2 Cache 2MB L3 Cache Socket AM2+ 125W Quad-Core Processor
ASUS M3A79-T Deluxe AM2+/AM2 AMD 790FX ATX AMD Motherboard
CORSAIR DOMINATOR 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory
ATI Radeon x1800XT 512mb GDDR3 core:625mhz mem:1500mhz (going to upgrade someday, and crossfire the secondary PC)

---

### Post by overdrank on 2008-12-23
Ok after reviewing your other thread, what system are you having issues with?
I assume it has a ATI graphics card, have you tried using recovery mode and use the xfix option to correct the graphics?
If this fails and you have another system using the same ATI graphics card then you may check that xorg to see how it varies from the system having issues.

Side note if you are creating this new thread then do not bump your previous one. ;)

---

### Post by EncryptedFile on 2008-12-23
ok this is the xorg.conf file from my secondary desktop that is working just fine with an ATI card in it.

---

### Post by EncryptedFile on 2008-12-23
This issue was resolved by myself.
I simply replaced my xorg.conf with the .conf file from my other desktop, and now "everything just works".

For anyone else with my problem simply copy the second xorg.conf.txt (remember to remove the .txt) file in you C:\ drive
boot into *ubuntu
press ctrl+alt+F1
login
type: cp /host/xorg.conf /etc/X11/
type: sudo reboot, or shutdown -r -t 0 now
???
profit.

---

