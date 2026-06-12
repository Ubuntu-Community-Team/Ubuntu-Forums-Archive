---
title: "wireless says i am connected not i can't access the internet..."
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by heathmc on 2011-02-20
just like the title says, it says that it has connected to my wireless network but when i go to firefox i can get online...

---

### Post by heathmc on 2011-02-20
hey, i have a wired connection that works, when i connect to my wireless network it says connected but it does not work.
any ideas?

---

### Post by elliotbeken on 2011-02-20
can you ping your router ? or another device in your LAN ?

open terminal> type "ping 192.168.1.1" <<<< change to suit your environment

---

### Post by grahammechanical on 2011-02-20
You need to give more information. In what way does it not work? What version of Ubuntu are you using? What machine do you have? Is this a home connection to a modem/router? Or is it some other kind of network? What do you do to connect?

Here is a link to the Wireless Trouble Shooting Guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

---

### Post by heathmc on 2011-02-20
while plugged into my router i typed in "ping my ip" and got this

```
meg@meg-Latitude-D505:~$ ping 192.168.2.10
PING 192.168.2.10 (192.168.2.10) 56(84) bytes of data.
64 bytes from 192.168.2.10: icmp_req=1 ttl=64 time=0.047 ms
64 bytes from 192.168.2.10: icmp_req=2 ttl=64 time=0.039 ms
64 bytes from 192.168.2.10: icmp_req=3 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=4 ttl=64 time=0.046 ms
64 bytes from 192.168.2.10: icmp_req=5 ttl=64 time=0.045 ms
64 bytes from 192.168.2.10: icmp_req=6 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=7 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=8 ttl=64 time=0.038 ms
64 bytes from 192.168.2.10: icmp_req=9 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=10 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=11 ttl=64 time=0.046 ms
64 bytes from 192.168.2.10: icmp_req=12 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=13 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=14 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=15 ttl=64 time=0.049 ms
64 bytes from 192.168.2.10: icmp_req=16 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=17 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=18 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=19 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=20 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=21 ttl=64 time=0.069 ms
64 bytes from 192.168.2.10: icmp_req=22 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=23 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=24 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=25 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=26 ttl=64 time=0.047 ms
64 bytes from 192.168.2.10: icmp_req=27 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=28 ttl=64 time=0.051 ms
64 bytes from 192.168.2.10: icmp_req=29 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=30 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=31 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=32 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=33 ttl=64 time=0.044 ms
64 bytes from 192.168.2.10: icmp_req=34 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=35 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=36 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=37 ttl=64 time=0.044 ms
64 bytes from 192.168.2.10: icmp_req=38 ttl=64 time=0.038 ms
64 bytes from 192.168.2.10: icmp_req=39 ttl=64 time=0.045 ms
64 bytes from 192.168.2.10: icmp_req=40 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=41 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=42 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=43 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=44 ttl=64 time=0.044 ms
64 bytes from 192.168.2.10: icmp_req=45 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=46 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=47 ttl=64 time=0.037 ms
64 bytes from 192.168.2.10: icmp_req=48 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=49 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=50 ttl=64 time=0.038 ms
64 bytes from 192.168.2.10: icmp_req=51 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=52 ttl=64 time=0.039 ms
64 bytes from 192.168.2.10: icmp_req=53 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=54 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=55 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=56 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=57 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=58 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=59 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=60 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=61 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=62 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=63 ttl=64 time=0.044 ms
64 bytes from 192.168.2.10: icmp_req=64 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=65 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=66 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=67 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=68 ttl=64 time=0.046 ms
64 bytes from 192.168.2.10: icmp_req=69 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=70 ttl=64 time=0.047 ms
64 bytes from 192.168.2.10: icmp_req=71 ttl=64 time=0.049 ms
64 bytes from 192.168.2.10: icmp_req=72 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=73 ttl=64 time=0.050 ms
64 bytes from 192.168.2.10: icmp_req=74 ttl=64 time=0.043 ms
64 bytes from 192.168.2.10: icmp_req=75 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=76 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=77 ttl=64 time=0.037 ms
64 bytes from 192.168.2.10: icmp_req=78 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=79 ttl=64 time=0.044 ms
64 bytes from 192.168.2.10: icmp_req=80 ttl=64 time=0.064 ms
64 bytes from 192.168.2.10: icmp_req=81 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=82 ttl=64 time=0.059 ms
64 bytes from 192.168.2.10: icmp_req=83 ttl=64 time=0.045 ms
64 bytes from 192.168.2.10: icmp_req=84 ttl=64 time=0.036 ms
64 bytes from 192.168.2.10: icmp_req=85 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=86 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=87 ttl=64 time=0.035 ms
64 bytes from 192.168.2.10: icmp_req=88 ttl=64 time=0.046 ms
64 bytes from 192.168.2.10: icmp_req=89 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=90 ttl=64 time=0.063 ms
64 bytes from 192.168.2.10: icmp_req=91 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=92 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=93 ttl=64 time=0.038 ms
64 bytes from 192.168.2.10: icmp_req=94 ttl=64 time=0.035 ms
64 bytes from 192.168.2.10: icmp_req=95 ttl=64 time=0.044 ms
64 bytes from 192.168.2.10: icmp_req=96 ttl=64 time=0.059 ms
64 bytes from 192.168.2.10: icmp_req=97 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=98 ttl=64 time=0.041 ms
64 bytes from 192.168.2.10: icmp_req=99 ttl=64 time=0.042 ms
64 bytes from 192.168.2.10: icmp_req=100 ttl=64 time=0.040 ms
64 bytes from 192.168.2.10: icmp_req=101 ttl=64 time=0.042 ms
```and it went on and on

