---
title: "Acer Aspire 5020 BCM4318"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by *g!t5^_)*(H on 2009-04-23
Hi,

Jaunty 9.04 is great, but Acer Aspire 5020 computers still need some help for wireless. But this time is very easy:

1 - Install Jaunty Jackalope
2 - Restart computer
(If you go to System>Administration>Hardware drivers,
Broadcom card may not be listed)
3 - Stop computer (restart is not valid)
4 - Connect by LAN cable (internet connection is needed)
5 - Go to: System>Administration>Hardware drivers
6 - "Broadcom B43 wireless driver" should be listed, activate it 
(if is not listed, :s, try stopping and starting computer again, or wait ... I don't know)
7 - Open a terminal (Applications>Accessories>Terminal)
8 - Type: sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
9 - Stop computer again

Wireless should be working when  (and for first time, even the front button works)

:D:D:D:D:D:D

---

### Post by Andreasen1970 on 2009-04-23
I have just installed Ubuntu 9.04 on my Acer Aspire 5020.  
 Everything works the first time besides  my Wlan.  
 But it was very easy to get it to work.  

 I just clicked "System> Administration> Hardware drivers"  
 "Broadcom B43 wireless driver" was in the list and only needed to be activated.  

 Now everything works.

Nice:P

Kim Andreasen

---

### Post by nush on 2009-04-24
hi optimisme
big big thanks for that 
worked just as you said
nush:)

---

### Post by ballboy on 2010-01-20
Wireless used to be a pain to install and required all sorts of steps to install - v 9.04 was much better but now with Karmic 9.10 all you need to do after installing Ubuntu is update the software (system->administration->update software) then the driver is available. Select the driver and reboot again and -tadaaa- working wireless - even the light on the front of the laptop works which uses to require the self creation of scripts to get working... Ubuntu is finally getting there, just need to get the high-end graphics working and we can dump Windoze forever...

---

### Post by Zuseppe on 2010-01-20
BTW did you try to connect to an ad-hoc network with Ubuntu 9.04/9.10 and your 5020 laptop? 
I activated BCM4318 adapter on my Aspire 5024 using the same procedure described by Andreasen1970, but ad-hoc networking doesn't work.
If you want, take a look at my [thread]("http://ubuntuforums.org/showthread.php?t=1383022&highlight=BCM4318").
Bye

---

