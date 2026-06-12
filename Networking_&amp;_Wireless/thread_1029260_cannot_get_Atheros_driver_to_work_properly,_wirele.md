---
title: "cannot get Atheros driver to work properly, wireless not detected"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by vladin8tor on 2009-01-03
Hi,

I have installed support for Atheros 802.11 wireless lan cards after I installed ubuntu OS.

in the network connections and network tools it doesnt seem to detect wifi device.
it displays only l0 and eth0.

I have spent whole day looking for some answers but I cannot find why the wifi device wont detect.

I have also run some diagnostics from post of this forum which gave some more info.

I have tried installing other drivers, packages from sypnctic package manager etc.

I have Acer aspire 5520g laptop, with Ubuntu 8.10 installed.
Anyways please help.




05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Device 0428
        Flags: fast devsel, IRQ 19
        Memory at d0400000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: ath5k, ath_pci

root@vlad-laptop:/etc/modprobe.d# lshw -C Network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:e0:d0:8c
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.11 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:69:e7:d5:62:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@vlad-laptop:/etc/modprobe.d# 


root@vlad-laptop:/etc/modprobe.d# wifi-radar
No wifi-device found. Exiting.
root@vlad-laptop:/etc/modprobe.d# 

root@vlad-laptop:/etc/modprobe.d# lspci -nn
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
root@vlad-laptop:/etc/modprobe.d#

---

### Post by vladin8tor on 2009-01-03
ahh please help someone

---

### Post by devlin7 on 2009-01-03
Yeah, a bad decision (personal opinion) by the Ubuntu team to ***disable*** the Atheros driver in the Linux kernel is the problem. From what I've read it was because it interfered with MadWifi. I still don't get why they'd disable a driver because it interfered with an optional component. The solution however is installing MadWifi or re-enabling the driver I believe. Just search google for **Ubuntu+atheros driver**. You'll find solutions abound.

It's kind of funny that in **U**buntu **N**etbook **R**emix the driver is enabled if you installed via the UNR iso. 

Devlin
Happy owner of Aspire One running Ubuntu Netbook Remix 1.0.1

---

### Post by tomszyszko on 2009-01-03
Remove the Existing ubuntu driver in system>administration>hardware drivers uncheck them

Search for madwifi-hal-0.10.5.6-r3835-20080801 in google 

download then open a terminal, type 
```
cd <the place you downloaded it too>
make
sudo make install
<when it asks you type in your password>
```
Then restart
If everything worked a list of networks should appear in network manager (were the little 2 computers icons used 2 be)

---

### Post by superprash2003 on 2009-01-03
or you could try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by vladin8tor on 2009-01-03
> **tomszyszko said:**
> Remove the Existing ubuntu driver in system>administration>hardware drivers uncheck them

Search for madwifi-hal-0.10.5.6-r3835-20080801 in google 

download then open a terminal, type 
```
cd <the place you downloaded it too>
make
sudo make install
<when it asks you type in your password>
```
Then restart
If everything worked a list of networks should appear in network manager (were the little 2 computers icons used 2 be)

Thanks Tom,
I downloaded madwifi-hal-0.10.5.6-r3875-20081105

and ran make and make install

and rebooted comp but when i type ifconfig doesnt come up with new network device.

i followed this url for instructions:

[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by vladin8tor on 2009-01-03
> **superprash2003 said:**
> or you could try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

i tryed that aswell.. i dont know should i try red hat linux??

---

### Post by 2hot6ft2 on 2009-01-03
It's been solved here.
> **luks911 said:**
> The drivers that work are the last madwifi version[0] (before compile and install it you have to disable the ath_pci you are using from System > Administration > Restricted Drivers Manager) or, more simple, the ath5k driver. To use ath5k install linux-backports-modules-intrepid
```
sudo aptitude install linux-backports-modules-intrepid
```
and then you can enable it in System > Administration > Restricted Drivers Manager, where you will saw a driver for Atheros 5xxx.

[0] [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz)

You're using ubuntu so instead of ```
sudo aptitude install linux-backports-modules-intrepid

```
use```
sudo apt-get install linux-backports-modules-intrepid
```

One more thing
> **Biochem said:**
> Thanks Luks, that exactly what I was looking for.

For further reference I needed to blacklist the ath_pci module and load the ath5k module
To blacklist those open a terminal
Applications>Accessories>Terminal
and use
```
gksudo gedit /etc/modeprobe.d/madwifi
```
and remove the # before each then save it and close it.

---

### Post by vladin8tor on 2009-01-03
> **2hot6ft2 said:**
> It's been solved here.


You're using ubuntu so instead of ```
sudo aptitude install linux-backports-modules-intrepid

```
use```
sudo apt-get install linux-backports-modules-intrepid
```

One more thing

To blacklist those open a terminal
Applications>Accessories>Terminala
and use
```
gksudo gedit /etc/modeprobe.d/madwifi
``` 
and remove the # before each then save it and close it.


Okay I have deactived all drivers in hardware changes.
also have blacklisted auth_pci.

then i downloaded wifi module, extracted it.
make all, then make install

then still no devices are installed

i did this twice now following instructions from here.

[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

I really dont get what im doing wrong.

---

### Post by vladin8tor on 2009-01-03
ah i got it working and when i rebooted doesnt work this sux

---

### Post by vladin8tor on 2009-01-03
well i installed old windows xp pro sp3

its alot better than vista :)

although ubuntu looks really kewl and has tons of usefull packages.

---

