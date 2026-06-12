---
title: "Connecting to ADSL Issues"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by chrisjabroni on 2011-04-15
Hi all,

Just to start off I am new to Ubuntu.

I am running Ubuntu 10.10 alongside windows 7

I have a few issues at the moment, one being that it hangs upon bootup. The only way to get Ubuntu to actually boot successfully is to change "splash quiet" into "nomodeset"

Not a major issue, but annoyance none the less.

My issue that concerns me the most is connecting to the internet.

I started off by trying to connect a wireless usb adapter and i struggled to get the drivers installed. I downloaded the ndisweeper and ndispkg in order to install the windows drivers but i only got the .inf driver installed and the windows wireless drivers kept crashing from then on out.

So i figured it would just be easier to plug a dsl line into it and install all updates and drivers that way. Upon plugging in the cord, nothing happened. I tried going into terminal and typing "sudo pppoeconf" and its response is that it couldnt connect to the modem/router.

I would love some help, it would be greatly appreciated. Let me know if anyother information is needed.

Thanks in advance,


Jabroni

---

### Post by sanguinoso on 2011-04-15
Can you post the results of ```
sudo lshw -C network
```

and 
```
ifconfig -a
```

---

### Post by chrisjabroni on 2011-04-15
```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0c:6e:ec:eb:6d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:8800(size=256) memory:d5000000-d5000fff memory:dfee0000-dfefffff


```

and

```
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:ec:eb:6d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26832 (26.8 KB)  TX bytes:26832 (26.8 KB)
```

---

### Post by sanguinoso on 2011-04-15
Was this with your usb wireless card plugged in or no? Was the ethernet cable plugged in at this time? Try typing dhclient with the ethernet cable plugged in.

---

### Post by chrisjabroni on 2011-04-15
Both were plugged in at that time

---

### Post by sanguinoso on 2011-04-15
Did you try typing ```
dhclient
``` in a terminal With the ethernet cable plugged in?

---

### Post by chrisjabroni on 2011-04-15
```
chris@chris-System-Name:~$ dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted
```


Why would it deny?

---

### Post by sanguinoso on 2011-04-15
My apologies type ```
sudo dhclient
```

It denies because you must be the root user to run that command.

---

### Post by chrisjabroni on 2011-04-15
No worries, here it is:

