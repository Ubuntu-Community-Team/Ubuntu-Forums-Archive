---
title: "I cant get my wirless working"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by pstap92 on 2009-12-07
I just installed Ubuntu v. 9.04 and my wireless card wont work. It doesn't have an on/off switch it just turns on when its plugged in on xp. But in Ubuntu the light doesn't even turn on. Also I searched through "Synaptic package manager" and nor Ndsiwrapped or ndsigtk are in there.

---

### Post by uncaspi on 2009-12-07
I need som more info. Is it an USB-card? If so check lsusb to se if it is there.Will you also post lshw -C network and sudo /sbin/ifconfig
We'll start with this.

---

### Post by pstap92 on 2009-12-08
[LEFT]Thank you :D but i cant do it right now, its a school night. 
[/LEFT]

---

### Post by pramtung on 2009-12-08
try lshw, if you can see your hardware listed there, that's mean you just need one more step.

sudo modprobe [something]

:p

---

### Post by pstap92 on 2009-12-08
Uscapi, it is a usb card thanks. and the results of *lshw -C network *are 
```
      *-network               
           description: Ethernet interface
           product: nForce2 Ethernet Controller
           vendor: nVidia Corporation
           physical id: 4
           bus info: pci@0000:00:04.0
           logical name: eth0
           version: a1
           serial: 00:40:ca:85:58:20
           width: 32 bits
           clock: 66MHz
           capabilities: bus_master cap_list ethernet physical
           configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
      *-network DISABLED
           description: Ethernet interface
           physical id: 2
           logical name: pan0
           serial: ae:93:cf:bd:de:d4
           capabilities: ethernet physical
           configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  
```

The results of [I]sudo /sbin/ifconfig are:
[/I]```
    eth0      Link encap:Ethernet  HWaddr 00:40:ca:85:58:20  
  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
  
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
            Interrupt:22 Base address:0xe000 
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
  
    [FONT=&quot][/FONT]   
  
```

---

### Post by uncaspi on 2009-12-10
Your eth0 connection should at least work if you put in the wire and type sudo dhclient eth0

---

### Post by pstap92 on 2009-12-10
I dont have any ports near my computer.

---

### Post by scape02 on 2009-12-10
> **pstap92 said:**
> I just installed Ubuntu v. 9.04 and my wireless card wont work. It doesn't have an on/off switch it just turns on when its plugged in on xp. But in Ubuntu the light doesn't even turn on. Also I searched through "Synaptic package manager" and nor Ndsiwrapped or ndsigtk are in there.


Ok here is a flaw i found in ubuntu, unplug your usb device, restart the pc, wait 2-3 mins and plug back in, then wait about 4-6 minutes and linux should recognize your usb device. At first i was thinking the same thing about my wifi receiver, but this did solve the problem.

---

### Post by pstap92 on 2009-12-13
Scape 02 it didnt work.

---

### Post by shade5 on 2009-12-13
Try running jockey-gtk and see if you find drivers that were not licensed to install. I downloaded mine for my PCI card. Not sure if it works for usb cards too.

Also run iwconfig and lsusb and post results. It might be useful.

---

### Post by pstap92 on 2009-12-14
Shade5, the *jockey-gtk *did not return any results, but this is what i got from the other commands you requested: 

Results of *lsusb*
```
    [FONT=OpenSymbol]peter[/FONT]@ubuntu:~$ lsusb
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 003 Device 002: ID 0a48:3239 I/O Interconnect Multimedia Card Reader
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 006: ID 1630:ff81  
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
```

The results of  [I]iwconfig
[/I]```

   [FONT=OpenSymbol]peter[/FONT]@ubuntu:~$ sudo iwconfig
  
  lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  pan0      no wireless extensions.
  
  
```

---

