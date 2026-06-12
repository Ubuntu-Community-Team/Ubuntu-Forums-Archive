---
title: "eth0 no longer works in 9.10"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by shadwe1l on 2010-02-03
Hi. I've got a bit of a problem I can't solve.

Here's the background:

I am running Ubuntu 9.10, and have been for about a week. Did a fresh install and have had no problems until yesterday. Yesterday morning I shutdown my laptop took it to the lab, where I used the wireless with no problem, then brought it home last night and could not get the wired network (eth0) to work. I only use wired connections at home. Up until this time the wired connection has worked with no problem.  I normally use manual configuration/static IPs to connect my laptop to my ubuntu-based router, (the router box still works with no problems.)

To start at the obvious place, ifconfig doesn't even show an entry for eth0 now. 

```

~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:a1:df:26  
          inet addr:172.31.82.103  Bcast:172.31.87.255  Mask:255.255.248.0
          inet6 addr: fec0::b:290:4bff:fea1:df26/64 Scope:Site
          inet6 addr: 2002:c652:3faf:b:290:4bff:fea1:df26/64 Scope:Global
          inet6 addr: 2001:468:c80:4310:290:4bff:fea1:df26/64 Scope:Global
          inet6 addr: fe80::290:4bff:fea1:df26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3866460 (3.8 MB)  TX bytes:459206 (459.2 KB)

```

attempts to use "ifconfig eth0" result in 

```

~$ ifconfig eth0
eth0: error fetching interface information: Device not found

```

checking dmesg for completeness...

```

~$ dmesg | grep eth0
~$ 

```

but lspci still shows the ethernet adapter (RTL-8139)

```

~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
06:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
06:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
06:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

I am not sure what to do from here.  Can any one help?

Thanks

---

### Post by chili555 on 2010-02-03
May we have a peek at:```
dmesg | grep 8139
```Thanks.

---

### Post by shadwe1l on 2010-02-03
chili555:

```
~$ dmesg | grep 8139
~$
```

Looks like that returns nothing.

---

### Post by chili555 on 2010-02-03
Ouch! It neither recognizes the card:> Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)Nor does it try to load the driver *8139too*, I believe. Even if the wire was not connected or the router or switch was defective, it ought to at least see the card...but then it *does* see the card in *lspci*. Very mysterious.

Please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```Please post the dmesg.zip as an attachment to your reply. Please do not post the entire dmesg as it's quite long and makes it harder for me to grep it.

I am starting to suspect a defective card.

---

### Post by shadwe1l on 2010-02-03
> **chili555 said:**
> 
I am starting to suspect a defective card.

Yeah, that's really gonna bring me down...

Anyway, here's the zip:

---

### Post by chili555 on 2010-02-03
I wonder what this means:> [  351.780420] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[  351.780426] Copyright (c) 1999-2006 Intel Corporation.
[  392.401710] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[  392.401716] e1000e: Copyright (c) 1999-2008 Intel Corporation.And this:> [   12.868056] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.116297] usbcore: registered new interface driver ndiswrapperWow! How many networking devices do you have?? What have you done previously to get this all going?

---

### Post by shadwe1l on 2010-02-03
> **chili555 said:**
> I wonder what this means:And this:Wow! How many networking devices do you have?? What have you done previously to get this all going?

Hmmm, sorry about that, I spent about two hours in the forums trying a bunch of different fixes before I posted my message.  One post looked similar and talked about "sudo modprobe e1000" and "sudo modprobe e1000e". It looked relevant, so i tried it, but no joy.  I just rebooted and checked dmesg again, and I didn't find those entries this time. The new dmesg is enclosed as dmesg2.txt/zip. 

Another thing I attempted include adding a second profile/entry/thingy to network manager for the wired connection. that didn't work either, I subsequently deleted the original and the second one. I also modified /etc/network/interfaces, adding a section for eth0 so that it now looks like:
```
~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
```

and tried to restart the network a bunch of times:
```
~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
Ignoring unknown interface wlan0=wlan0.

```
But all this resulted in the same: no eth0.  I even checked my /var/log/apt/term.log for the last thing i installed, (easytag-aac) to see if that might have done anything. A quick read through /var/log/messages didn't show me anything obvious, but there's a fair amount there I don't really understand.  

Finally, I even checked the pins on the ethernet port to see if they had bent and might be causing a short (seen that happen once, but it only resulted in no connection.) No luck there, all pins nice and straight.

At that point, I submitted my question to the forum.

As far as interfaces go, I have the onboard ethernet port that is currently giving me issues, an onboard wlan that works fine but is using a Broadcom B43 wireless driver from System >> Administration >> Hardware Drivers.

I also have a no-name (well Aprotech really,) PC Card 10/100 card that I have tried, but doesn't come on line. If we can't get the on board card working, I may ask for help with the PC Card, but let's just tackle one thing at a time, eh?

A thought:  Is there any point trying one of the live disks to see if the port works then? I have a raft of different versions of ubuntu at the lab that I can try this afternoon...

---

### Post by shadwe1l on 2010-02-03
Sorry, edit: I checked and didn't find the first group of entries. The ndiswrapper still shows up in dmesg, due to the Broadcom wifi driver (I think.)

---

### Post by chili555 on 2010-02-03
> A thought: Is there any point trying one of the live disks to see if the port works then?Please do and, if any of them work, pull a *dmesg* as outlined above so we can compare.> I may ask for help with the PC Card, but let's just tackle one thing at a time, eh?Yes, exactly. However, if the Realtek doesn't work with any of the live CDs, then I'd slap the other card in there and run:```
lspci -nn | grep Ethernet
```That will give us the vendor and device IDs so we can see if a driver is available to drive the card.

---

### Post by shadwe1l on 2010-02-03
chili555, thanks for your help.  I'll check those things and get back to you later this afternoon, probably in 6-7 hours.

---

### Post by shadwe1l on 2010-02-03
ok, i think i found something.  I restarted my laptop and used the grub menu to load the previous kernel (2.6.31-14-generic) and after some twiddling with network-manager, I got all the network functionality restored.  eth0 shows in ifconfig, and it show up in dmesg. (and all the other stuff works too, www, ssh, etc)

```
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:36:6f:81:46  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe6f:8146/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:700793 (700.7 KB)  TX bytes:108462 (108.4 KB)
          Interrupt:20 Base address:0x5000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

$ dmesg | grep eth0
[    1.790654] eth0: RealTek RTL8139 at 0x5000, 00:16:36:6f:81:46, IRQ 20
[   14.360092] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   25.088009] eth0: no IPv6 routers present
``` 

the kernel that i was using earlier was 2.6.31-17.  I didn't realize the change because grub doesn't normally show the menu on this machine. 

So the most recent kernel seems to be the source of the issue, and I have temporarily solved this by using the previous one.  I don't know that I would consider this "solved" yet, but I am not quite sure what to do from here...

---

### Post by chili555 on 2010-02-03
Well! That is very weird! You might open up Synaptic and mark linux-image-2.6.31-17-generic for re-installation, let it do so and then re-boot into x-17 and see if a clean sweep did the job. Then post back for the benefit of the searchers.

That's *still* weird!

---

