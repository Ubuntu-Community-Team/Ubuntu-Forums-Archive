---
title: "Internet Connection not Working in Windows XP after boot"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by Mlemos on 2009-11-22
Dear all.

I have installed Karmic from Wubi making a dual boot  with Windows XP.

I had an excellent outcome in configuring all network aspects. However when booting back to Windows XP I receive a notification that the Network Cable is not Connected and I also noticed that in the D-Link wireless router the light indicating LAN port 1 is turned-off.

Exploring it I have boot back to Ubuntu Karmic and: The LAN port 1 turned on and the connectivity is perfect.

I have checked all cables, they are working and connected properly, but in Windows it keeps not recognizing it and in my Network Card all lights are turned off.

Did someone experienced something similar?

Thanks in advance.

---

### Post by Iowan on 2009-11-22
A few versions ago, a similar problem was mentioned - the other way around. Ubuntu wouldn't work when windows was started first. I saw an article somewhere that suggested computer software is now faster than the hardware, and can get systems reset faster than the hardware drivers can reset. 
 Have you tried a full power-down and back up?

---

### Post by Mlemos on 2009-12-05
Yes I did try it. However it keeps not connecting at Windows, only in Ubuntu environment. It seems for Windows the network adapter (hardware) doesn't exist.

Any other thoughts on it?

Thanks for your attention.

---

### Post by abr on 2009-12-05
yes similar problem is faced by my system (e-machine laptop - winxp, ubuntu-9.10 and puppy linux - Huawei ETS 2288 - Wireless Telephone(BSNL) modem connected via USB port)

when I find the extreme delay in connection I always 

1. remove USB and reinsert (after say 10-20 seconds) before trying again.

if the above steps fails

2.  switch off telephone (cut power to telephone) and switch on after say 10 or 20 seconds. 

the above steps generally solves problem in my case - it may be of help - you can also try)

Another point I noticed - I installed USB port monitor in windows and noticed only the following commands move from computer to modem (winxp)

1.  AT    (Note : not ATZ or ATX0 or ATQ0)

2.  ATEOV1  (no other commands from winxp) 

the success rate (of getting an internet connection within a few seconds) is very high under winxp.

I tried (in both ubuntu and puppy) to connect to internet by changing the modem init strings similar to winxp.

but under ubuntu and puppy linux the success rate is low (It means the dialer keeps on trying - and gets/shows "OK" only - no carrier deduction)
randomly -  I would rather like to say - luckily - carrier is deducted after several trials)

I am neither a computer engineer nor a software professional 

but my observation may be of help to others

so I submit:P

bye

---

### Post by abr on 2009-12-25
Further to my above post- I have accidentally found way to get quickly (without so may trials) internet connection with HUawei WLL BSNL T1 ETS2288 modem.

(Note: I have already completed creating/changing rules, wvdial files as suggested in different threads of different linux forums)

1.  Start gnome-ppp

2. just before clicking the connect button - lift the telephone (mouth - ear piece/part)

3. click the connect button - gnome-ppp

4. very fast computer gets connected to internet

5. replace/keep the mouth-ear piece/part of the BSNL Phone in its resting place

(I am not a technical user or software geek - however, I am sharing my experience so that others may find out reasons for this modem - connection behaviour)
:guitar:

---

### Post by stevevp on 2010-01-01
Hi, I have exactly the same propem as the originally poster (OP). I have just installed ubuntu 8.10 within Windows XP sp2. (Ubuntu 9.10 would not install so I plan to upgrade in due course.) The install went well and my internet connection in Ubuntu via network cable to my router seemed faster than usual. Unfortunately when I boot back to Windows XP I have no internet connectivity. I have tried turning off the router and the computer and rebooting but still have the problem. Has the OP's original problem been solved please and if so how? 

PS This is my first post as an Ubuntu newbie so please be patient! :P

---

### Post by Selmi on 2011-11-19
i never had this problem before, but now i upgraded to ubuntu 11.10 and here it is. i can't find any solution anywhere. only when i switch off computer and let it switched off for longer time it helps (sometimes after 15 minutes, sometimes 2 hours are not enough)

---

