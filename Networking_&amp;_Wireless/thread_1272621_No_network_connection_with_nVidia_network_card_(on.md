---
title: "No network connection with nVidia network card (onboard)"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by michael_madsen on 2009-09-22
Hi,
 
I'm new to Linux/Ubuntu, but have lots of experience from Windows platform. I am trying to get Ubuntu to run on a HTPC, I have built. The system is built on an ASUS P5N7A-VM ([http://www.asus.com/product.aspx?P_ID=8YiUFvK51IergAqY&templete=2](http://www.asus.com/product.aspx?P_ID=8YiUFvK51IergAqY&templete=2)) motherboard, so most devices are onboard.
 
I have installed Ubuntu 9.04 Desktop edition. Everything seems to work fine, except that I don't seem to be connected to the internet/network. The network connection is a wired one. The NetworkManager icon in the top, right corner (next to the date) says "No network connection".
 
I have read around in forums for a while to try to see if I could find anything, without any luck though.
 
 
I have done the following commands:
 
lspci |grep Eth
[COLOR=blue]00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)[/COLOR]
 
lshw -C network
[COLOR=blue]WARNING: you should run this program as super-user.[/COLOR]
[COLOR=blue]*-network [/COLOR]
[COLOR=blue]description: Ethernet interface[/COLOR]
[COLOR=blue]product: MCP79 Ethernet[/COLOR]
[COLOR=blue]vendor: nVidia Corporation[/COLOR]
[COLOR=blue]physical id: a[/COLOR]
[COLOR=blue]bus info: pci@0000:00:0a.0[/COLOR]
[COLOR=blue]logical name: eth0[/COLOR]
[COLOR=blue]version: b1[/COLOR]
[COLOR=blue]serial: 00:26:18:35:b9:b9[/COLOR]
[COLOR=blue]width: 32 bits[/COLOR]
[COLOR=blue]clock: 66MHz[/COLOR]
[COLOR=blue]capabilities: bus_master cap_list ethernet physical[/COLOR]
[COLOR=blue]configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes[/COLOR]
[COLOR=blue]*-network DISABLED[/COLOR]
[COLOR=blue]description: Ethernet interface[/COLOR]
[COLOR=blue]physical id: 2[/COLOR]
[COLOR=blue]logical name: pan0[/COLOR]
[COLOR=blue]serial: 12:35:bb:ed:e5:37[/COLOR]
[COLOR=blue]capabilities: ethernet physical[/COLOR]
[COLOR=blue]configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/COLOR]
 
I hope this will guide any of you Linux gurus into knowing what this could be about.

---

### Post by scragar on 2009-09-22
Could you please run:
```
ifconfig
```And see if eth0 is listed, if not:```
sudo ifconfig eth0 up
```Will bring it up, then try connecting with it```
sudo dhcpcd eth0
```

---

### Post by michael_madsen on 2009-09-22
ifconfig
[COLOR=blue]eth0 Link encap:Ethernet HWaddr 00:26:18:35:b9:b9 [/COLOR]
[COLOR=blue]UP BROADCAST MULTICAST MTU:1500 Metric:1[/COLOR]
[COLOR=blue]RX packets:123 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=blue]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=blue]collisions:0 txqueuelen:1000 [/COLOR]
[COLOR=blue]RX bytes:10853 (10.8 KB) TX bytes:0 (0.0 B)[/COLOR]
[COLOR=blue]Interrupt:20 Base address:0xa000 [/COLOR]
[COLOR=blue]lo Link encap:Local Loopback [/COLOR]
[COLOR=blue]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR]
[COLOR=blue]inet6 addr: ::1/128 Scope:Host[/COLOR]
[COLOR=blue]UP LOOPBACK RUNNING MTU:16436 Metric:1[/COLOR]
[COLOR=blue]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=blue]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=blue]collisions:0 txqueuelen:0 [/COLOR]
[COLOR=blue]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/COLOR]
 
since eth0 was listed, I went straight to
 
sudo dhcpcd eth0
[COLOR=blue][sudo] password for michael:[/COLOR] (here i typed password)
[COLOR=blue]sudo: dhcpcd: command not found[/COLOR]

---

### Post by mzulkoski on 2009-09-22
Sorry I can't help.   also have nVidia onboard lan. However, mine was working but suddenly stopped. I verified my router and cable by connecting the lan cable to another computer; no problem connecting with the other computer.

That narrowed it down to the onboard lan or (uuughhhh) maybe a motherboard problem.

I ran the same commands you did and got pretty much same results.

I disabled the onboard lan and installed a network card that I know is good.  The card won't connect either.

The computer has only been in use for three months (third computer on my lan).  I thought a recent update may have broken the onboard lan so I did a fresh install using the same cd I used for the original install (9.04 amd64).  During the new install I formatted all of my partitions to make sure all old settings were erased.  The onboard lan and add-on card still do not work.  The reinstall was probably a waste of time; both of my other computers are running 9.04 with the same updates and they still work.

So, here we are, stuck at:  dhcpcd: command not found.

Mike

---

