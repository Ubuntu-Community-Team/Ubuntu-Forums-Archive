---
title: "Network manager sees wireless, but won't talk to it - 9.10 netbook remix"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by yduras on 2009-12-04
I've just picked up an Acer Aspire One netbook that came with WinXP pre-installed.  When I load WinXP, my wireless connection works fine.  I installed the latest netbook remix, which seemed to go smoothly enough, except that I can't connect to my local wireless.

The Network Manager spots my home network and prompts me for the WEP code, which I enter.  It then churns for several minutes and asks me for the WEP code again.  I've run though that enough times that I'm really sure I am typing in the right code correctly.

I've seen a few comments that folks had the same issue with the 9.10 beta, but those either were left unresolved or were resolved by installing wicd.  I tried the install command for that, but I don't seem to have it already in the library.

I have no wired network, and naturally can't connect to the net, so anything I add is going to have to be ferried over on a flash drive.

This is my first try at Linux, so I'm quite the novice.  The last time I used Unix was well more than decade ago, but I do at least know what command line looks like.

---

### Post by uncaspi on 2009-12-04
This have to do with WEP Wpa etc key password. Look at man iwconfig and run this to add the keycode.

---

### Post by yduras on 2009-12-05
> **uncaspi said:**
> This have to do with WEP Wpa etc key password. Look at man iwconfig and run this to add the keycode.
  
I'm sorry.  I think I need more detail.  All I get doing that is "Operation not supported" and I don't have enough context to guess where I am going wrong.

It says SET failed on device ...; Operation not supported.

---

### Post by yduras on 2009-12-05
So, in the course of hunting around, I found this post about manually setting up wireless: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
How cool is that post, eh?

So anyway, I tried this command as suggested ```
lshw -C network
``` to make sure I was using the right interface name.  And, I hope you can forgive me for not posting the output - the computer I am posting from is not the one I'm troubleshooting, because the one I'm troubleshooting won't connect to the internet (which would be why I'm here, right?)  But anyway, that command finds me two networks, wmaster0 and eth0.  wmaster0 is the one with 'wireless' listed amongst its capabilities, so I figure that's what I should be using.

The thing is, when I try the iwconfig dance with wmaster0, I get "Operation not supported" all over the place.

So, to be sure, I gave ```
iwlist scan
``` a  try, and hey, it told me that wmaster0 (and lo and eth0) doesn't support scanning, but this wlan0 sure does.  And under wlan0 I even see my local wireless network.  I don't know why the network check didn't tell me about wlan0 before, but it looked promising so I ran through the iwconfig dance and huzzah! all the commands went through.

Until ```
dhclient wlan0
```.  That one tries real hard, doing its best to connect about five times and then gives up, letting me know "no working leases in persistent database - sleeping"

It's been fun exploration, but the upshot is that I still can't connect my netbook to the local wireless.  It still works fine if I boot WinXP instead, and the Network Manager in Ubuntu still just churns for while an then asks me for the network key over and over.

Does anyone have any suggestions?

---

### Post by uncaspi on 2009-12-06
I think it has something to do with the network key in nm. Have you tried to remove the key in the router or to connect to other local routers which don't require a key? Try nm-tool to get additional info

---

### Post by luomo on 2009-12-06
> **yduras said:**
> 

Until ```
dhclient wlan0
```.  That one tries real hard, doing its best to connect about five times and then gives up, letting me know "no working leases in persistent database - sleeping"

It's been fun exploration, but the upshot is that I still can't connect my netbook to the local wireless.  It still works fine if I boot WinXP instead, and the Network Manager in Ubuntu still just churns for while an then asks me for the network key over and over.

Does anyone have any suggestions?
 
**I have the same problem but my network manager doesn't ask for key as it is not needed. Any solution to the above problem is very much appreciated.**

---

### Post by uncaspi on 2009-12-06
It could be a bug. Several postings here indicate that. I don't use a key either so I don't have the problem.

---

### Post by dannyp32 on 2009-12-06
i also have the same problem
when i boot up into the live cd it detects my networks, but when i try to connect it doesnt connect and i am 100% sure that my password was correct (wpa-psk)
i also tried to delete my network, then leave my router insecure and try to connect again, but it doesnt connect.
i am guessing that my wireless usb adapter is working since the networks are detected automatically, but i am having a lot of trouble getting it to connect.

---

### Post by luomo on 2009-12-06
> **uncaspi said:**
> It could be a bug. Several postings here indicate that. I don't use a key either so I don't have the problem.
If it is a bug please tell me how to fix it. Help Please.

---

### Post by coffeeaddict22 on 2009-12-06
Hi,
"Bug" is a little bit too generic.  Can you please post the output of ```
nm-tool
```which will be a lot more helpful in terms of identifying the problem.

---

### Post by luomo on 2009-12-06
**Output of nm-tool:**
[html]
NetworkManager Tool

State: connecting

- Device: wlan0  [UTStarcom] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:    xxxxxxxx    

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    UTStarcom:       Infra, xx:xx:xx:xx:xx:EF, Freq 2462 MHz, Rate 54 Mb/s, Strength 74


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:    xxxxxxxxx    

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
[/html]

---

### Post by coffeeaddict22 on 2009-12-06
If you're not dogmatic about proprietary code, I'd suggest you go into System/Administration/Hardware Drivers and enable the Broadcom STA driver first.

If you're still not going, can you post back the results of ```
lshw -C network
ifconfig
sudo iwlist scan
``` as well?

---

### Post by luomo on 2009-12-07
I has installed STA driver already.
**Output of ifconfig:**
[html]
cyber@cyber-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:06:02:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:50:4e:b0  
          inet6 addr: fe80::21a:73ff:fe50:4eb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2376 (2.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-50-4E-B0-35-30-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[/html]I don't know what "wmaster0" is doing here?
**Output of lshw -C network:**
[html]
cyber@cyber-laptop:~$ sudo lshw -C network
[sudo] password for cyber: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:06:02:cc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:50:4e:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

[/html]

---

### Post by luomo on 2009-12-07
**Output of iwlist scan wlan0:**
[HTML]
y
cyber@cyber-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:57:F4:F7:EF
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"UTStarcom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000011c457187
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 0009555453746172636F6D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014


[/HTML]

---

### Post by uncaspi on 2009-12-07
You could try sudo /sbin/ifdown wmaster0
Btw can you post the contest of /etc/network/interfaces

---

### Post by uncaspi on 2009-12-07
and restart the network sudo /etc/init.d/networking restart

---

### Post by luomo on 2009-12-07
> **uncaspi said:**
>   post the contest of /etc/network/interfaces
[HTML]
auto lo
iface lo inet loopback
[/HTML]

---

### Post by uncaspi on 2009-12-07
Did it help when you used ifdown and restarted the network? Eventually type dhclient wlan0

---