```
chris@chris-System-Name:~$ sudo dhclient
[sudo] password for chris: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:0c:6e:ec:eb:6d
Sending on   LPF/eth0/00:0c:6e:ec:eb:6d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by dineshs on 2011-04-15
>        capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 [COLOR="Red"]link=no[/COLOR] maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:8800(size=256) memory:d5000000-d5000fff memory:dfee0000-dfefffffThe result of sudo lshw -C network says link=no.I think you need to concentrate on this.
Is your ethernet cable OK?
Is it plugged properly?(check the lamp on the card)

---

### Post by chrisjabroni on 2011-04-16
Ok so I tried a couple of things,

Firstly, I tried the ethernet cable on my macbook pro (with air port turned off) and it worked flawlessly.

Secondly, I made sure the connection was properly inserted into the slot of the back of the computer and booted it up in Win7, to my surprise I was having the same issue.

My assumption is that I am probably missing the drivers for that?

*Edit*
I just went into device manager and double checked to make sure there wasn't any devices uninstalled, and the ethernet adapter is said to be installed correctly. I had it check to see if there was any available drivers for it and it said it was up to date.

Any ideas?

---

### Post by chrisjabroni on 2011-04-16
Just some more things i've tried:

I went back into windows 7 and uninstalled the device and reinstalled it ... no change
I tried updating to the newest software for it ... no change
I went into the BIOS and made sure it was enabled ... no change
I reset my BIOS all-together ... no change

Any ideas anyone?

---

### Post by dineshs on 2011-04-16
I dont think it is a driver issue/disabled because sudo lshw -C network output shows normal except link=no.
> Secondly, I made sure the connection was properly inserted into the slot of the back of the computer and booted it up in Win7, to my surprise I was having the same issue. To what device your ethernet cable is plugged ?
I have heard that routers can be configured to ALLOW or DENY network/Internet access by looking  MAC address.You may check your router configuration to ensure that the MAC id of your ethernet card in this machine is allowed (I think).
Pl see [this]("http://ubuntuforums.org/showpost.php?p=7782108&postcount=7")
> you may need to power-cycle the modem. (turn off, leave for a moment, then turn back on) Some modems "lock onto" a specific MAC address.

---

### Post by chrisjabroni on 2011-04-17
Thanks for your help Dineshs,

> **dineshs said:**
> To what device your ethernet cable is plugged ?
I have heard that routers can be configured to ALLOW or DENY network/Internet access by looking  MAC address.You may check your router configuration to ensure that the MAC id of your ethernet card in this machine is allowed (I think).
Pl see [this]("http://ubuntuforums.org/showpost.php?p=7782108&postcount=7")

Currently I have a dsl cable running across my floor and directly into the modem/router

Ok so I unplugged the router/modem for a few moments, let it start back up and I unplugged the dsl cable from the back of the computer and waited for the modem. Once restarted I plugged the dsl cable back into the Ethernet port and nothing had changed.

I also checked through my router settings to see if there was anything being blocked or denied and there are no signs of anything there

Any other ideas?

---

### Post by chrisjabroni on 2011-04-18
Could there be any correlation between the fact that in Win7 it doesn't recognize the dsl cord is connected?

---

### Post by sanguinoso on 2011-04-19
It could be a bad cable do you have a spare? Also, have you verified that this link works with any device?

---

### Post by chrisjabroni on 2011-04-19
I have tried that cable on my macbook pro and it worked no problem :(
I have switched which port I use on the back of the modem for this cable, same issue :(

---

### Post by sanguinoso on 2011-04-19
Does the card light up when you plug the cable in? Could be the card has failed.

---

### Post by josephmills on 2011-04-19
please plug in you usb wifi thingy then could we see a ```
lsusb
```
thank you

---

### Post by chrisjabroni on 2011-04-19
I tried a lsusb early today and this was the outcome

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3108 D-Link System predator Bootloader Download
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

When i went to do it again just now, it just hung with a blinking cursor :(

---

### Post by josephmills on 2011-04-19
> **chrisjabroni said:**
> I tried a lsusb early today and this was the outcome

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3108 D-Link System predator Bootloader Download
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

When i went to do it again just now, it just hung with a blinking cursor :(

close out of the termanal and open a new one lets try this ```
rfkill list all 
``` and  ```
dmesg | grep -e ndis -e wlan
``` and a new ```
lsusb
``` thanks

---

### Post by josephmills on 2011-04-19
could I also see a ```
lspci
``` thanks

---

### Post by chrisjabroni on 2011-04-19
Alright here we go:

rfkill:
```
chris@chris-biwinning:~$ rfkill list all
```

dmesg:
```
chris@chris-biwinning:~$ dmesg | grep -e ndis -e wlan
[   14.011549] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   14.777688] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'KeNumberProcessors'
[   14.777865] ndiswrapper: driver neta5agu (D-Link,06/12/2008,1.5.206.2) loaded
[   14.779237] Modules linked in: snd_hwdep snd_ac97_codec ac97_bus snd_pcm snd_seq_midi ttm snd_rawmidi snd_seq_midi_event drm_kms_helper snd_seq snd_timer ppdev drm snd_seq_device ndiswrapper(+) ns558 parport_pc gameport snd sis_agp i2c_algo_bit lp psmouse soundcore snd_page_alloc serio_raw agpgart shpchp i2c_sis96x parport sis900 floppy mii
[   14.780016]  [<f8301726>] ? mp_init+0x66/0x220 [ndiswrapper]
[   14.780016]  [<f8302e65>] ? ndis_start_device+0x15/0x8d0 [ndiswrapper]
[   14.780016]  [<f82fc0f9>] ? pdoDispatchPnp+0x49/0xf0 [ndiswrapper]
[   14.780016]  [<f82f9766>] ? IofCallDriver+0x56/0xc0 [ndiswrapper]
[   14.780016]  [<f82f9cff>] ? IoSyncForwardIrp+0x7f/0xd0 [ndiswrapper]
[   14.780016]  [<f82fa585>] ? IoAllocateIrp+0x65/0x80 [ndiswrapper]
[   14.780016]  [<f83037b3>] ? NdisDispatchPnp+0x93/0x140 [ndiswrapper]
[   14.780016]  [<f82f9766>] ? IofCallDriver+0x56/0xc0 [ndiswrapper]
[   14.780016]  [<f82fb328>] ? IoSendIrpTopDev+0xe8/0x140 [ndiswrapper]
[   14.780016]  [<f82fb70f>] ? pnp_start_device+0x3f/0x90 [ndiswrapper]
[   14.780016]  [<f82fb9c0>] ? wrap_pnp_start_device+0xe0/0x170 [ndiswrapper]
[   14.780016]  [<f82fbb0e>] ? wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[   14.780016]  [<f82ee325>] ? loader_init+0xb5/0x150 [ndiswrapper]
[   14.780016]  [<f82fc287>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[   14.780016]  [<f81d507f>] ? wrapper_init+0x7f/0xb7 [ndiswrapper]
[   14.780016]  [<f81d5000>] ? wrapper_init+0x0/0xb7 [ndiswrapper]
```

Lsusb:
```
chris@chris-biwinning:~$ lsusb
{Blinking cursor - had to close terminal}
```

Lspci:
```
chris@chris-biwinning:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: ATI Technologies Inc RV730 Pro AGP [Radeon HD 4600 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
```

---

### Post by josephmills on 2011-04-19
could I now see a ```
dmesg | grep sis900
``` Thanks

---

### Post by chrisjabroni on 2011-04-19
> could I now see a
Code:
dmesg | grep sis900


Does ethernet cable need to be plugged in for this one?
I'm sorry if this is a really dumb question, I am new to ubuntu/linux commands 


---

Nice link :) I'd say that's the way this is looking :P

---

### Post by chrisjabroni on 2011-04-19
I ran it without:


```
chris@chris-biwinning:~$ dmesg | grep sis900
[    1.468819] sis900.c: v1.08.10 Apr. 2 2006
[    1.468929] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.886903] Modules linked in: snd_intel8x0(+) radeon snd_hda_codec(+) snd_ac97_codec ac97_bus snd_hwdep snd_pcm snd_seq_midi snd_rawmidi ttm snd_seq_midi_event drm_kms_helper snd_seq snd_timer snd_seq_device ppdev ndiswrapper(+) drm ns558 parport_pc gameport sis_agp snd psmouse i2c_algo_bit serio_raw soundcore lp snd_page_alloc i2c_sis96x agpgart shpchp parport sis900 floppy mii
```

If you need me to run it again with it plugged in just let me know


Thanks!

---

### Post by josephmills on 2011-04-19
how about an ```
rfkill list all
``` if nothing shows up tell us thanks

---

### Post by chrisjabroni on 2011-04-19
I ran it again, and I got no results

---

### Post by josephmills on 2011-04-19
are you using natty?

---

### Post by chrisjabroni on 2011-04-19
I'm using maverick meerkat I believe is the name, 10.10 i know for sure

---

### Post by josephmills on 2011-04-19
I am pretty sure that you need a sis900 firmware folder or something to that nature I wish that I could do more but I am at a loss maybe download the driver (tar.gz)from a different machine create a folder called wireless put the downloaded file in that folder then move the folder to lib/firmware then extract there. that might do the trick but not sure

---

### Post by dineshs on 2011-04-20
If you plugin the USB device and run ```
sudo lshw -C network
```what is the output?

---

### Post by chrisjabroni on 2011-04-20
```
chris@chris-biwinning:~$ sudo lshw -C network
[sudo] password for chris: 
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0c:6e:ec:eb:6d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:8800(size=256) memory:d5000000-d5000fff memory:dfee0000-dfefffff
```

---

