---
title: "wireless wount install"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by ronald1989 on 2010-01-24
i am useing a D-link wireless usb adapter .
i put it in to the usb port and tryed installing useing the disk
and when i click auto run or setup.exe file all i get is errors 
i have been trying everything posable but no luck.
i dont have a sweet clue about this OS lol
my first time useing it lol
so if i can get any help at all it would be great =)
 
useing a gigabit mobo
8800 gforce vid card
2.9 ghz prosesser cor 2 duo 
650 psu 
newest [ubuntu]("http://ubuntu") OS
 
i would like to add that its not picking up any think i plug in to the usb ports
not even the onbored usb ports :S ... kinds realy pissing me off lol.

---

### Post by bkratz on 2010-01-25
> **ronald1989 said:**
> i am useing a D-link wireless usb adapter .
i put it in to the usb port and tryed installing useing the disk
and when i click auto run or setup.exe file all i get is errors 
i have been trying everything posable but no luck.
i dont have a sweet clue about this OS lol
my first time useing it lol
so if i can get any help at all it would be great =)
 
useing a gigabit mobo
8800 gforce vid card
2.9 ghz prosesser cor 2 duo 
650 psu 
newest [ubuntu]("http://ubuntu") OS
 
i would like to add that its not picking up any think i plug in to the usb ports
not even the onbored usb ports :S ... kinds realy pissing me off lol.

Which wireless dongle is it. D_Link makes quite a few. Go to the terminal (Applications>>Accessories>>Terminal) and type in:

lsusb 
(that is LSUSB in lowercase). Copy/Paste the output back here so we can decode it.

---

### Post by ronald1989 on 2010-01-25
> **bkratz said:**
> Which wireless dongle is it. D_Link makes quite a few. Go to the terminal (Applications>>Accessories>>Terminal) and type in:
 
lsusb 
(that is LSUSB in lowercase). Copy/Paste the output back here so we can decode it.
 
 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3a08 D-Link System predator Bootloader Download
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by bkratz on 2010-01-25
The ID of 07d1:3a08 (bus 001 device 3)  corresponds with theDlink WUA-2340.  Here is one thread regarding the device  [http://ubuntuforums.org/showthread.php?t=1259316&highlight=WUA-2340](http://ubuntuforums.org/showthread.php?t=1259316&highlight=WUA-2340)  pay particular attention to post #4 where external help is offered.
Additional threads can be found at
[http://ubuntuforums.org/search.php?searchid=69455306](http://ubuntuforums.org/search.php?searchid=69455306)

---

