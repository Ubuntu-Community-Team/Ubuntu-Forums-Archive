---
title: "Can't connect to the router"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by maqtanim on 2012-06-23
I am using Ubuntu 12.04.

Previously I was using a DSL connection. I used to connect that network using **[FONT=Courier New]pppoeconf[/FONT]**.[FONT=Arial] Recently[/FONT] I bought a new connection (to be precisely [this one]("http://ollo.com.bd/devices/indoor")). After connecting the cable to my PC, Ubuntu doesn't get the modem. Even I can't access the router admin panel by typing 192.***.***.***. 

Any Help?

---

### Post by maqtanim on 2012-06-28
* Bump *

---

### Post by linux6994 on 2012-06-28
In a terminal window type ifconfig what do you see? Remember you are no longer using the DSL entry in Network Connections it needs to be removed. Under the Wired section you need to have an entry "Wired connection 1" or some other name which has Automatic (DHCP) set.

---

### Post by critin on 2012-06-28
Turn the machine off.  Make sure the router is turned on and start the machine.   It should be on before the computer is turned on for the system to find it,  are all the lights lit?

---

### Post by maqtanim on 2012-06-29
> **linux6994 said:**
> In a terminal window type ifconfig what do you see? Remember you are no longer using the DSL entry in Network Connections it needs to be removed. Under the Wired section you need to have an entry "Wired connection 1" or some other name which has Automatic (DHCP) set.

The result of ifconfig is:
```
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8512 (8.5 KB)  TX bytes:8512 (8.5 KB)

```

I've totally removed/deleted the DSL connection from the network manager. But there is not any wired network listed either (like your screen shot). May be the settings from the previous DSL connection making some conflicts. But I don't know how to solve the conflict.

---

### Post by maqtanim on 2012-06-29
> **critin said:**
> Turn the machine off.  Make sure the router is turned on and start the machine.   It should be on before the computer is turned on for the system to find it,  are all the lights lit?

Followed your instruction and all the lights of the router lit during the procedure. No problem with the router, I can even connect to that router and browse internet with another laptop (which is running Ubuntu 12.04) with both the wired and wireless connection.

---

### Post by linux6994 on 2012-06-29
Your eth0 is not being seen since you just have the loopback showing? Do a 'lspci' and see what you have hardware wise?

---

### Post by steeldriver on 2012-06-29
hi maybe nm-tool will shed some light on the matter:

```
nm-tool
```

also check your /etc/network/interfaces to see if there's any left over stuff about your pppoe connection in there

```
cat /etc/network/interfaces
```

---

### Post by SparTacux on 2012-06-29
I'm  not at all familiar with the version of Ubuntu you are using. But..I  would try and manually set up your network connection using your  Administrator account and make sure you have allowed the connection to  be used by all users.

Also check the Ethernet  LED on the network card on your computer to see if it's lit and flashing.

If that don't work- buy a book on Relaxation & Calming Exercises and prepare yourself for a few hours of stress and burnout :wink:
 		                   		  		  		 		 			 				__________________
				You can take my trousers but you won't take my Freedom ! 			
 		 		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12062985") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12062985")

---

### Post by maqtanim on 2012-06-29
> **linux6994 said:**
> Your eth0 is not being seen since you just have the loopback showing? Do a 'lspci' and see what you have hardware wise?

```
lspci

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)


```

> **steeldriver said:**
> hi maybe nm-tool will shed some light on the matter:

```
nm-tool
```also check your /etc/network/interfaces to see if  there's any left over stuff about your pppoe connection in there

```
cat /etc/network/interfaces
```
```

nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unmanaged
  Default:           no
  HW Address:        E0:69:95:90:BC:E4

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```
```

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
```

---

### Post by steeldriver on 2012-06-29
well first off I would comment out (or delete) the lines relating to eth0 in your /etc/network/interfaces file, and then do

```
sudo service network-manager restart
```

it would also be a good idea to check that there's nothing related to 'unmanaged-devices' in /etc/NetworkManager/NetworkManager.conf

---

### Post by SparTacux on 2012-06-29
If you need a good relaxation techniques book then give me a nod and I'll point you in the right direction. They should be delivered in PDF format with every new UBUNTU release :-)

---

### Post by maqtanim on 2012-07-01
> **steeldriver said:**
> well first off I would comment out (or delete) the lines relating to eth0 in your /etc/network/interfaces file, and then do

```
sudo service network-manager restart
```it would also be a good idea to check that there's nothing related to 'unmanaged-devices' in /etc/NetworkManager/NetworkManager.conf

Thanks a lot! It worked! :D

> **SparTacux said:**
> If you need a good relaxation techniques book  then give me a nod and I'll point you in the right direction. They  should be delivered in PDF format with every new UBUNTU release :smile:

oh ... the problem is solved. No more relaxation technique is required. :D

---

### Post by SparTacux on 2012-07-01
LOL - Well done

I was hoping to make some money selling this book of mine ;-)

---

