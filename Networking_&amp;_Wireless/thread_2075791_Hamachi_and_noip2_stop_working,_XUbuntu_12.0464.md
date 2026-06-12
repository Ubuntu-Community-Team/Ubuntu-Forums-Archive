---
title: "Hamachi and noip2 stop working, XUbuntu 12.04/64"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by mbogevik on 2012-10-24
This afternoon both Hamachi and noip2 stopped working on my server (XUbuntu 12.04/64, desktop)

Everything possible have been checked, programs reinstalled and debugged with no result. Since noip2 fails on creating new config file (sude noip2 -C) and Hamachi fails logging in (new clean install, "sudo hamachi login" reports "Logging in .. failed") it seems both programs do not manage to interface with eth0 network card.

And here the problem may be, last year a thunderstorm broke the 1G network connection on main board.  I bought a 1G PCI card and installed it, and since "eth0" is often used in programs (like conky) I edited /etc/udev/rules.d/70-persistent-net.rules setting the PCI card to "eth0"

After new install of XUbuntu this summer I now only see working PCI card in /etc/udev/rules.d/70-persistent-net.rules:

# PCI device 0x1186:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="84:c9:b2:48:ef:75", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


ifconfig :
eth0      Link encap:Ethernet  HWaddr 84:c9:b2:48:ef:75  
          inet addr:192.168.1.45  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::86c9:b2ff:fe48:ef75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:577706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:465193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:642196836 (642.1 MB)  TX bytes:185037555 (185.0 MB)
          Interrupt:20

Is there something I have missed that allows these programs to access the "eth0" card ?  And can it happen just like that ?

I have reset computer, router and network to make sure there is no issues.  Everything else on computer and network is OK (file share, teamspeak ++)

Any suggestions appreciated :)

---

### Post by mbogevik on 2012-10-24
Oh what a wonderful day !  Most likely this is about my ISP that is blocking most of my DSL ports claiming I have "unwanted traffic" on my line.  Seems my kid's have got a virus/trojan again.

Sorry if this is the problem !

---

### Post by mbogevik on 2012-10-26
Yes, it is now confirmed that the reason for noip2 and hamachi stop working was my ISP blocking most if my outgoing ports.

One of my children had a Trojan in computer, no need to say, Windows XP, and even with updated NOD32...  As long as IE is allowed to write to users temp folder and to put in "run key's" in registry that runs on next re-boot, before virus scanner starts, this is not possible to avoid !

Sorry if I wasting anyone valuable time

---

