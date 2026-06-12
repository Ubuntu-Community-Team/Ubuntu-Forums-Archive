---
title: "How to install wifi wireless driver Atheros AR5007EG in Ubuntu Jaunty?"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by dummiebeginner on 2009-04-28
After countless tries to make this Atheros AR5007EG wifi driver work in Ubuntu Jaunty I managed to make it work.

See post #10 below ([http://ubuntuforums.org/showpost.php?p=7201345&postcount=10](http://ubuntuforums.org/showpost.php?p=7201345&postcount=10))

---

### Post by ktechman on 2009-04-28
You may need the Compat-Wireless solution use google to run it down.

---

### Post by roadrash on 2009-04-28
This AR5007EG interface was actually working in either the beta or RC release of the latest 9.04 Jaunty but I just installed the Final and its not working again.  Is there anywhere the Beta or RC releases are kept so I can get it again? or does anyone know if there is something being done to fix it.

---

### Post by dummiebeginner on 2009-04-30
anyone please?

---

### Post by t0mppa on 2009-04-30
Well, you could simply just check which driver Mandriva 2009.0 & PCLinuxOS use to make it work and then install that one to Ubuntu as well.

To see what driver the interface is using, just open a terminal and run either of these two commands: ```
lspci -vv
lshw -C network
``` Each provide data for other devices than your wireless interface as well, so you'll have to do a little searching.

Here's an example of what you're looking for: ```
$ lshw -C network
*-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:68:a0:03:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.2 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

$ lspci -vv
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0428
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k
``` Lshw lists the driver as 'driver=X' and lspci simply says 'Kernel driver in use: X'.

Once you figure out what driver to install, installing it in Ubuntu should be pretty simple, but if you have no idea, there's 4 different options to try, so knowing would save quite a bit of hassle.

---

### Post by pedromagnus on 2009-04-30
Hi, I've got the exactly same problem in my HP dv6815nr with Atheros. I've already tried with 3 differents versions of madwifi without any success. This is my output for the 'lshw -C network' command (the block for ethernet is ommitted, it works ok).

*-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:55:59:e0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.9 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

Hoping from anyone blessed by the light of the lord linus to throw out some ray of light !!
Greetings from Argentina (sorry for my silly english :)).
Chau!

_EDIT_
I finally made it!! Just 20 minutes after I posted the message above, I was the happy receiver of the holy light :P
I have my Atheros working PERFECT (I hope it continues like this after I'll restart). This is what I did to make the Atheros work: (I'll mention the route in spanish, you just care about following the analogous in your language)