---

### Post by Bucky Ball on 2011-02-20
Getting good ping response there.

In your wireless setup have you got the appropriate DNS addresses provided by your ISP? 

(Right click network icon>Edit Connections>Wireless>IPv4 settings.)

---

### Post by heathmc on 2011-02-20
1. i am using a dell d505
2. just did a fresh format and install of 10.10 desktop
3. when i plug into my router it works fines
4. when i go to wireless networks it says "disconntected" , sometimes it will connect and say 82-93% strength but when i go to a webpage it says can not be found
5. i have gone to system- admin- add drivers and my b43 wireless driver is installed and running.

---

### Post by Hakunka-Matata on 2011-02-20
Has firefox switched to '_W_ork _O_ffline' mode?  that sometimes happens to me if I try to use firefox when there is no internet connection.

---

### Post by Bucky Ball on 2011-02-20
Right click network icon>Edit Connections>Wireless>IPv4 settings.

Have you got the correct DNS IPs there, normally provided by your ISP?

---

### Post by Bucky Ball on 2011-02-20
I have noticed you have double posted this problem. Against forum rules and I am going to ask mods to merge threads. ;)

---

### Post by heathmc on 2011-02-20
in ipv4 under method i have "automatic DHCP"

---

### Post by lisati on 2011-02-20
Threads merged. Please do not start multiple threads for the same problem.

---

### Post by heathmc on 2011-02-20
thank you, i am new please be patient again thanks

---

### Post by heathmc on 2011-02-20
also, i am not in "work offline" mode and it does the same thing in chrome as well

---

### Post by lisati on 2011-02-20
> **Bucky Ball said:**
> I have noticed you have double posted this problem. Against forum rules and I am going to ask mods to merge threads. ;)

Noted.

It could be related to the "no firmware" problem the OP reported elsewhere.

---

### Post by heathmc on 2011-02-20
so is, "automatic" bad? how would i go about getting my dns address and what should i do then?
------------------ i am no longer "missing firmware" i have since done a clean install which fixed that problem but gave me another....

---

### Post by Bucky Ball on 2011-02-20
Auto is fine if your router is serving you an IP address and by the looks it is. Your ISP will be able to provide approriate DNS addresses (although that may not be the problem) probably available on their website or their setup guide.

I use static IPs myself as it makes it easier to identify the four machines in the house but your setup looks okay, at least on the LAN, else you wouldn't be getting a ping response.

All other machines getting internet fine through this router or the Windows install if you are dual booting? If you are dual-booting you may want to check details in the wireless setup in Windows and make sure details match those in your Ubuntu wireless setup.

---

