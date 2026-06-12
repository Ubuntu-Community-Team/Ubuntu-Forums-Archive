---
title: "Nic recognized by liveCD, not by installation"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by ineedausername on 2006-07-08
When I startup using the live CD, my ethernet card (3com 3c589 PCMCIA) is recognized, configured and works without a hitch.  That is how I am connected now.

However, my hard drive installation does not properly configure the card.  I have reinstalled several times.  I boot from CD, look for a solution, boot to HD, failure, ... for about 4 hours now without success.

What am I doing wrong?  I am new to linux and to ubuntu.

Thanks,

Joel

---

### Post by stubadub on 2006-07-08
I think I am having the exact same problem.  Everything worked with 5.10, but when I upgraded to 6.06 I can't connect to the internet once I install. I've tried ubuntu, kubuntu, the lamp server install and the problem is the same every time.

---

### Post by icedcapp on 2006-07-08
sudo gedit /etc/modules
ADD "dmfe"

sudo gedit /etc/modprobe.d/blacklist
ADD "blacklist tulip"

REBOOT

---

### Post by ineedausername on 2006-07-08
I have attached 2 files[INDENT]cd-mods.txt -- lsmod from the liveCD install 
hd-mods.txt -- lsmod from the hard drive install [/INDENT]

Examining them, I noticed that the functional install on the liveCD uses 3c589_cs module, but it was not available on the HD, so I copied it to the HD.

I modified /etc/modules and added 3c589_cs

rebooted, here is the output from ifconfig -a
[INDENT]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)
[/INDENT]
here is the output from lspci
[INDENT]0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:02.0 CardBus bridge: Toshiba America Info Systems ToPIC97 (rev 05)
0000:00:02.1 CardBus bridge: Toshiba America Info Systems ToPIC97 (rev 05)
0000:00:04.0 VGA compatible controller: Chips and Technologies F65555 HiQVPro (rev c6)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0a.0 Communication controller: Toshiba America Info Systems FIR Port (rev 23)
[/INDENT]
I hope this makes sense to someone.  I have to go to bed, I have been trying to resolve this for 10 hours straight now.  ](*,) 

Thanks,

Joel

---

### Post by stubadub on 2006-07-08
It doesn't sound like that fixed his problem, but my lamp server is actually able to reach the outside world (and pretty soon vice versa).  Thanks for the assistance!  That's exactly what I needed.  Any chance you could briefly explain what exactly those changes did to make my network card recognized?

---

