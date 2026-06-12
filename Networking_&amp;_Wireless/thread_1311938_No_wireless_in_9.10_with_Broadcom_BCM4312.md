---
title: "No wireless in 9.10 with Broadcom BCM4312"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Gravy on 2009-11-02
Hey Guys,

I'm having some problems with 9.10 on my Dell Mini 9. I'm a bit of a new comer to linux so if it's something obvious I apologise. If you can help me out thanks in advance. :)

Basically I'm not getting wireless as an option in the little network drop down thing. (very technical description :p)

I've tried some of the suggestions in this thread:
[http://ubuntuforums.org/showthread.php?t=1309760](http://ubuntuforums.org/showthread.php?t=1309760)

Well the following commands from that thread:
>  sudo apt-get upgrade
sudo aptitude reinstall bcmwl-kernel-source
sudo apt-get install updateThe **Broadcom STA** driver now shows up in Hardware Drivers however has the following message at the bottom:
> The driver is activated but currently not in use[B]sudo lshw -c network:

[/B]> 
[B]*-network UNCLAIMED     
description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f0203fff

  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:fa:9a:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.9 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=no multicast=yes
[/B]I'm guessing that UNCLAIMED bit probably is causing the problem. However I know nothing.

EDIT: I also just thought it might be worth mentioning. I couldn't get ubuntu to boot when using the usb-creator.exe. I created an USB drive with unetbootin and install was successful.

Cheers
Dave G

---

### Post by pjomega on 2009-11-02
If you'll post the relevant Network Controller section from 

**sudo lspci -vvv**

we can look at the available and currently used drivers.

---

### Post by Gravy on 2009-11-02
Hey pjomega,

Thanks for helping out. 

Here is the relevant section:
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Broadcom Corporation Device 04b5
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=2 PME-
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [d0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 23-00-18-ff-ff-08-39-96
    Capabilities: [16c] Power Budgeting <?>
    Kernel modules: ssb, wl

```

---

### Post by pjomega on 2009-11-02
You just need to activate the wl kernel module (the STA driver). Did you reboot after installing? It shouldn't be necessary, but mine did not work properly until i did. Even if you haven't go ahead and try to load it manually:

[INDENT]**sudo modprobe wl**[/INDENT]

Running 

[INDENT]**lsmod|grep wl** [/INDENT]

should show wl and ssb loaded afterward. Then check to see if the network interface is up with 

[INDENT]**ifconfig**[/INDENT]

The wireless should be eth1 or eth2.

---

### Post by Gravy on 2009-11-02
Hey,

I've tried restarted a fair few times. :p

The modprobe command returns this:

> FATAL: Error inserting wl (/lib/modules/2.6.31-14-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Found this info on the message:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/449268](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/449268)

Tried:
sudo apt-get install bcmwl-kernel-source *- Was already newest version*

depmod -a *- no change*

dmesg error:
> [ 4230.435376] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 4230.435390] wl: Unknown symbol lib80211_get_crypto_ops
.

---

### Post by Gravy on 2009-11-03
Someone elsewhere suggested checking the wifi was actually enabled. 

Installed aircraft-manager and it does appear to be running. 

Still no progress with it been usable though. :(

Has also been suggested trying this patch:
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/252630](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/252630)

Will update with result once they're able to help as have no idea how to apply it. :p However have also been told that it should already be in 9.10.

Thought ubuntu was meant to be easy. :(

Update:
Have now also tried moving maximus-autostart.dektop from /etc/xdg/autostart to my home directory as suggested here:
[http://ubuntuforums.org/showthread.php?t=975498&page=2](http://ubuntuforums.org/showthread.php?t=975498&page=2)

Want to try adding wl to /etc/modules as suggested in that thread but don't have a clue how.
EDIT: Just realised this is what we were trying to do with modprobe. :(

---

### Post by Gravy on 2009-11-03
Tried the following from this thread [http://georgia.ubuntuforums.org/showpost.php?p=7506946&postcount=18:](http://georgia.ubuntuforums.org/showpost.php?p=7506946&postcount=18:)
Which was found via this bug report:[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630)

I've removed linux-backports-modules-2.6.31-1-generic as suggested in the bug report. I also deleted the lib80211.ko files as they were still causing the unknown symbol error. However now those files are gone I'm still getting an error saying that it's got an unknown symbol in that file. Even though it doesn't exsist any more.

I'm thinking about just installing .04. Is the wireless likely to work there?
Also should I maybe try ndiswrapper.

---

### Post by pjomega on 2009-11-03
haha. It should work NOW. BCM4312 works for me with bcmwl. Did you try the insmod instructions in bug 395630?

---

### Post by Gravy on 2009-11-03
> **pjomega said:**
> haha. It should work NOW. BCM4312 works for me with bcmwl. Do you have linux backports installed by any chance?

Still nothing. :( haha I'm running 9.04 off USB now and it's working great. Guess we may aswell try and get 9.10 going though. :p

How do I check if I have any backports installed?

---

### Post by pjomega on 2009-11-03
Run 

sudo dpkg -S lib80211.ko

This will list any packages containing the module in question. if you have backports, or anything other than the linux-image package which contains it, you'll see it listed.

---

### Post by Gravy on 2009-11-03
Returns:

```
linux-image-2.6.31-14-generic: /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko
linux-backports-modules-2.6.31-14-generic: /lib/modules/2.6.31-14-generic/updates/cw/lib80211.ko

```

---

### Post by pjomega on 2009-11-03
ok, so you still have linux backports installed. There shouldn't be anything you need in there, but if you lose any functionality when you remove just note it and you can add it back. 

**wl** was probably built against */lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko*, but depmod is compiling symbols from the "updated" */lib/modules/2.6.31-14-generic/updates/cw/lib80211.ko*.

Run **sudo apt-get remove linux-backports-modules-2.6.31-14-generic ** to remove the backports. The run **depmod -a**  and **modprobe wl** as root.

And keep fingers crossed :)

---

### Post by Gravy on 2009-11-03
Finger crossing wasn't enough. :(

It's somehow still finding an unknown symbol there.

```

david@david-netbook:~$ sudo apt-get remove linux-backports-modules-2.6.31-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-backports-modules-2.6.31-14-generic linux-backports-modules-karmic
  linux-backports-modules-karmic-generic
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
After this operation, 4,841kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113849 files and directories currently installed.)
Removing linux-backports-modules-karmic ...
Removing linux-backports-modules-karmic-generic ...
Removing linux-backports-modules-2.6.31-14-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
david@david-netbook:~$ sudo depmod -a
david@david-netbook:~$ sudo modprobe wl
FATAL: Error inserting wl (/lib/modules/2.6.31-14-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

---

### Post by pjomega on 2009-11-03
ok, run **modprobe wl** and then immediately **dmesg|tail**, which will give you the tail end of the system message log. What's it complaining about?

---

### Post by Gravy on 2009-11-03
Same error as earlier which there is this bug report for:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630)

```
[  335.063603] wl: Unknown symbol lib80211_get_crypto_ops
```

---

### Post by pjomega on 2009-11-03
rebooting should fix that. but you should be able to effect it without rebooting. look at that bug report comment #4. as root remove those modules, add them back, and then load wl:

rmmod  /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_wep.ko
rmmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_tkip.ko
rmmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_ccmp.ko
rmmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko

insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko
insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_ccmp.ko
insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_tkip.ko
insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_wep.ko
modprobe wl

---

### Post by Gravy on 2009-11-03
Returning:

```
ERROR: Module lib80211 does not exist in /proc/modules
```

Think I probably messed them up earlier. :s

---

### Post by pjomega on 2009-11-03
even after running **sudo insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko**?

---

### Post by Gravy on 2009-11-03
I ran that again and I could execute the .ko but none of the others.

```
david@david-netbook:~$ sudo insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko
david@david-netbook:~$ rmmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko
ERROR: Removing 'lib80211': Operation not permitted
david@david-netbook:~$ sudo rmmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko
david@david-netbook:~$ sudo rmmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_ccmp.ko
ERROR: Module lib80211_crypt_ccmp does not exist in /proc/modules
david@david-netbook:~$ sudo insmod /lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_ccmp.ko
insmod: can't read '/lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_ccmp.ko': No such file or directory

```

---

### Post by pjomega on 2009-11-03
hmmm...that's a problem. is that one of the ones you deleted?  does **ls /lib/modules/2.6.31-14-generic/kernel/net/wireless/** not show them?

---

### Post by Gravy on 2009-11-03
No it doesn't show them.
I believe they are the ones I deleted earlier. I thought I had moved them to somewhere rather than deleting. However I cannot find them now so I must of moved them somewhere that doesn't exist. 

Is there anyway of reinstalling them?

---

### Post by pjomega on 2009-11-03
first try a **locate ccmp**. see if you see where you stashed the modules. if not try marking *linux-image-2.6.31-14-generic* for reinstallation in synaptic. with most packages you can just purge and install, but i don't think you can purge the only linux image ;)

---

### Post by Gravy on 2009-11-03
Ok this is weird locate ccmp says they're in the directory. But, when I ls it they're not there.

```
david@david-netbook:~$ locate ccmp lib80211_crypt_wep.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_ccmp.ko
/lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211_crypt_wep.ko
/usr/share/doc/wpasupplicant/examples/wpa2-eap-ccmp.conf
/usr/src/linux-headers-2.6.31-14-generic/include/config/lib80211/crypt/ccmp.h

david@david-netbook:~$ ls /lib/modules/2.6.31-14-generic/kernel/net/wireless/
cfg80211.ko  lib80211.ko

```

---

### Post by pjomega on 2009-11-03
the locate db is outdated (it only updates periodically; just thought it might work) you can do a **sudo find / -iname 'lib80211_crypt_wep.ko'**, which will search everything, right now, but it takes longer.

---

### Post by Gravy on 2009-11-03
Great news. :D Once I put all the files back in place I ran the instructions below. Now is working great.


> **pjomega said:**
> You just need to activate the wl kernel module (the STA driver). Did you reboot after installing? It shouldn't be necessary, but mine did not work properly until i did. Even if you haven't go ahead and try to load it manually:
[INDENT]**sudo modprobe wl**[/INDENT]Running 
[INDENT]**lsmod|grep wl** [/INDENT]should show wl and ssb loaded afterward. Then check to see if the network interface is up with 
[INDENT]**ifconfig**[/INDENT]The wireless should be eth1 or eth2.

---

### Post by 007marek on 2009-11-12
Hi there

I also have problems with wireless after upgrading to 9.10. The sad part is that I got it to work only a week before I upgraded and now it is gone  :( .
The computer is a DELL VOSTRO 1520
Following the troubleshooting guide  [http://https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("http://https//help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
we have:
1. Device recognition - check
```
marek@marek-laptop:~$ sudo lshw -C network
[sudo] password for marek: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:ae:d8:bc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:32 ioport:4000(size=256) memory:fe004000-fe004fff(prefetchable) memory:fe000000-fe003fff(prefetchable) memory:fe020000-fe03ffff(prefetchable)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:50:b1:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f6000000-f6003fff
```2. Check for driver - check
```
marek@marek-laptop:~$ sudo lsmod |grep wl
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
```3. router connection - I think it is ok
```
marek@marek-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
```If I right click on the Network Connection applet in the Panel the "Enable Wireless" is grayed out. It becomes active (not grayed out) when I turn off the wireless card with the hardware switch. That is strange enough for me.

I installed wifi radar recently. When I try to connect with it it just sits there forever.
The hardware is ok because when I boot into windows everything works fine.

Any hints on how to proceed from here?

---

### Post by sakthidaran on 2009-11-29
I had similar problem when I migrated from 9.04 to 9.10. Fortunately, I had put 9.10 in a new partition. I configured 9.10 wireless connection with the same SSID and PWD of 9.04. Still, it did not work. Then, I checked System - Administration - Hardware Driver, it was Broadcom STA Wireless Driver in 9.04 where as there was no driver in 9.10. 

Next, I booted the system in 9.10 and connected in wired connection. It was working. I updated all the packages by running System - Administration - Update Manager. I rebooted the system in 9.10. Then, I ran System - Administration - Hardware Driver. The system now was showing two drivers. They were Broadcom B43 Wireless Driver and Broadcom STA Wireless Driver. B43 was found activated and STA was not. I selected STA and activated that driver. Then, once again, I rebooted the system. I ran System - Administration - Hardware Driver. The system now was showing only one driver that is Broadcom STA Wireless Driver. It was already activated so I closed. Then, I removed the wired connection and the system automatically connected through wireless.

In a nutshell, 9.10 (original CD) does not load the Broadcom STA Wireless Driver. B43 has some problem. Updating 9.10 helps to detect and load STA driver which needs to be activated manually. If we do this, the problem is solved.

Sakthidaran,
Lenova G450, Intel(R) Core(TM)2 Duo CPU, T6600 @ 2.20GHz, 2 GB RAM, 350GB HD, Broadcom BCM 4312 Controller, Ubuntu 9.10

---

### Post by mt1234 on 2009-11-29
I posted what's below in another thread about problems with connecting to wireless networks. I'm pretty new to Linux and the below is pretty basic, but I think that this may be what is causing some of the peoples problems. 

It appears that an Ubuntu 9.10 64-bit installation by default has the "Connect to wireless and ethernet networks" setting unchecked in the User Privileges for the Administrators group and Users group (possibly others). 

Go to System > Administration > Users and Groups. Click on Properties and then go to the User Privileges tab. Check the box next to "Connect to wireless and ethernet networks". Then click OK. 

Then go back to System > Administration > Hardware Drivers. Make sure the Broadcom STA wireless driver is activated. You may need to restart the computer after it is activated. Once restarted, make sure that any switch or button on your laptop or desktop for turning on the wireless radio is turned on. 

This worked for me! I hope this helps! :grin:

---

### Post by sakthidaran on 2009-12-07
I agree with mt1234. I also found this method to work with Ubuntu 9.10 32 bit version also.

---

