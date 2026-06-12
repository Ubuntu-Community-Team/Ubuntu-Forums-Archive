---
title: "wireless adaptor"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by freefixkorma on 2009-08-31
hi there i not sure i am posting in the right forum please need some guidance is there any wireless adapter to get internet in my desktop my router is downstairs and my desktop up so i was wondering if there is any internet wireless adaptor to connect my desktop any advice will appreciate please i am with ubuntu 11.5

thanks you

---

### Post by freefixkorma on 2009-09-03
i am with ubuntu 11.4 will someone please tell me what kind of bridge or usb adapter will work with my desktop i can move my router from where it is right now is there any way i can get internet in my desktop is upstairs please any advice will appreciate please can someone advice what to buy to get internet in my desktop thanks
thanks

---

### Post by Iowan on 2009-09-03
Capital letters and punctuation don't cost extra ;)
There is no Ubuntu 11.4 (yet) - 9.04 is stable, 9.10 under development. What kind of adapter were (are?) you using? A couple of commands can be used from a terminal (Applications>Accessories>Terminal) to gain information:```
lshw -C network
ifconfig -a
```

---

### Post by jonobr on 2009-09-03
Also you should try changing your subject line to something a bit more descriptive. Makes people searching for stuff, find solutions a bit easier

---

### Post by freefixkorma on 2009-09-03
actually i am not using any adapter just want some advice what should i get in order to have some internet in my desktop my bad about the version of ubuntu is the latest one i downloaded a couple of month ago my router is downstairs and my desktop upstairs i tried one usb adapter linksys and wont work is there any wireless device  that i can get to work with i running on latest ubuntu on p4 destop thanks for your help hope this is enough info for you guys 
thanks

---

### Post by freefixkorma on 2009-09-05
hi guys i need some advice i am running ubuntu 9.0 on a desktop p4 i do not have any idea how can get wireless  internet in my desktop the thing is that my router i can not move it from where it is now can someone advice me what will be the best wireless bridge to buy or any divice please any ideas i cant not run wires to the desktop will appreciate any guidance in this issue thanks 
thanks again please post
ethernet controler intel corporation 82562ez
modem intel co fa82537ep
usb controler 82801eb/er
pci bridge intel 82801

---

### Post by freefixkorma on 2009-09-05
hi guys i need some advice i am running ubuntu 9.0 on a desktop p4 i do not have any idea how can get wireless internet in my desktop the thing is that my router i can not move it from where it is now can someone advice me what will be the best wireless bridge to buy or any divice please any ideas i cant not run wires to the desktop will appreciate any guidance in this issue thanks 
thanks again please post
    korma@korma-desktop:~$ lspci
  
  00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
  
  00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
  
  00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
  
  00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
  
  00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
  
  00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
  
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
  
  00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
  
  00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
  
  00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
  
  00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
  
  01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
  
  01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
  
  korma@korma-desktop:~$ lshw -c network
  
  WARNING: you should run this program as super-user.
  
    *-network               
  
         description: Ethernet interface
  
         product: 82562EZ 10/100 Ethernet Controller
  
         vendor: Intel Corporation
  
         physical id: 8
  
         bus info: pci@0000:01:08.0
  
         logical name: eth0
  
         version: 02
  
         serial: 00:11:11:2a:65:37
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: bus_master cap_list ethernet physical
  
         configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  
    *-network DISABLED
  
         description: Ethernet interface
  
         physical id: 1
  
         logical name: pan0
  
         serial: 16:be:8d:da:cf:27
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  
  korma@korma-desktop:~$ sudo
  
  usage: sudo -h | -K | -k | -L | -l | -V | -v
  
  usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
  
              {-i | -s | <command>}
  
  usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
  
  korma@korma-desktop:~$ lshw -C network
  
  WARNING: you should run this program as super-user.
  
    *-network               
  
         description: Ethernet interface
  
         product: 82562EZ 10/100 Ethernet Controller
  
         vendor: Intel Corporation
  
         physical id: 8
  
         bus info: pci@0000:01:08.0
  
         logical name: eth0
  
         version: 02
  
         serial: 00:11:11:2a:65:37
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: bus_master cap_list ethernet physical
  
         configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  
    *-network DISABLED
  
         description: Ethernet interface
  
         physical id: 1
  
         logical name: pan0
  
         serial: 16:be:8d:da:cf:27
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  
  korma@korma-desktop:~$ ifconfig -a
  
  eth0      Link encap:Ethernet  HWaddr 00:11:11:2a:65:37  
  
            inet6 addr: fe80::211:11ff:fe2a:6537/64 Scope:Link
  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
  
            RX packets:120 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:565 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:18984 (18.9 KB)  TX bytes:46242 (46.2 KB)
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:184 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:16252 (16.2 KB)  TX bytes:16252 (16.2 KB)
  
   
   
  pan0      Link encap:Ethernet  HWaddr 16:be:8d:da:cf:27  
  
            BROADCAST MULTICAST  MTU:1500  Metric:1
  
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by puppywhacker on 2009-09-05
Hi,

Ask the same question in a computer shop. I would prefer a "wireless PCI card"

An "wireless USB stick"  is also an option

---

### Post by bapoumba on 2009-09-06
Threads merged.

---

