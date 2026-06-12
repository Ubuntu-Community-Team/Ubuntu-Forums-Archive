---
title: "linksys and ubuntu"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by THE_MAC on 2009-04-22
i just built a linux box of ubuntu and i have a linksys wireless card.
pci adapter model number wmp54g but why cant i get ubuntu to see it ?

is thier soemthing else i must do to get it going?
it is not onthe internet cause this is the only way i can connect. their is no lan connection. all i have is the linksys card. my neighbor which is a really nice guy is gonna give me his wep key to get access. how can i get ubuntu to see this card and work.. i have never used nything else besides windows before.. this is a new style of computer for me, tho i like ubuntu cause it does everything i need so far, but getting on the internet is very important to me and what i do. any help will be appreciated greatly. 
thank you for taking the time to read this guys!!!

---

### Post by cariboo on 2009-04-23
Could you open an Applications-->Accessories-->Terminal and type:

```
lshw -C network
```

and paste the output in your next post.

---

### Post by Padraig Notlad on 2009-04-24
> **cariboo907 said:**
> Could you open an Applications-->Accessories-->Terminal and type:

```
lshw -C network
```

and paste the output in your next post.
Maybe you can help me.  I'm running Ubuntu 8.10 - the Intrepid Ibex.  My system does use the linksys wmp54g card, but when I ran the command you said for the other guy, I get this.  Looks like Ubuntu isn't seeing this card as a Linksys?  The reason I'm looking for help is, I constantly have inconsistent performance with it.  I have other computers using my router, and they all work great.  I'm suspect to the card, but don't know if it's a driver problem or a device problem.  I'm trying to figure out what the problem is before I go spend money on a new card.
----------------------------------------------------------------------------------
padraig@Notlads-Ubuntu:~$ sudo lshw -C network
[sudo] password for padraig: 
  *-network               
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wmaster0
       version: 01
       serial: 00:12:17:99:96:0a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.18.113 latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:05:34:b4:2e:97
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
-------------------------------------------------------------------------------

I also see these messages in my logs.  Any ideas?

-------------------------------------------------------------------------------
Apr 24 09:22:18 Notlads-Ubuntu NetworkManager: <debug> [1240579338.479637] periodic_update(): Roamed from BSSID 00:16:B6:AA:92:F3 (IT_WAP) to (none) ((none)) 
Apr 24 09:22:24 Notlads-Ubuntu NetworkManager: <debug> [1240579344.483702] periodic_update(): Roamed from BSSID (none) ((none)) to 00:16:B6:AA:92:F3 (IT_WAP) 
Apr 24 09:24:18 Notlads-Ubuntu NetworkManager: <debug> [1240579458.559659] periodic_update(): Roamed from BSSID 00:16:B6:AA:92:F3 (IT_WAP) to (none) ((none)) 
Apr 24 09:24:24 Notlads-Ubuntu NetworkManager: <debug> [1240579464.563644] periodic_update(): Roamed from BSSID (none) ((none)) to 00:16:B6:AA:92:F3 (IT_WAP) 
Apr 24 09:26:18 Notlads-Ubuntu NetworkManager: <debug> [1240579578.639635] periodic_update(): Roamed from BSSID 00:16:B6:AA:92:F3 (IT_WAP) to (none) ((none)) 
Apr 24 09:26:24 Notlads-Ubuntu NetworkManager: <debug> [1240579584.643648] periodic_update(): Roamed from BSSID (none) ((none)) to 00:16:B6:AA:92:F3 (IT_WAP)

---

### Post by THE_MAC on 2009-04-26
> **cariboo907 said:**
> Could you open an Applications-->Accessories-->Terminal and type:

```
lshw -C network
```

and paste the output in your next post.


here is my results

 *-network DISABLED      
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:c4:51:03:5f:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by SeanSov on 2009-05-02
I have a WMP54G PCI wireless NIC.  The FCC-id on the card is PKW-WMP54GV2, so I assume it is the version 2 card.  I am having the same problem as the THE_MAC.  My output is as follows:

sean@sean-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:07:e9:4f:3e:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:12:17:94:f6:ea
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 62:23:74:44:f9:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I also do not have access to a wired network without moving the computer from the garage apt., where I reside, to the house.  However, when I plugged an Ethernet cable into my wired NIC and plugged it into the Ethernet port on my MacBook, there was a connection that showed up in the Network Connections applet on the taskbar of Gnome called 'Auto eth0'.  I tried to turn on internet connection sharing on the MacBook, and was unable to get the MacBook to assign an IP address to the Ubuntu computer.  However, the 'Ethernet Interface (eth0)' on the Network Tools applet in Ubuntu gave an IP of 192.168.2.8.  This sounds like an address on the network of my wireless router, only it is showing up under the Ethernet card.  Also, I tried to log into my router using it's IP 192.168.2.1 on Ubuntu FireFox and no luck there either.  When I click the two computers or wireless meter that show up on the taskbar in Ubuntu, the 'Wired Network' and 'Wireless Networks' options are greyed out.

---

