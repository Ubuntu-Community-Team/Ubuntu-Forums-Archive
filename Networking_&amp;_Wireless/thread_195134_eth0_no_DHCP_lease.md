---
title: "eth0 no DHCP lease"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by nebula on 2006-06-12
Heya,

Just ran my install of breezy after half a year, never been used on my PC before but I discovered a problem, My eth0 couldn't get an IP address. I though that this was a bad install thing so I downloaded a install disk of dapper and ran that. Still no networking on my computer (the same as where I am writing from now booted in m$ XP) I thought: maybe my networking card isn't functioning so I ran lspci:

(...)
0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

So it seems that it sees my card and from what I know, realtek is very well supported but no response from dhclient eth0:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:02:44:58:21:28
Sending on   LPF/eth0/00:02:44:58:21:28
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5

So I don't know what to do next?
Who can help me fix this problem?

Thanks in advance, 
Nebula

---

### Post by kb3hkg on 2006-06-14
run ifconfig and post its results please, it would be a big help.

---

### Post by nebula on 2006-06-15
Here yu are:

eth0    Link encap:Ethernet  HWaddr 00:02:44:58:21:28  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2375 (2.3 KiB)  TX bytes:2375 (2.3 KiB)

Rather low on activity no? ;-)

---

### Post by a12ctic on 2006-06-15
im having the same problem with the same card

---

### Post by ToXedVirus on 2006-06-16
Hey guys, i got the same problem. I have a nforce4 board with a build in adapter and exectly the same realtek card. The internet cable is connected to the realtek card. Under windows it works just perfect, but drapper drake isnt able to find the needed information(ip,mask and co) via DHCP.

---

### Post by tymanthius on 2006-06-17
This is going to sound odd, but I had the same exact problem w/ a dual boot machine on the sound card.  Worked in windows, not in linux.  Do you reboot from windows to linux, or do you do a full shutdown (all power off), then restart into linux?

The old ASUS board would 'hold' the windows assigned irq & other settings, so when I went back to linux, it wouldn't work.  

Probably not the solution, but you never know.

---

### Post by nebula on 2006-06-20
Nope, unfortunately this is not the case (not with me anyway) but thanks for the tip!

---

### Post by TimJ on 2006-06-20
This may not work but this fix seems to help a lot of people with a similar problem. It doesn't seem to be restricted to the network card used in the title of the thread.

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by ToXedVirus on 2006-06-25
Didn't work for me either. I have also tried to use a newer kernel, outclude the 8139cp module, it did not work too. So, i think there is a problem with the assigned irq, is there any way to change it ?

---

### Post by ToXedVirus on 2006-06-25
cat /proc/interrupts
```
           CPU0
  0:      30874    IO-APIC-edge  timer
  1:        569    IO-APIC-edge  i8042
  7:          1    IO-APIC-edge  parport0
  8:          3    IO-APIC-edge  rtc
  9:          0   IO-APIC-level  acpi
 10:          0    IO-APIC-edge  MPU401 UART
 12:       2055    IO-APIC-edge  i8042
 14:       1790    IO-APIC-edge  ide0
 50:          2   IO-APIC-level  ehci_hcd:usb2
 58:          3   IO-APIC-level  ohci1394
 66:          0   IO-APIC-level  eth1
217:      11190   IO-APIC-level  libata, eth0
225:       5723   IO-APIC-level  libata, NVidia CK804
233:         13   IO-APIC-level  ohci_hcd:usb1
NMI:          0
LOC:      30723
ERR:          0
MIS:          0

```

66:          0   IO-APIC-level  eth1
217:      11190   IO-APIC-level  libata, eth0

i bet eth1 is my realtek card !
And the zero before it is more then interesting ... Maybe anyone has an idea what's going on ?

---