### Post by Hakunka-Matata on 2011-02-20
> **heathmc said:**
> 1. i am using a dell d505
2. just did a fresh format and install of 10.10 desktop
3. when i plug into my router it works fines
4. when i go to wireless networks it says "disconntected" , sometimes it will connect and say 82-93% strength but when i go to a webpage it says can not be found
5. i have gone to system- admin- add drivers and my b43 wireless driver is installed and running.

b43 wireless driver:  That's a notorious one.  Broadcom wireless cards can be a real pain to get configured correctly.  Since you said you're strength is @ 82-93% it sounds like you don't have the right driver installed.  Look @ the following Link for explanation: [http://ubuntuforums.org/showthread.php?t=1686852]("http://ubuntuforums.org/showthread.php?t=1686852")

---

### Post by Bucky Ball on 2011-02-20
STA might be worth a try. That should also be in Additional Drivers.

ps: Nothing wrong with your signal strength really. Your ping results report an excellent speed.

---

### Post by heathmc on 2011-02-21
hey, i am still not sure what it is you want we to do? but in answer to your question the dell d505 is the only machine running linux, it does not dual boot, it does not even have windows installed. i have 3 other laptops, running vista ultimate that can access the router just fine.

---

### Post by Hakunka-Matata on 2011-02-21
Let's see what version b43 wireless you have:  What is the output from code```
lspci -vnn | grep 14e4
```

---

### Post by Hakunka-Matata on 2011-02-21
```
Code:

meg@meg-Latitude-D505:~$ ping 192.168.2.10
PING 192.168.2.10 (192.168.2.10) 56(84) bytes of data.
64 bytes from 192.168.2.10: icmp_req=1 ttl=64 time=0.047 ms
64 bytes from 192.168.2.10: icmp_req=2 ttl=64 time=0.039 ms
64 bytes from 192.168.2.10: icmp_req=3 ttl=64 time=0.043 ms

```

Something looks strange here, I've never seen a LAN using 192.168.2.x IP address.  I use either 192.168.1.x or 192.168.16.x, which are reserved for private use, i.e. 'Non-Route-able'.  Is 192.168.2.x also non-route-able?  

Any comments appreciated.........

---

### Post by Hakunka-Matata on 2011-02-21
> **Bucky Ball said:**
> STA might be worth a try. That should also be in Additional Drivers.

ps: Nothing wrong with your signal strength really. Your ping results report an excellent speed.

@Bucky Ball;  I agree that the signal strength is sufficient, however with Broadcom's b43xx series, and it's many different hardware versions and drivers, I've experienced varying signal strength while I've had the interface *almost* working, but only *almost*.  It would be dropping out and coming back on during that configuration.  Once I got the correct drivers, and got them installed correctly, the signal strength would be rock solid and the interface would not be dropping any packets.  That's what made me think the OP might have something wrong in the driver setup.  Well, that plus the fact it's a Broadcom b43xx series piece of hardware.

Do you have an opinion on the 192.168.2.X range?, private?, or routeable?

---

### Post by Hakunka-Matata on 2011-02-21
Drat, answered my own question:> Private Address Space

The Internet Assigned Numbers Authority (IANA) has reserved the
following three blocks of the IP address space for private networks:

10.0.0.0 - 10.255.255.255
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255

In other words 10.123.123.123 is a private non-routable

Read more: [http://wiki.answers.com/Q/What_is_a_nonroutable_IP_address#ixzz1EcFLaPB3](http://wiki.answers.com/Q/What_is_a_nonroutable_IP_address#ixzz1EcFLaPB3)


---

### Post by PeMa GonGo on 2011-02-21
can confirm this issue on a dell laptop with a 
```
Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 6b-93-e1-ff-ff-3d-00-1f
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
```
happens around 50% of the time my guess is, that it is causes by the internal powermanagment, and NetworkManager doesn't notice this... but wicd does..  newest ubuntu up-to-date

---

### Post by Hakunka-Matata on 2011-02-21
> happens around 50% of the time my guess is, that it is causes by the internal powermanagment, and NetworkManager doesn't notice this... but wicd does.. newest ubuntu up-to-date
Last edited by PeMa GonGo; 21 Minutes Ago at 10:26 AM..
PeMa GonGo is online now Report Post   	Reply With Quote

what "happens around 50% of the time"?  thanks.

---