Sistema -> Administración -> Orígenes del Software. (enter root password when required). In the first tab (Ubuntu Software) check everything less 'Código Fuente' ('Source Code'). In the second tab 'Software de terceros' ('Third Party Software' or something like that) I have the following repositories (all checked):
- [http://ppa.launchpad.net/vicox/ppa/ubuntu](http://ppa.launchpad.net/vicox/ppa/ubuntu) jaunty main
- [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty non-free
- [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty non-free (Código fuente).
Finally, in the third tab I've checked 'jaunty-security' and 'jaunty-updates'.
That's it! When you update/upgrade it will appear about 40 new packages to update. One of them is the wireless thing that starts functioning right there without any restart.

Before all this I tried all the possible methods that you can find in this forum and others similar. Maybe that's the reasson why this solution works for me.

Good Luck!! I hope this could help anyone.
Greetings again.

---

### Post by coffeecat on 2009-04-30
> **pedromagnus said:**
> Hoping from anyone blessed by the light of the lord linus to throw out some ray of light !!

The only ray of light I can throw is that the Atheros AR242X wireless chipset works out of the box with Jaunty. I'm posting from my Asus EeePC 701 with Jaunty NBR. Jaunty NBR uses the same kernel and network manager as the ordinary Jaunty, by the way. I've done nothing with wireless except configure network manager with my WPA passkey. Here's the relevant bit of my lshw:

```
*-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:45:55:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.68 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
```Does that look familiar? All I can suggest is that you remove madwifi and see if you can get network manager working with the inbuilt kernel driver. According to my network manager, this is ath5k_pci.

To the OP - I don't know about the AR5007EG chipset.

---

### Post by t0mppa on 2009-04-30
Drivers are working ok and you're getting an IP address, thus there's a connection to the router as well. So what is the problem here? Can ping sites online, but can't access them on browser?

---

### Post by dummiebeginner on 2009-05-02
> **pedromagnus said:**
> 
_EDIT_
I finally made it!! Just 20 minutes after I posted the message above, I was the happy receiver of the holy light :P
I have my Atheros working PERFECT (I hope it continues like this after I'll restart). This is what I did to make the Atheros work: (I'll mention the route in spanish, you just care about following the analogous in your language)

Sistema -> Administración -> Orígenes del Software. (enter root password when required). In the first tab (Ubuntu Software) check everything less 'Código Fuente' ('Source Code'). In the second tab 'Software de terceros' ('Third Party Software' or something like that) I have the following repositories (all checked):
- [http://ppa.launchpad.net/vicox/ppa/ubuntu](http://ppa.launchpad.net/vicox/ppa/ubuntu) jaunty main
- [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty non-free
- [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty non-free (Código fuente).
Finally, in the third tab I've checked 'jaunty-security' and 'jaunty-updates'.
That's it! When you update/upgrade it will appear about 40 new packages to update. One of them is the wireless thing that starts functioning right there without any restart.

Before all this I tried all the possible methods that you can find in this forum and others similar. Maybe that's the reasson why this solution works for me.

Good Luck!! I hope this could help anyone.
Greetings again.

It didn't work for me either. However, I don't have that "http://ppa.launchpad.net/vicox/ppa/ubuntu" in the second tab "third party software" if that could be the problem. How could I get that?

--------------------

> **t0mppa said:**
> Well, you could simply just check which driver Mandriva 2009.0 & PCLinuxOS use to make it work and then install that one to Ubuntu as well.

To see what driver the interface is using, just open a terminal and run either of these two commands: ```
lspci -vv
lshw -C network
``` Each provide data for other devices than your wireless interface as well, so you'll have to do a little searching.


Thanks a lot t0mppa, but you mean that I must do that from Mandriva or PCLinuxOS or from my Ubuntu? Because then I would need to install them again. I meant if that can be checked from the Mandriva or PCLinuxOS CDs or even from within a Virtualbox run of them so I wouldn't need to install them again, a real mess.

---

### Post by dummiebeginner on 2009-05-02
SOLVED!!!

I managed to make it work finally.

I followed these instructions [http://nuclear-imaging.info/site_content/2009/01/30/atheros-5007eg-now-works-in-jaunty-jackalope/](http://nuclear-imaging.info/site_content/2009/01/30/atheros-5007eg-now-works-in-jaunty-jackalope/)

Then I went to activate the madwifi driver (System-Administration-Hardware Drivers) that I had installed before following these other instructions ([http://ubuntuforums.org/showpost.php?p=7129768&postcount=5](http://ubuntuforums.org/showpost.php?p=7129768&postcount=5)) (download driver here [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r4016-20090429.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r4016-20090429.tar.gz))

Then I clicked once over the connection icon in the system bar and a list of wifi connections showed up. I chose mine and edited it inserting my wifi WAP password.

It worked after deactivating the net (right click over netwrk icon) and activating it again. I pray for it to keep working after restarting.

Hope it helps someone because ths was a nightmare.

---

### Post by webchannel on 2010-06-23
> **t0mppa said:**
> Well, you could simply just check which driver Mandriva 2009.0 & PCLinuxOS use to make it work and then install that one to Ubuntu as well.

To see what driver the interface is using, just open a terminal and run either of these two commands: ```
lspci -vv
lshw -C network
``` Each provide data for other devices than your wireless interface as well, so you'll have to do a little searching.

Here's an example of what you're looking for: ```
$ lshw -C network
*-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:68:a0:03:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.2 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

$ lspci -vv
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device 0428
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k
``` Lshw lists the driver as 'driver=X' and lspci simply says 'Kernel driver in use: X'.

Once you figure out what driver to install, installing it in Ubuntu should be pretty simple, but if you have no idea, there's 4 different options to try, so knowing would save quite a bit of hassle.


webchannel@webchannel-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:ce:ca:16
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.254.117 latency=0 multicast=yes
       resources: irq:28 memory:f8000000-f8003fff ioport:3000(size=256) memory:f2000000-f201ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 04
       serial: 00:22:5f:07:ab:24
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa000000-fa00ffff
webchannel@webchannel-laptop:~$ 



my wireless is disabled
how to enable my wireless?

---

