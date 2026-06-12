---
title: "Network Problems"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by erakepio on 2006-02-23
just got linux installed and trying to setup my network connection.  I basically have a network connection to my collages network system which then goes out onto the Internet.

I've got a NIC and an onboard LAN chip.  My collage network allows access to internet according to MAC address...and in this case I've got it setup on the Network interface Card.

in Network, its picked up a eth0 connection and when I attempt to enable this connection it has no effect even tho it says the connection is active.  I've tried installing network drivers for my NIC and i managed to unpack the file...but couldnt get it to install the drivers as im unsure of the commands.  The readme was a little vague.

if anyone could help it'd be much appreciated

---

### Post by joshuapurcell on 2006-02-23
It sounds like the NIC is recognized by the OS since you can see it in the network-admin window (and it shows that it is active). You say that your college allows access to the network based on MAC address... does this mean they need to know your MAC address and have it listed somewhere before giving you access? That's how some cable-based ISPs work, and you can't get internet connection through those types of internet service providers (ISPs) until they know your MAC address.

What does the NIC think is going on? Type this in a terminal:
```
sudo ethtool eth0
```
This should print a little information about your connection status, including whether or not the NIC thinks it is connected to another network device.

You may need your MAC address at some point... you can get that from this command:```
ifconfig eth0
```

What is your gateway? are you able to ping that gateway or anything else on the network?

---

### Post by jamesr on 2006-02-23
You mention that you have both a NIC and an onboard LAN chip. One would assume eth0 equates to the the onboard but that is only the case if it is recognised. But what the other. What type of NIC is it.

I agree that with the previous poster that the output of 

sudo ifconfig -a

would be useful

---

### Post by erakepio on 2006-02-24
thanks for the response guys, my college knows my MAC address for Network Card as I also run a copy of windows on this machine and that doesnt have any problems conecting to the net (through windows).  

the make of the card is a Linksys 1032v3 

i will try and get the other information you need once i get home.

---

### Post by erakepio on 2006-02-24
ok, i got some of the information required. I typed in...

sudo ipconfig -a     and also sudo ipconfig eth0  and it came back that ipconfig was an unknown command.  the rest of the info i got from here...

        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: puag
        Wake-on: g
        Current message level: 0x00000002 (2)
        Link detected: yes

---

### Post by grw on 2006-02-24
I think it should be ifconfig not ipconfig

Have you followed the trouble shooting sticky at start of the forum? If you post some more information, it might be useful

---

### Post by erakepio on 2006-02-24
yeh sorry about that..was my fault trying to get it all  read to quickly hehe.  heres the rest of the info...

eth0      Link encap:Ethernet  HWaddr 00: 50: 8D: D7: E4: F1
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xee00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:61792 (60.3 KiB)  TX bytes:61792 (60.3 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by erakepio on 2006-02-24
looking at that its my onboard LAN card...as doing an ipconfig /all   in windows on my Network Card produced this...


        Connection-specific DNS Suffix  . : zen.port.ac.uk
        Description . . . . . . . . . . . : Linksys EG1032 v3 Instant Gigabit De
sktop Network Adapter Driver

        Physical Address. . . . . . . . . : 00-12-17-59-B0-38
        IP Address. . . . . . . . . . . . . : 148.197.132.236
        Subnet Mask . . . . . . . . . . . : 255.255.240.0
        Default Gateway . . . . . . . .  : 148.197.128.1
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . : Yes

as you can see the MAC address is completely different therefoe not picking up the changes.  I cant seem to get the drivers to install either.  I'm relatively new to Linux and I followed the readme instructions for my network drivers...which ive posted below...but i kept getting "Unkown command"

Quick install with proper kernel settings>

  Unpack the tarball :
	tar vzxf eg1032v3.tgz

  Change to the directory:
	cd eg1032v3

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a

make" isnt recognised.  As i said im relatively new to Linux so any info would be greatly appreciated :)

---

### Post by joshuapurcell on 2006-02-24
Your NIC drivers are already installed correctly.. no need reinstalling different drivers at this time from the looks of it. Your NIC shows that you are connected to another network device, but you are not getting an address. The reason seems to be that for some reason you have a different MAC address under Linux than what you do under Windows. You can change your MAC address under Linux to the same one as what you get under Windows by following these instructions:
[http://ubuntuforums.org/showthread.php?t=77932](http://ubuntuforums.org/showthread.php?t=77932)

Once you have the same MAC addresss then you should automatically get an IP address.

---

### Post by joshuapurcell on 2006-02-24
[QUOTE=erakepio]make" isnt recognised.  As i said im relatively new to Linux so any info would be greatly appreciated :)[/QUOTE]Although you shouldn't have to run these commands (since your current driver seems to be working just fine), you can't run the **make** command without having the **build-essential** package installed (which you can easily do through apt-get or synaptic). Also, you can run **make** without using sudo, but not **make install**.

---

### Post by erakepio on 2006-02-24
no this is my unboard LAN.  the connection you see is running from Windows.  perhaps i never explained it correctly.

In WindowsXP..i connect to their network using my Network Card.  Ubuntu isnt picking up this network card.  It's picking up my on-board LAN.  As when I check Device Manager it's got my onboard LAN there..but my Network Card (which I need to use) is set an "Unknown Device"  hence why i need the drivers.

I cant use my onboard LAN due to its mac address being different.

---

### Post by jamesr on 2006-02-24
Hi,

This is my understanding of the current situation correct me if I am wrong.
The ifconfig only shows one network card  ie the on board and also not picking an address because it is not connected.

Whereas you can connect with the NIC (not the on-board) using Windows but not when using Ubuntu

Can you disable the on-board?
Can you see the additional nic  post the output

lspci

I would not as yet build any modules until we can find the cause of the problem. 

You could fool the univ network by using the macchanger prog as metioned in the link posted by joshuapurcell

---

### Post by erakepio on 2006-02-25
it can see the NIC as an unknowndevice.  although the BIOS picks it up

---

