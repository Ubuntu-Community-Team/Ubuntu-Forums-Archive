---
title: "Wireless Problems: Acer Aspire One running Karmic"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by johnerskine2010 on 2010-02-09
Acer Aspire One, running Kubuntu 9.10 Netbook Remix 

Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

My Acer Aspire has worked very happily with a number of home wireless networks as well as public Wi-Fi in a number of the usual places like Starbucks, and on the East Coast main line. I recently got a Vodafone 3g dongle, and as part of the process of trying to make it work, I seem to have stopped my system's ability to connect to wireless networks. I'm running 9.10, which doesn't recognise Vodafone dongles out of the box, so I installed some packages from the Betavine respositories to try to make the dongle work. These included 

ozerocdoff_0.4-2_i386.deb
usb-modeswitch_0.9.7_i386.deb
vodafone-mobile-connect_2.10.01-1_all.deb

I also installed an extra Kde package, Kwlan, in an attempt to try to detect the dongle. Unfortunately this seemed to have adverse effects on my system. First to disappear was the network icon on the top bar, then the KnetworkManager icon disappeared, and I lost the ability to connect to my wireless network.  

I'm paying the penalty for working too quickly, and in an unplanned way, and I would welcome suggestions on what I should do to get a wireless network connection again; once I've done that I'll try to make the Vodafone connection work. 

What I know is 

1. The network light at the bottom right of the keyboard is on
2. When I change the boot order, and run a live Ubuntu 9.04 USB stick, the machine detects wireless networks, and the little turning icon on the top bar appears
3. Everything else on my default Kubuntu 9.10 installation works, apart from the wireless networking, and I can access the internet using a network cable to my router. 

Help gratefully received!

---

### Post by northd_tech on 2010-02-10
Hi John.

I remember the Gnome Network Manager not getting along with WiCD (and me needing to manually re-install Gnome Network Manager after removing WiCD).  Of course, it sounds like you are using a KDE environment, not Gnome- so this may not be applicable.

According to this page, you can run Wicd in lieu of KWifiManager:

[http://www.linuxplanet.com/linuxplanet/tutorials/6527/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6527/1/)

You can obtain wicd (or read up on it) here:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

I haven't run KDE in ages and don't recall what the package manager is called (it's Synaptic Package Manager under Gnome though), but you might be able to just re-install KWifiManager using the KDE software package manager.  I think I'll reboot using KDE and see what my wireless network uses if I can get it linked up.  I'll advise if I find anything helpful.

Good luck.

Edit:  I couldn't get my wireless to work under KDE either just now (but it works flawlessly under Gnome 2.26.1- both 64-bit Ubuntu 9.04)- hmmm...  The KDE "package manager" said "Software & Programs" or something similar- it is not very much like the one under Gnome.  I can't post from KDE unfortunately.

---

### Post by northd_tech on 2010-02-10
Well, for whatever reason, my Broadcom wireless now decided to just work as "eth1" the 2nd time I logged in to KDE.

It looks like the package manager is named "kpackagekit" (it will open if you type this name in a terminal), or else go to System Settings > Add and Remove Software to get to the package manager in KDE (version 4, I believe).

I found the wireless settings under System Settings > Network Settings > Network Management > Wireless (or by right-clicking the Wireless icon that looks like an antenna and choosing Network Management Settings (or Manage Connections).

It looks like one of the KDE network managers is named "knetworkmanager" and you could download it (using a cabled ethernet connection) by running this command from a terminal:

```
sudo apt-get install network-manager-kde 
```

There appear to be 2 network managers for KDE from what I'm seeing.  You might want to try wicd though- several people have said they prefer it.

Hopefully someone with more experience with KDE than I have will chime in soon.

---

### Post by bkratz on 2010-02-10
> **northd_tech said:**
> Well, for whatever reason, my Broadcom wireless now decided to just work as "eth1" the 2nd time I logged in to KDE.

It looks like the package manager is named "kpackagekit" (it will open if you type this name in a terminal), or else go to System Settings > Add and Remove Software to get to the package manager in KDE (version 4, I believe).

I found the wireless settings under System Settings > Network Settings > Network Management > Wireless (or by right-clicking the Wireless icon that looks like an antenna and choosing Network Management Settings (or Manage Connections).

It looks like one of the KDE network managers is named "knetworkmanager" and you could download it (using a cabled ethernet connection) by running this command from a terminal:

```
sudo apt-get install network-manager-kde 
```

There appear to be 2 network managers for KDE from what I'm seeing.  You might want to try wicd though- several people have said they prefer it.

Hopefully someone with more experience with KDE than I have will chime in soon.

The network manager name has changed in kubuntu, please see this thread

[http://ubuntuforums.org/showpost.php?p=8784160&postcount=6](http://ubuntuforums.org/showpost.php?p=8784160&postcount=6)

---

### Post by johnerskine2010 on 2010-02-12
I've installed the network manager, now called 

"plasma-widget-networkmanagement" 

with the script 

<sudo apt-get install plasma-widget-networkmanagement> 

I've also run

<sudo apt-get install linux-backports-modules-karmic>

and   

<sudo apt-get install linux-backports-modules-wirelsss-karmic-generic>

but I'm still not able to access my wireless network.

---

### Post by johnerskine2010 on 2010-02-13
Just run another few things

<lshw -c network>

the output is 

WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:c0:8b:75
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:3000(size=256) memory:31010000-31010fff(prefetchable) memory:31000000-3100ffff(prefetchable) memory:31020000-3103ffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:35200000-3520ffff

then ran

<lspci>

the output was

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)  

and finally

<iwconfig>

the output is 

lo        no wireless extensions.

eth0      no wireless extensions.

this leads me to believe that although the cards are in place, the drivers aren't working.

Is this correct?

In addition, although I've moved the wireless switch to 'on' the light isn't on.

---

### Post by johnerskine2010 on 2010-02-13
I've also tried installing the madwifi modules, as suggested here

[http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/](http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/)

Still no wireless; and no wireless light either

---

### Post by johnerskine2010 on 2010-02-13
I've also tried what's suggested here to download new wireless drivers

[http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)

Download and unpacking goes OK, until I run

*sudo ./scripts/driver-select <ath5k>*

and I get 

*bash: syntax error near unexpected token 'newline'*

---

### Post by johnerskine2010 on 2010-02-23
I'm not sure why this has happened, but I am now able to access wireless networks again, using KNetworkManager.

I'll keep a watch to see if it goes flakey again, but I think I'm going to wait for Lucid to get my wider connection issues sorted once and for all.

---

### Post by ken78724 on 2010-02-25
am unsure the guidance applies. I stopped at step 6 when I saw "WARNING,,," 

How do U go to super user? am stopped at step 6 of post8870235    am using an Acer Aspire 5517 & not sure how to be a super user

---

### Post by ken78724 on 2010-02-25
forgot to indicate on this new Acer 5517 Laptop, I deleted WIN 7 OS & installed 9.10Karmic w/o yet building Ubu Studio, but will be. first need wireless to work away from home.:popcorn:

---

