---
title: "EVDO speed problem in Ubuntu 9.04"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by ntomer on 2009-07-02
Hi,

I am a recent convert to Ubuntu. After struggling with M$'s pathetic Windows Vista for long, I decided to switch allegiance to Ubuntu and I must say I am not disappointed.

I installed Ubuntu 9.04 on my laptop and it out-performs Vista by a mile. But I've run in a problem. I am based in India, and use BSNL (India's national carrier) EvDO for internet connection. It uses ZTE AC8700 USB Modem for connecting.

I this device EVDO on my laptop using userserial drivers and wvdial. I put the stupid mode as 1, and baud rate as 921600. 

It works alright, but the speed is capped at 62.5 KBps; it'll go up to 62.5 KBps but never beyond that. Whereas at the same laptop, at the same place, when I connect from Win XP, the speed easily goes upto 100-110 KBps.

Is this due to the usbserial drivers, which reportedly have max buffering capacity of 60 KBps (At many places I've read that the usbserial drivers in Ubuntu 9.04 don't have this problem)? And if yes, how do I change it to Airprime drivers?

Please help.

Regards

Nitin

---

### Post by KewlEugene on 2009-07-06
I think I will be facing the same problem soon, when I receive a Sprint Novatel EX270 Expresscard in the mail this week, and try it on a Dell 15n with Ubuntu 8.10. The Sprint PDG guide for Linux says the max thruput is limited to 599kbps by the USB drivers. I live in Oregon and California.

---

### Post by harry2006 on 2009-08-06
updating the kernel dint help either? i'm using the evdo modem with the latest kernel and its working fine, no issues with speed.

---

### Post by nagub on 2009-08-17
I am also facing the same issue with Janunty ( Ubuntu 9.04) on Dell  ... speed is damn slow 10~15 KBPS in Ubuntu  .. but  140~150 KBPS using the XP

---

### Post by harsh.C on 2011-05-22
This problem persists in Ubuntu 10.04 too. I have tried using EVDO in windows 7 where the speed is well above 100-110 where as that in ubuntu is much much lower.

Please Help

---

### Post by harsh.C on 2011-05-22
just found the solution to the problem ... first install firefox on your system and then in the URL box type about:config pass through the warnings and in the filter box type ipv6 now there will be a single option that will appear double click it and the boolean value will chnage to true.. now restart firefox and probably u'll have a better net speed.

What is happening here is firefox is looking for the ipv6 addresses and by doing the above steps we prohibit it by disabling ipv6

---

