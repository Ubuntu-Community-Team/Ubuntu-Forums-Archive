---
title: "Need help. Wireless not working. Please, any info appreciated."
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by rshrc1 on 2009-08-16
I am a total Linux-noob and really have only used it in virtual machines properly despite having it installed on one of my two computers. Both computers have wireless adapters.

Any way this is probably annoying but there are three things I really need to do before I can properly use Ubuntu:

1.) Connect to the internet
2.) Network with my 2nd PC
3.) Use Synergy

Today I decided that I wanted to get synergy working between my Vista 64 bit computer on a wireless network and my Ubuntu 8.04 computer (on no network and w/o internet).

 I first tried to use a crossover cable to connect the two and use the Vista's internet connection with no luck. I must admit though, I really didn't have a clue and despite hours of looking, I couldn't find any decent instructions on doing this.

I then installed 9.04 in the hope that it might come with better wireless support, which I hear it does but not for the Ubuntu's card.

I then tried using Ndiswrapper to make another attempt at getting the Ubuntu's wireless card to work (had tried once before but to unfortunately it didn't work). It didn't work this time either and told me I had an invalid .inf file.

Anyway, I'm all out of ideas, I'm sorry this is so long but if can anyone can help me I would greatly appreciate it. If you need more information just ask, thanks.

---

### Post by The Toxic Mite on 2009-08-16
Hey!

Can you go to Applications > Accessories > Terminal, and enter the following commands please?:

```

sudo lshw -c network
lspci
iwconfig
ifconfig

```

Post the outputs of them when you're done :)

---

### Post by rshrc1 on 2009-08-17
sam@sam-ubuntu-desktop:~$ sudo lshw -c network
  
  [sudo] password for sam: 
  
    *-network:0 UNCLAIMED   
  
         description: Ethernet controller
  
         product: Marvell W8300 802.11 Adapter
  
         vendor: Marvell Technology Group Ltd.
  
         physical id: b
  
         bus info: pci@0000:02:0b.0
  
         version: 07
  
         width: 32 bits
  
         clock: 66MHz
  
         capabilities: pm bus_master cap_list
  
         configuration: latency=32
  
    *-network:1
  
         description: Ethernet interface
  
         product: RTL-8139/8139C/8139C+
  
         vendor: Realtek Semiconductor Co., Ltd.
  
         physical id: c
  
         bus info: pci@0000:02:0c.0
  
         logical name: eth0
  
         version: 10
  
         serial: 00:10:dc:80:d6:1d
  
         size: 10MB/s
  
         capacity: 100MB/s
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  
         configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  
    *-network DISABLED
  
         description: Ethernet interface
  
         physical id: 1
  
         logical name: pan0
  
         serial: 86:1f:88:c4:79:93
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  
  sam@sam-ubuntu-desktop:~$ lspci
  
  00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
  
  00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
  
  00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
  
  00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
  
  00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
  
  00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
  
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
  
  00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
  
  00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
  
  00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
  
  00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
  
  01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
  
  02:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
  
  02:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
  
  02:0b.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
  
  02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
  
  sam@sam-ubuntu-desktop:~$ iwconfig
  
  lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  pan0      no wireless extensions.
  
   
   
  sam@sam-ubuntu-desktop:~$ ifconfig
  
  eth0      Link encap:Ethernet  HWaddr 00:10:dc:80:d6:1d  
  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
  
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
            Interrupt:23 Base address:0xc400 
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
  
   
   
  sam@sam-ubuntu-desktop:~$ 





Thanks a lot btw.

---

### Post by superprash2003 on 2009-08-17
take a look at this [http://ubuntuforums.org/showthread.php?t=1194772](http://ubuntuforums.org/showthread.php?t=1194772)

---

### Post by rshrc1 on 2009-08-17
I'll give this ago thnx

---

