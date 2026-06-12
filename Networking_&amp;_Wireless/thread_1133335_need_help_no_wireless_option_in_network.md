---
title: "need help no wireless option in network"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by rednkfool on 2009-04-22
I am new to this OS  but i was told it was a good OS  I purchased a dell 530n and i have no wireless option in the network manager screen.  i bought a usb WUSB54GC  to use to connect to my Linksys wireless router WRT54g        some one told me i have to download a file called ndiswrapper     how do i do that    i thought i was good at computers until this new system   please help   i am running ubuntu 8.04 lts dvd

thanks

bbmfic@dell-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IR (ICH9R) LPC Interface Controller [8086:2916] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller [8086:2920] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller [8086:2926] (rev 02)
bbmfic@dell-desktop:~$

---

### Post by abyssius on 2009-04-22
Hi rednkfool

I happen to have the same linksys usb adapter and router. Here's the deal. If you were using ver. 8.10 or 9.04, you wouldn't have to do a thing as your USB adapter is supported "out-of-the-box". When I was using 8.04 I had to use ndiswrapper. I highly recommend you use either 8.10 or 9.04. You could download the live CD, burn it, and try it out. If you get connected with the live CD, then you're done. If you don't want to do this then you'll have to install the ndiswrapper utility, locate the Windows drivers and set up your adapter that way. This is more involved, but not impossible if you know how to get the .inf and the .sys files which comprise your windows driver. With these in hand, I can help you to get connected.

Try this command, since lspci -nn didn't specifically show your adapter:
```
lsusb
```

The command should return something like this:
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13b1:000a Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Note that it identified my Linksys adapter as Device 003: etc.

Pleas post the output.

---

### Post by rednkfool on 2009-04-23
Thank you for your help     so i can dowmload the new 9.04  and it should work.     9.04 is better than 8.04  correct.    Once again i am new to this and trying something new.   
 
I will try doing it tonight when i get back home

---

### Post by Tobi-fp on 2009-04-23
We are glad to have you on the team ;)
Anyways, 9.04 is newer than 8.04, the name "8.04" the 8 is because it was released in 2008 and 04 is because it was released in april, 9.04 is the newest one, they released it today :) and there has not been found many bugs. I believe it is better for you to download the 9.04, because it would probably solve your issues.. 
Anyways, you can also update without a cd, just do -> System -> Administration -> update**** (cant remember what its called in English, mine is in danish), and at the top of the screen it will say "upgrade"

---

### Post by rednkfool on 2009-04-23
-> System -> Administration -> update

I did as stated above and ask me for a disk i put in the one i received with the puter and it dont do anything it gives me an error message


I burned a cd of 9.04    how do i instal it   please help

---

### Post by rednkfool on 2009-04-24
I figured it out i needed to change a few things and update to 8.10 first before i can go to 9.04    thank you everyone

---

### Post by rednkfool on 2009-04-28
Thank you all  problemed solved once upgrated to 9.04 and also picked up the silver usb and returned the black one.   silver worked out of box

problem solved

---

