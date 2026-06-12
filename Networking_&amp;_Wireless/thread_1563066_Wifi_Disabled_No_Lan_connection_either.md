---
title: "Wifi Disabled/ No Lan connection either"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by Aamirsi on 2010-08-28
Well I have researched quiet a bit on the topic, and I will start with specifications:

Compaq Presario c500 laptop
2 Partitions:
Windows Vista 32-Bit
Ubuntu 10.04

Wifi Card type: BCM4311 802.11 b/g Wlan

The terminal says : Network "disabled" I assume this means the wifi card isnt being read? I have tried a number of terminal options that don't seem to do more then tell me the specs.


When I first installed Ubuntu I did not have it plugged into the router via Lan/ethernet. Could that have been a problem? If thats the case hwo can I fix it.

I was trying to find a copy of Ndiswrapper, but I don't understand how to unpack, or how to g0 about doing so Via terminal or the unpacker.

If there is another option please let me know.

Thanks I was thinking if I could get LAN working first it would be a good starting place for the Wifi Later. but if some has suggestions or another way to go about getting my Wifi/Lan wokring thanks a bunch!

---

### Post by ieee488 on 2010-08-28
If you plug in your Ethernet cable now, it should automatically be recognized. Most people don't have problems with that.

If you can get that working, it will be much easier to get your wireless working.

---

### Post by Aamirsi on 2010-08-28
I am attempting this in a bit thank you i will let you know how it goes thanks again!

---

### Post by pytheas22 on 2010-08-29
If you still can't get the ethernet working, could you please run the following commands and post the output:
```

lspci -nn
lsusb
lshw -C Network
uname -rm
dmesg | grep -e eth -e bcm -ie firmware
lsmod | grep -e wl -e b43
ls /lib/firmware
```

If you can't get any Internet connection on your Ubuntu machine, save the output to a text file (open a blank file from Applications>Accessories>Text Editor), then use a USB drive to transfer the file to a computer with Internet access so that you can copy and paste the output onto this website.

---

### Post by Aamirsi on 2010-08-29
as requested! 

unver@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
unver@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
unver@ubuntu:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:60400000-60403fff
unver@ubuntu:~$ Unam - rm
Unam: command not found
unver@ubuntu:~$ Unam -rm
Unam: command not found
unver@ubuntu:~$ Uham -rm
Uham: command not found
unver@ubuntu:~$ Uham - rm
Uham: command not found
unver@ubuntu:~$ dmesg | grep -e eth -e bcm -ie firmware
unver@ubuntu:~$ dmesg | grep -e eth -e bcm -ie firmware
unver@ubuntu:~$ lsmod / greb -e w/l -e b43
Usage: lsmod
unver@ubuntu:~$ ls /lib/firmware
2.6.32-21-generic         i2400m-fw-usb-1.3.sbcf  rt2561s.bin
3com                      i2400m-fw-usb-1.4.sbcf  rt2661.bin
acenic                    intelliport2.bin        rt2860.bin
adaptec                   ipw2100-1.3.fw          rt2870.bin
advansys                  ipw2100-1.3-i.fw        rt73.bin
agere_ap_fw.bin           ipw2100-1.3-p.fw        RTL8192SE
agere_sta_fw.bin          ipw2200-bss.fw          sb16
aic94xx-seq.fw            ipw2200-ibss.fw         scripts
ar9170-1.fw               ipw2200-sniffer.fw      slicoss
ar9170-2.fw               iwlwifi-1000-3.ucode    sun
ar9170.fw                 iwlwifi-3945-2.ucode    sxg
ath3k-1.fw                iwlwifi-4965-2.ucode    tehuti
atmel_at76c502_3com.bin   iwlwifi-5000-1.ucode    ti_3410.fw
atmel_at76c502.bin        iwlwifi-5000-2.ucode    ti_5052.fw
atmel_at76c502d.bin       iwlwifi-5150-2.ucode    tigon
atmel_at76c502e.bin       iwlwifi-6000-4.ucode    tr_smctr.bin
atmel_at76c504_2958.bin   kaweth                  ttusb-budget
atmel_at76c504a_2958.bin  keyspan                 usbdux
atmel_at76c504.bin        keyspan_pda             usbduxfast_firmware.bin
atmel_at76c506.bin        korg                    usbdux_firmware.bin
atmsar11.fw               libertas                v4l-cx231xx-avcore-01.fw
av7110                    matrox                  v4l-cx23418-apu.fw
bnx2                      mts_cdma.fw             v4l-cx23418-cpu.fw
bnx2x-e1-4.8.53.0.fw      mts_edge.fw             v4l-cx23418-dig.fw
bnx2x-e1-5.2.7.0.fw       mts_gsm.fw              v4l-cx2341x-dec.fw
bnx2x-e1h-4.8.53.0.fw     mwl8k                   v4l-cx2341x-enc.fw
bnx2x-e1h-5.2.7.0.fw      myricom                 v4l-cx2341x-init.mpg
cis                       NPE-B                   v4l-cx23885-avcore-01.fw
cpia2                     NPE-C                   v4l-cx23885-enc.fw
cxgb3                     ositech                 v4l-cx25840.fw
dabusb                    ql2100_fw.bin           v4l-pvrusb2-24xxx-01.fw
dsp56k                    ql2200_fw.bin           v4l-pvrusb2-29xxx-01.fw
dvb-fe-xc5000-1.6.114.fw  ql2300_fw.bin           vicam
dvb-usb-dib0700-1.20.fw   ql2322_fw.bin           whiteheat.fw
e100                      ql2400_fw.bin           whiteheat_loader.fw
ea                        ql2500_fw.bin           yam
edgeport                  qlogic                  yamaha
emi26                     r128                    zd1201-ap.fw
emi62                     radeon                  zd1201.fw
ess                       rt2561.bin              zd1211
unver@ubuntu:~$


hope it helps thanks soo much !

---

### Post by ieee488 on 2010-08-29
Ubuntu completely doesn't see your LAN. Did the LAN ever work in Windows?

You have Broadcom BCM4311 chipset. Search on that in this forum.

---

### Post by Aamirsi on 2010-08-29
yeah it works prfectly on windows, as i am using it right now on windows. hmm...

---

### Post by pytheas22 on 2010-08-30
Yes, the ethernet device doesn't appear to exist at all, according to Ubuntu.  That's very strange.  Are you positive it's not disabled in BIOS or something, or configured in some way that only Windows can see it?

As for the wireless, it should work using the Broadcom STA driver.  You can install the driver from your Ubuntu installation CD (assuming you have one--if not let me know and I'll tell you how to work around it).  Put your CD in the drive, then go to System>Administration>Software Sources.  Under the Ubuntu Software tab, enable the use of your CD as a repository.  Close the window, and agree to reload the sources list when prompted.  Then type:
```

sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```

and it will install the driver.  Reboot, and it should work.  If it still doesn't, please post the output of:
```

dmesg | grep -e wl -e b43
lshw -C Network
```

---

### Post by HankB on 2010-08-30
This is probably a dumb reply, but just in case...

I found this thread while trying to figure out why networking had stopped working on my Eee PC. I too faced the "Network Disabled" status from the task bar icon. While collecting information, I right clicked the network icon so I could click the "about" button to identify the version and application behind it. I found that there was also an "enable networking" button. When I clicked that, I had working networking in about 10 seconds. I have no idea how it got turned off, but I had allowed the battery to run down while the netbook was suspended and perhaps that had something to do with it.

HTH,
hank

---

### Post by Aamirsi on 2010-08-30
pytheas22 thank you agian, but i do not have the ubuntu installation disk. so i would need "you way of working around it". And ethernet dosent seem to work in windows either but works wifi fine. I don't care much for Ethernet capability rather have the wifi. I figured I need a Broadcom STA know of a location for my specific 1 and what kind? Would i need a windows vista or xp driver?

---

### Post by pytheas22 on 2010-08-30
The workaround is to download the installers for the Broadcom STA driver on a computer with Internet access, then transfer them to Ubuntu and install them there manually.  The installers you need are available at [http://packages.ubuntu.com/lucid/bcmwl-kernel-source](http://packages.ubuntu.com/lucid/bcmwl-kernel-source) and [http://packages.ubuntu.com/lucid/bcmwl-modaliases](http://packages.ubuntu.com/lucid/bcmwl-modaliases).  If you are using 32-bit Ubuntu, choose the "i386" package; if you're using 64-bit, choose "amd64" (if you don't know, the command "uname -m" will tell you; if it says x86_64, you're using 64-bit; otherwise it's a decent bet you're on 32-bit).

After you click the link for each package, you'll be presented with a list of mirrors hosting the file.  Click it to download.  Then transfer the two files on Ubuntu, and simply double-click on them to install.

I'm pretty sure this will work, but it may fail because the installers may complain about needing additional packages installed first as dependencies.  If you get any error messages, please let me know what they are and we can try to solve them.

It would also be helpful to see the output of:
```

uname -a
```

With that information, I could potentially compile the driver for you, as a backup in case the approach detailed above doesn't work.

Sorry this is so complicated, but once you get online it should all become much easier.

And if your ethernet isn't working in Windows either, you may want to check BIOS just to be sure it's not disabled there for some reason.  Even if you don't plan on using ethernet, it can always be nice to have as a backup to wireless.

---

### Post by Aamirsi on 2010-08-31
This is the error produced for the “i386”

Status:  Error: Wrong architecture 'i386'

Broadcom 802.11 Linux STA wireless driver source
These package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware. 


And this was the message I got when I ran the “amd64”

Status:   Error: Dependency is not satisfiable: dkms

Broadcom 802.11 Linux STA wireless driver source
These package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware. 

This below is the “uname -a” output

unver@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
unver@ubuntu:~$ 

thanks a ton pythean22, ur so helpful so far. Not worried about the ethernet just the wifi really I have worked without for years so not necessary maybe sometime in the future for now this is fine! Hope we can get this! Thanks a million!

---

### Post by pytheas22 on 2010-08-31
It looks like you have a 64-bit kernel, so use the amd64 packages.

Apparently the packages for the driver depend on the dkms package.  dkms in turn depends on make, gcc and module-init-tools. So in order to install all this, you should go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), search for each of those packages and download them.  Then transfer them to the Ubuntu computer and install them as you tried to do with the bcmwl-kernel-source and bcmwl-modaliases packages.

Install gcc first, then make, then dkms.  After that, try installing the bcmwl* packages again.  It should work this time.  But if you get any error messages, please of course post them here.

Sorry this is a bit complicated--it's hard to set this stuff up without having any kind of Internet connection available--but it should work this time!  If it still doesn't, I'll see about trying to compile the driver for you myself (but my kernel doesn't match yours so that might be a bit of work for me; I'm willing to do it if necessary, but let's try the approach above first).

---

### Post by Aamirsi on 2010-09-01
I have learned to navigate the link you provided, I am going to attempt to use the 3 items you asked for and see the outcome of the compilation. I will let you know as soon as I attempt it, thank you so much again Pytheas22.

---

### Post by Aamirsi on 2010-09-01
in your first post it stated that dkms needs gcc, make, and module-init-tools. but then further on you stated to install gcc, make and dkms? do i still need the module-init-tools.? And if that is the case what order would these 4 be put on the computer?

---

### Post by spawnywhippet on 2010-09-01
I have just upgraded my hard drive following a failure in my HP 69010p laptop. The system was running perfectly before, HW config is identical, and I'm using same Ubuntu 10.04 install disk. On the new installation, my WiFi card is disabled and the option to enable it in Network Manager is greyed out. The LED for the WiFi switch does not come on when I try to toggle the WiFi switch on the laptop. If I boot the same laptop with Windows, all hardware works, especially the wireless. Everything is enabled in BIOS and the hardware switches are on.

when I run 
sudo lshw -C network

I get the following output:

  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:67:7b:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:d8000000-d8001fff


How do I get this enabled?

UPDATE: I rebooted many times trying various things and now the WiFi card is not detected at all, lshw -C Network shows only a LAN card. In Windows the WiFi card is still there and working fine.

I also cannot run Update Manager, as it does not seem to work from behind a proxy. I configured the 'Preferences-Network Proxy-Apply System Wide' correctly, and the identical settings used for Firefox works fine.

---

### Post by pytheas22 on 2010-09-01
> in your first post it stated that dkms needs gcc, make, and module-init-tools. but then further on you stated to install gcc, make and dkms? do i still need the module-init-tools.? And if that is the case what order would these 4 be put on the computer?

Sorry, that was an oversight on my part.  You need module-init-tools as well as the three other packages.  I'm not positive of the order that they should be installed in, but I'd do gcc first, then make, then init-tools and finally dkms.

Or better yet, try installing all of them at once by using control+mouse-click to highlight multiple icons, then press enter.  I'm not positive but I think this will work, and it will automatically install them in the order needed.
[B]
spawnywhippet[/B]: that sounds strange.  You have an Intel 4965 chipset, which should always work out-of-the-box.  Does your "lspci" output mention the wireless card at all?  Does:
```

dmesg | grep -e 4965 -e wlan -e iwl
```

say anything useful?

Also, if there are settings in your BIOS related to your wireless card, try playing with them to see if they change things.

---

### Post by Aamirsi on 2010-09-01
pytheas22 all 4 of the installations have taken place, all though I don't know what to do now? I attempted to install bcmwl-kernel and it installed but nothing is working? Myt wifi light is still not running, and i tried to shutdown adn reboot.

---

### Post by spawnywhippet on 2010-09-02
> [B]
spawnywhippet[/B]: that sounds strange.  You have an Intel 4965 chipset, which should always work out-of-the-box.  Does your "lspci" output mention the wireless card at all?  Does:
```

dmesg | grep -e 4965 -e wlan -e iwl
```

say anything useful?

Also, if there are settings in your BIOS related to your wireless card, try playing with them to see if they change things.

I'm now pretty sure this is a toggle somewhere in Linux that needs activating. I'm 100% sure its not the hardware, BIOS, or switch setting - all of those are working fine in Windows and the Wireless switch is toggling the WWAN, Bluetooth fine, as you can see by the rfkill listings below:
```

andy@ubuntu-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1b:38:e6:9f:36
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.3-0 ip=10.50.43.121 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:d8500000-d851ffff memory:d8520000-d8520fff ioport:5000(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:67:7b:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d8000000-d8001fff
andy@ubuntu-laptop:~$ dmesg | grep -e 4965 -e wlan -e iwl
[    0.496501] pci 0000:00:1c.1:   MEM window: 0xd8000000-0xd80fffff
[    0.496505] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.496513] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:28
[    0.496517] pci 0000:00:1c.4:   IO window: 0x2000-0x3fff
[    0.496524] pci 0000:00:1c.4:   MEM window: 0xd4000000-0xd7ffffff
[    0.496529] pci 0000:00:1c.4:   PREFETCH window: 0x000000c8000000-0x000000c81fffff
[    0.496541] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.496544] pci 0000:02:06.0:   IO window: 0x006000-0x0060ff
[    0.496550] pci 0000:02:06.0:   IO window: 0x006400-0x0064ff
[    0.496555] pci 0000:02:06.0:   PREFETCH window: 0xc0000000-0xc3ffffff
[    0.496561] pci 0000:02:06.0:   MEM window: 0xcc000000-0xcfffffff
[    0.496567] pci 0000:02:06.1: CardBus bridge, secondary bus 0000:04
[    0.496570] pci 0000:02:06.1:   IO window: 0x006800-0x0068ff
[    0.496575] pci 0000:02:06.1:   IO window: 0x006c00-0x006cff
[    0.496581] pci 0000:02:06.1:   PREFETCH window: 0xc4000000-0xc7ffffff
[    0.496587] pci 0000:02:06.1:   MEM window: 0xdc000000-0xdfffffff
[    0.496594] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.496597] pci 0000:00:1e.0:   IO window: 0x6000-0x6fff
[    7.230199] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    7.230202] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    7.230308] iwlagn 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.230341] iwlagn 0000:10:00.0: setting latency timer to 64
[    7.230428] iwlagn 0000:10:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[    7.273586] iwlagn 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    7.273676] iwlagn 0000:10:00.0: irq 30 for MSI/MSI-X
[    9.031089] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.097388] iwlagn 0000:10:00.0: RF_KILL bit toggled to enable radio.
[   15.129982] iwlagn 0000:10:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   15.330558] iwlagn 0000:10:00.0: loaded firmware version 228.61.2.24
[   15.544767] Registered led device: iwl-phy0::radio
[   15.544786] Registered led device: iwl-phy0::assoc
[   15.544802] Registered led device: iwl-phy0::RX
[   15.544821] Registered led device: iwl-phy0::TX
[   15.589868] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.883148] iwlagn 0000:10:00.0: RF_KILL bit toggled to disable radio.
andy@ubuntu-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by ReplicateThis on 2010-09-02
Hi.  I'm a new Ubuntu devotee - this is my first post here so I apologize if it is going in the wrong spot.  I am having a similar problem with my desktop PC.  I have a Broadcom intergrated ethernet card on my Asus mobo, and my rig is set to dual boot XP and Ubuntu Lucid.  

Trouble is the network card will be working fine in XP, then on rebooting into Ubuntu it reads as disconnected.  My router shows no light on for that port - as if the ethernet cable has been disconnected.  If I boot back into Windows, the card still shows as if a cable disconnected.  I have to disable and uninstall the network card from the hardware manager, then reboot into XP again and it will reinstall itself and work then with no trouble. 

Here's the weird part though: if I leave the card working in XP and boot back into Ubuntu the card will not gain an IP (will have 0.0.0.0).  However if I uninstall the card from Windows XP first and then boot into Ubuntu the card will work fine, using the static IP I have the card set to use. (Card is set to use the same static IP in both operating systems).

Obviously I have my workaround in manually disabling the network card in Windows prior to booting to Ubuntu, so the problem is merely an annoyance, but what could be conflicting the card in this way?  Its as if Windows settings on the card are registered by the machine during the boot sequence, so when Ubuntu boots it's trying to assign the same IP address to the card again and subsequently not able to.

Any ideas on how I could fix this?

---

### Post by pytheas22 on 2010-09-02
**Aamirsi**: perhaps the driver is simply not being auto-activated as it should.  What output do you get from running these commands (in this order):
```

lsmod | grep wl
sudo modprobe wl
lshw -C Network
dmesg | grep -e wl -e eth1
lshw -C Network
iwconfig
ifconfig
```

Note that some commands may have not output.

If the driver was indeed correctly installed, this should help figure out why it's not working.

Thanks for all of your patience on this--hopefully we're close to having it finally working.
[B]
spawnywhippet[/B]: yes, it looks like the wireless is being disabled by a software switch within the Linux kernel.  Does it work if you type:
```

sudo rfkill unblock all
```

You may need still to toggle the physical kill switch after disabling the software switch.
[B]
ReplicateThis[/B]: I have an idea what might be causing your trouble, but it's probably not related to the other problems in this thread.  If you could please start a new thread, I'll help you there, so things don't get too confusing here.  In your new thread, please include the output of the commands:
```

dmesg | grep -e eth -e bcm -e rtl -e 8139 -e atl
lspci -nn
lshw -C Network
uname -rm
```

---

### Post by Aamirsi on 2010-09-02
unver@ubuntu:~$ lsmod | grep wl
unver@ubuntu:~$ sudo modprobe wl
[sudo] password for unver: 
FATAL: Module wl not found.
unver@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:60400000-60403fff
unver@ubuntu:~$ dmesg | grep -e wl -e ethl
unver@ubuntu:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:60400000-60403fff
unver@ubuntu:~$ iwconfig
lo        no wireless extensions.

unver@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3312 (3.3 KB)  TX bytes:3312 (3.3 KB)

unver@ubuntu:~$

this was the output of what u asked for pytheas22 and don't worry about it. I have to say thank you for you being so patient with me.!

---

### Post by pytheas22 on 2010-09-02
**Aamirsi**: it looks like the driver didn't get installed for some reason.  So, I compiled it myself in a way that you should be able to install.  To do that, first download the file [http://burnthesorbonne.com/files/STA_driver.tar.gz](http://burnthesorbonne.com/files/STA_driver.tar.gz) using a computer with Internet access, and transfer the file to your desktop on Ubuntu.  Then run these commands.  Please post all output:
```

cd ~/Desktop
tar -xzvf STA_driver.tar.gz 
cd STA
sudo make install
sudo rmmod b43
sudo rmmod ssb
sudo modprobe wl
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/wl.ko
dmesg | tail
lshw -C Network
```

If this works, you should at this point have your wireless card up.  Keep your fingers crossed...

---

### Post by Aamirsi on 2010-09-02
unver@ubuntu:~$ cd ~/Desktop
unver@ubuntu:~/Desktop$ tar -xzvf STA_driver.tar.gz
STA/
STA/.tmp_versions/
STA/src/
tar: STA/.tmp_versions: time stamp 2010-09-02 21:45:12 is 2260.220596396 s in the future
STA/lib/
STA/src/shared/
STA/src/include/
tar: STA/src/shared: time stamp 2010-09-02 21:45:10 is 2258.220388758 s in the future
STA/src/wl/
STA/src/include/proto/
STA/src/wl/sys/
STA/src/wl/phy/
tar: STA/src/wl/sys: time stamp 2010-09-02 21:45:12 is 2260.220301177 s in the future
STA/.wl.ko.cmd
tar: STA/.wl.ko.cmd: time stamp 2010-09-02 21:45:13 is 2261.220149272 s in the future
STA/.wl.mod.o.cmd
tar: STA/.wl.mod.o.cmd: time stamp 2010-09-02 21:45:13 is 2261.220002535 s in the future
STA/wl.ko
tar: STA/wl.ko: time stamp 2010-09-02 21:45:13 is 2261.158653182 s in the future
STA/wl.mod.o
tar: STA/wl.mod.o: time stamp 2010-09-02 21:45:12 is 2260.158397563 s in the future
STA/Module.symvers
tar: STA/Module.symvers: time stamp 2010-09-02 21:45:12 is 2260.158324928 s in the future
STA/wl.mod.c
tar: STA/wl.mod.c: time stamp 2010-09-02 21:45:12 is 2260.158229036 s in the future
STA/modules.order
tar: STA/modules.order: time stamp 2010-09-02 21:45:12 is 2260.15813901 s in the future
STA/.wl.o.cmd
tar: STA/.wl.o.cmd: time stamp 2010-09-02 21:45:12 is 2260.157317328 s in the future
STA/wl.o
tar: STA/wl.o: time stamp 2010-09-02 21:45:12 is 2260.104921626 s in the future
STA/.built-in.o.cmd
tar: STA/.built-in.o.cmd: time stamp 2010-09-02 21:45:07 is 2255.104684655 s in the future
STA/built-in.o
tar: STA/built-in.o: time stamp 2010-09-02 21:45:07 is 2255.104591207 s in the future
STA/README.txt
STA/hybrid-portsrc-x86_64-v5.60.48.36.tar.gz
STA/Makefile
STA/.tmp_versions/wl.mod
tar: STA/.tmp_versions/wl.mod: time stamp 2010-09-02 21:45:12 is 2260.089372233 s in the future
STA/lib/LICENSE.txt
STA/lib/wlc_hybrid.o_shipped
STA/src/shared/linux_osl.o
tar: STA/src/shared/linux_osl.o: time stamp 2010-09-02 21:45:10 is 2258.035763805 s in the future
STA/src/shared/.linux_osl.o.cmd
tar: STA/src/shared/.linux_osl.o.cmd: time stamp 2010-09-02 21:45:10 is 2258.035016501 s in the future
STA/src/shared/linux_osl.c
STA/src/include/epivers.h
STA/src/include/wlioctl.h
STA/src/include/typedefs.h
STA/src/include/pcicfg.h
STA/src/include/packed_section_start.h
STA/src/include/packed_section_end.h
STA/src/include/osl.h
STA/src/include/linuxver.h
STA/src/include/linux_osl.h
STA/src/include/bcmwifi.h
STA/src/include/bcmutils.h
STA/src/include/bcmendian.h
STA/src/include/bcmdefs.h
STA/src/include/proto/wpa.h
STA/src/include/proto/ethernet.h
STA/src/include/proto/bcmevent.h
STA/src/include/proto/bcmeth.h
STA/src/include/proto/802.1d.h
STA/src/include/proto/802.11.h
STA/src/wl/sys/wl_iw.o
tar: STA/src/wl/sys/wl_iw.o: time stamp 2010-09-02 21:45:12 is 2260.029776659 s in the future
STA/src/wl/sys/wl_linux.o
tar: STA/src/wl/sys/wl_linux.o: time stamp 2010-09-02 21:45:11 is 2259.029212621 s in the future
STA/src/wl/sys/.wl_iw.o.cmd
tar: STA/src/wl/sys/.wl_iw.o.cmd: time stamp 2010-09-02 21:45:12 is 2260.028674634 s in the future
STA/src/wl/sys/.wl_linux.o.cmd
tar: STA/src/wl/sys/.wl_linux.o.cmd: time stamp 2010-09-02 21:45:11 is 2259.028061847 s in the future
STA/src/wl/sys/wlc_pub.h
STA/src/wl/sys/wlc_key.h
STA/src/wl/sys/wl_linux.h
STA/src/wl/sys/wl_linux.c
STA/src/wl/sys/wl_iw.h
STA/src/wl/sys/wl_iw.c
STA/src/wl/sys/wl_export.h
STA/src/wl/sys/wl_dbg.h
STA/src/wl/phy/phy_version.h
tar: STA: time stamp 2010-09-02 21:45:13 is 2261.019473532 s in the future
unver@ubuntu:~/Desktop$ cd STA
unver@ubuntu:~/Desktop/STA$ sudo make install
install -D -m 755 wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/wl.ko
unver@ubuntu:~/Desktop/STA$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
unver@ubuntu:~/Desktop/STA$ sudo make ssb
make: *** No rule to make target `ssb'.  Stop.
unver@ubuntu:~/Desktop/STA$ sudo modprobe wl
FATAL: Module wl not found.
unver@ubuntu:~/Desktop/STA$ sudo insmod /lib/modules/'uname -r'/kernel/drivers/bet/wirless/wl.ko
insmod: can't read '/lib/modules/uname -r/kernel/drivers/bet/wirless/wl.ko': No such file or directory
unver@ubuntu:~/Desktop/STA$ dmesg | tail
[   52.200879] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           8.02 PQ: 0 ANSI: 0 CCS
[   52.203057] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   52.203855] sd 6:0:0:0: [sdb] 3907583 512-byte logical blocks: (2.00 GB/1.86 GiB)
[   52.204349] sd 6:0:0:0: [sdb] Write Protect is off
[   52.204353] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[   52.204356] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   52.208726] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   52.208735]  sdb: sdb1
[   52.213777] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   52.213785] sd 6:0:0:0: [sdb] Attached SCSI removable disk
unver@ubuntu:~/Desktop/STA$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:60400000-60403fff
unver@ubuntu:~/Desktop/STA$ cd ~/Desktop
unver@ubuntu:~/Desktop$ tar -xzvf STA_driver.tar.gz
STA/
STA/.tmp_versions/
STA/src/
tar: STA/.tmp_versions: time stamp 2010-09-02 21:45:12 is 2013.96063513 s in the future
STA/lib/
STA/src/shared/
STA/src/include/
tar: STA/src/shared: time stamp 2010-09-02 21:45:10 is 2011.960424 s in the future
STA/src/wl/
STA/src/include/proto/
STA/src/wl/sys/
STA/src/wl/phy/
tar: STA/src/wl/sys: time stamp 2010-09-02 21:45:12 is 2013.960334883 s in the future
STA/.wl.ko.cmd
tar: STA/.wl.ko.cmd: time stamp 2010-09-02 21:45:13 is 2014.960180115 s in the future
STA/.wl.mod.o.cmd
tar: STA/.wl.mod.o.cmd: time stamp 2010-09-02 21:45:13 is 2014.960033867 s in the future
STA/wl.ko
tar: STA/wl.ko: time stamp 2010-09-02 21:45:13 is 2014.899809527 s in the future
STA/wl.mod.o
tar: STA/wl.mod.o: time stamp 2010-09-02 21:45:12 is 2013.899555025 s in the future
STA/Module.symvers
tar: STA/Module.symvers: time stamp 2010-09-02 21:45:12 is 2013.899482809 s in the future
STA/wl.mod.c
tar: STA/wl.mod.c: time stamp 2010-09-02 21:45:12 is 2013.899386428 s in the future
STA/modules.order
tar: STA/modules.order: time stamp 2010-09-02 21:45:12 is 2013.899296054 s in the future
STA/.wl.o.cmd
tar: STA/.wl.o.cmd: time stamp 2010-09-02 21:45:12 is 2013.898464384 s in the future
STA/wl.o
tar: STA/wl.o: time stamp 2010-09-02 21:45:12 is 2013.846303012 s in the future
STA/.built-in.o.cmd
tar: STA/.built-in.o.cmd: time stamp 2010-09-02 21:45:07 is 2008.84606653 s in the future
STA/built-in.o
tar: STA/built-in.o: time stamp 2010-09-02 21:45:07 is 2008.845967634 s in the future
STA/README.txt
STA/hybrid-portsrc-x86_64-v5.60.48.36.tar.gz
STA/Makefile
STA/.tmp_versions/wl.mod
tar: STA/.tmp_versions/wl.mod: time stamp 2010-09-02 21:45:12 is 2013.825347693 s in the future
STA/lib/LICENSE.txt
STA/lib/wlc_hybrid.o_shipped
STA/src/shared/linux_osl.o
tar: STA/src/shared/linux_osl.o: time stamp 2010-09-02 21:45:10 is 2011.774279604 s in the future
STA/src/shared/.linux_osl.o.cmd
tar: STA/src/shared/.linux_osl.o.cmd: time stamp 2010-09-02 21:45:10 is 2011.77366989 s in the future
STA/src/shared/linux_osl.c
STA/src/include/epivers.h
STA/src/include/wlioctl.h
STA/src/include/typedefs.h
STA/src/include/pcicfg.h
STA/src/include/packed_section_start.h
STA/src/include/packed_section_end.h
STA/src/include/osl.h
STA/src/include/linuxver.h
STA/src/include/linux_osl.h
STA/src/include/bcmwifi.h
STA/src/include/bcmutils.h
STA/src/include/bcmendian.h
STA/src/include/bcmdefs.h
STA/src/include/proto/wpa.h
STA/src/include/proto/ethernet.h
STA/src/include/proto/bcmevent.h
STA/src/include/proto/bcmeth.h
STA/src/include/proto/802.1d.h
STA/src/include/proto/802.11.h
STA/src/wl/sys/wl_iw.o
tar: STA/src/wl/sys/wl_iw.o: time stamp 2010-09-02 21:45:12 is 2013.768406581 s in the future
STA/src/wl/sys/wl_linux.o
tar: STA/src/wl/sys/wl_linux.o: time stamp 2010-09-02 21:45:11 is 2012.767828505 s in the future
STA/src/wl/sys/.wl_iw.o.cmd
tar: STA/src/wl/sys/.wl_iw.o.cmd: time stamp 2010-09-02 21:45:12 is 2013.767282556 s in the future
STA/src/wl/sys/.wl_linux.o.cmd
tar: STA/src/wl/sys/.wl_linux.o.cmd: time stamp 2010-09-02 21:45:11 is 2012.766666346 s in the future
STA/src/wl/sys/wlc_pub.h
STA/src/wl/sys/wlc_key.h
STA/src/wl/sys/wl_linux.h
STA/src/wl/sys/wl_linux.c
STA/src/wl/sys/wl_iw.h
STA/src/wl/sys/wl_iw.c
STA/src/wl/sys/wl_export.h
STA/src/wl/sys/wl_dbg.h
STA/src/wl/phy/phy_version.h
tar: STA: time stamp 2010-09-02 21:45:13 is 2014.763800129 s in the future
unver@ubuntu:~/Desktop$ cd STA
unver@ubuntu:~/Desktop/STA$ sudo make install
install -D -m 755 wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/wl.ko
unver@ubuntu:~/Desktop/STA$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
unver@ubuntu:~/Desktop/STA$ sudo rmmod ssb
unver@ubuntu:~/Desktop/STA$ sudo modprobe wl
FATAL: Module wl not found.
unver@ubuntu:~/Desktop/STA$ sudo insmod /lib/modules/ 'uname -r'/kernel/drivers/net/wirless/wl.ko
insmod: can't read '/lib/modules/': Is a directory
unver@ubuntu:~/Desktop/STA$ dmesg | tail
[   52.203057] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   52.203855] sd 6:0:0:0: [sdb] 3907583 512-byte logical blocks: (2.00 GB/1.86 GiB)
[   52.204349] sd 6:0:0:0: [sdb] Write Protect is off
[   52.204353] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[   52.204356] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   52.208726] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   52.208735]  sdb: sdb1
[   52.213777] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   52.213785] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  542.378698] b43-pci-bridge 0000:06:00.0: PCI INT A disabled
unver@ubuntu:~/Desktop/STA$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:60400000-60403fff
unver@ubuntu:~/Desktop/STA$


this is after attempting 2 times, in the same terminal.

---

### Post by pytheas22 on 2010-09-03
It looks like you got the module in place correctly, but there were a couple of small errors that prevented it from activating (you typed "sudo make ssb" where it should have been "sudo rmmod ssb" and you entered a quote ' instead of a tick ` ...an easy mistake to make, but there's actually a big difference!).

Please reboot, then try this and post output:
```

sudo rmmod b43
sudo rmmod ssb
sudo rmmod wl
sudo insmod /lib/modules/2.6.32-21-generic/kernel/drivers/net/wirless/wl.ko
dmesg | tail
lshw -C Network
```

Hopefully this will do it!

---

### Post by Aamirsi on 2010-09-03
unver@ubuntu:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
unver@ubuntu:~$ sudo rmmod ssb
ERROR: Module ssb does not exist in /proc/modules
unver@ubuntu:~$ sudo rmmod wl
ERROR: Module wl does not exist in /proc/modules
unver@ubuntu:~$ sudo insmod /lib/modules/2.6.32-21-generic/kernel/drivers/net/wirless/wl.ko
insmod: can't read '/lib/modules/2.6.32-21-generic/kernel/drivers/net/wirless/wl.ko': No such file or directory
unver@ubuntu:~$ dmesg | tail
[   25.928134] type=1505 audit(1283554725.971:10):  operation="profile_load" pid=708 name="/usr/bin/evince-previewer"
[   25.939220] type=1505 audit(1283554725.981:11):  operation="profile_load" pid=708 name="/usr/bin/evince-thumbnailer"
[   26.245771] ppdev: user-space parallel port driver
[  112.769013] b43-pci-bridge 0000:06:00.0: PCI INT A disabled
[  160.762206] wl: module license 'unspecified' taints kernel.
[  160.762212] Disabling lock debugging due to kernel taint
[  160.763299] wl: Unknown symbol lib80211_get_crypto_ops
[  208.668963] wl: Unknown symbol lib80211_get_crypto_ops
[  398.608136] wl: Unknown symbol lib80211_get_crypto_ops
[  758.665456] wl: Unknown symbol lib80211_get_crypto_ops
unver@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:60400000-60403fff
unver@ubuntu:~$ 

this is the output, but when I get to the section with “sudo insmod” I post exactly how u had  told me and it tells me otherwise? Thanks Pytheas22 I can tell were close, just needs a bit more work.

---

### Post by pytheas22 on 2010-09-03
Yes, it's close but some annoying issues are still present.  What do you get from:

```
sudo -s
rmmod b43
rmmod ssb
rmmod wl
insmod /lib/modules/$(uname -r)/kernel/net/wireless/lib80211.ko
insmod /lib/modules/$(uname -r)/kernel/net/wireless/lib80211_crypt_ccmp.ko
insmod /lib/modules/$(uname -r)/kernel/net/wireless/lib80211_crypt_tkip.ko
insmod /lib/modules/$(uname -r)/kernel/net/wireless/lib80211_crypt_wep.ko
insmod /lib/modules/$(uname -r)/kernel/drivers/net/wirless/wl.ko
uname -r
locate wl.ko
dmesg | grep -e wl -e eth1
lshw -C Network
```

I know that's a lot to type but it will hopefully get to the root of this "Unknown symbol lib80211_get_crypto_ops" bit, which is why the driver is not loading properly.

An alternative approach to getting an Internet connection is to use the b43 driver.  This driver probably won't work well for you, but if you can at least use it to get online once, you can grab all the stuff you need to get online permanently.  To get b43 working, first download the file [http://burnthesorbonne.com/files/b43_firmware.tar.gz](http://burnthesorbonne.com/files/b43_firmware.tar.gz) and save it to your desktop on Ubuntu.  Then run:
```

cd ~/Desktop
tar -xzvf b43_firmware.tar.gz
sudo cp -r b43 /lib/firmware
sudo cp -r b43legacy /lib/firmware
sudo rmmod wl
sudo modprobe b43
sudo ifconfig wlan0 up
```

At this point, if you can see wireless networks, try connecting.  You may need to reboot a couple times (after reach reboot, run the last three commands above to ensure the b43 driver is activated) before you can get a connection.  If you manage to get online, run:
```

sudo apt-get update
sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```

and it will download and install a solid driver that should work permanently.

---

### Post by Aamirsi on 2010-09-03
thanks pytheas i will do this right now, so hopefully u will be on by the time i have th ouputs and outcome of the procedures thanks again! ill get back to u asap!

---

### Post by Aamirsi on 2010-09-03
Pytheas22 this is what I got from the first terminal you had told me to run, and asked for the outcome:
 

 unver@ubuntu:~$ sudo -s  
 [sudo] password for unver:  
 root@ubuntu:~# rmmod b43  
 ERROR: Module b43 does not exist in /proc/modules  
 root@ubuntu:~# rmmod ssb  
 root@ubuntu:~# rmmod wl  
 ERROR: Module wl does not exist in /proc/modules  
 root@ubuntu:~# insmod /lib/modules/$(uname -r)/kernel/net/wireless/lib80211.ko  
 root@ubuntu:~# insmod /lib/modules/$(uname  
 > -r)/kernel/net/wireless/lib80211_crypt_ccmp.ko  
 -r: command not found  
 insmod: can't read '/lib/modules/Linux/kernel/net/wireless/lib80211_crypt_ccmp.ko': No such file or directory  
 root@ubuntu:~# insmod /lib/modules/$(uname  
 > -r)/kernel/net/wireless/lib80211_crypt_tkip.ko  
 -r: command not found  
 insmod: can't read '/lib/modules/Linux/kernel/net/wireless/lib80211_crypt_tkip.ko': No such file or directory  
 root@ubuntu:~# insmod /lib/modules/$(uname  
 > -r)/kernel/net/wireless/lib80211_crypt_wep.ko  
 -r: command not found  
 insmod: can't read '/lib/modules/Linux/kernel/net/wireless/lib80211_crypt_wep.ko': No such file or directory  
 root@ubuntu:~# insmod /lib/modules/$(uname -r)/kernel/drivers/net/wirless/wl.ko  
 insmod: can't read '/lib/modules/2.6.32-21-generic/kernel/drivers/net/wirless/wl.ko': No such file or directory  
 root@ubuntu:~# uname -r  
 2.6.32-21-generic  
 root@ubuntu:~# locate wl.ko  
 root@ubuntu:~# dmesg | grep -e wl -e eth1  
 root@ubuntu:~# lshw -C Network  
   *-network UNCLAIMED      
        description: Network controller  
        product: BCM4311 802.11b/g WLAN  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:06:00.0  
        version: 01  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress cap_list  
        configuration: latency=0  
        resources: memory:60400000-60403fff  
 root@ubuntu:~#  
 

 

 below this what I have been given after following the steps for the one try wifi connnection. I got wifi capabilities, I will let you know if it worked, but this was the terminal outcome:
 

 unver@ubuntu:~$ sudo apt-get update  
 [sudo] password for unver:  
 Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US  
 Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [189B]  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US  
 Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg [189B]  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US  
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US  
 Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]  
 Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]  
 Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [38.5kB]  
 Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,193B]  
 Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,383kB]  
 Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,430kB]  
 Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [176kB]           
 Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,270B]  
 Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [293kB]         
 Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [109kB]     
 Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [3,652B]  
 Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages [14B]    
 Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages [67.3kB]       
 Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages [34.4kB]   
 Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages [1,876B]  
 Fetched 7,649kB in 14s (516kB/s)                                                
 Reading package lists... Done  
 unver@ubuntu:~$ sudo apt-get install bcmwl-kernel-source bcmwl-modaliases  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 bcmwl-kernel-source is already the newest version.  
 bcmwl-modaliases is already the newest version.  
 0 upgraded, 0 newly installed, 0 to remove and 266 not upgraded.  
 1 not fully installed or removed.  
 After this operation, 0B of additional disk space will be used.  
 Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...  
 Removing old bcmwl-5.60.48.36+bdcom DKMS files...  
 

 ------------------------------  
 Deleting module version: 5.60.48.36+bdcom  
 completely from the DKMS tree.  
 ------------------------------  
 Done.  
 Loading new bcmwl-5.60.48.36+bdcom DKMS files...  
 First Installation: checking all kernels...  
 Building only for 2.6.32-21-generic  
 Building for architecture x86_64  
 Building initial module for 2.6.32-21-generic  
 /usr/sbin/dkms: line 35: patch: command not found  
 

 Error! Application of patch 0001-MODULE_LICENSE.patch failed.  
 Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.  
 dpkg: error processing bcmwl-kernel-source (--configure):  
  subprocess installed post-installation script returned error exit status 6  
 Errors were encountered while processing:  
  bcmwl-kernel-source  
 E: Sub-process /usr/bin/dpkg returned an error code (1)  
 unver@ubuntu:~$ sudo apt-get install bcmwl-kernel-source bcmwl-modaliases  
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)  
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?  
 [EMAIL="unver@ubuntu"]unver@ubuntu[/EMAIL]:~$
 

 

 I also installed updates and what not with the wifi I got, I will reboot and see if the wifi works. Thanks, but I have not yet known if this works fully for wifi yet.

---

### Post by Aamirsi on 2010-09-03
wifi seems to be working perfectly!!!!!!!!!!!!!!!!!!!! thank you thank you thank you a million times pytheas!!!!!!!!!!!!!! =). I will reboot the computer a few times just to see if it is not "false hope"

---

### Post by pytheas22 on 2010-09-04
> wifi seems to be working perfectly!!!!!!!!!!!!!!!!!!!! thank you thank you thank you a million times pytheas!!!!!!!!!!!!!! =). I will reboot the computer a few times just to see if it is not "false hope"

Good to hear!  Thanks for all your patience as we struggled to get it going.

Out of curiosity, I'm wondering which driver is actually working with your card, because it doesn't appear that the STA driver ever got installed correctly.  Maybe the b43 driver actually works better with your hardware than I thought (the last I checked it only barely worked, but the developers may have improved it since then).  If you don't mind, what is the output of:
```

lshw -C Network
```

In any case, hopefully this will continue to "just work" and you'll be all set from now on, and know the procedure for getting wifi working in case you reinstall Ubuntu.

Hopefully you can also get the ethernet up using the instructions from earlier in this thread.  Let me know if not.

---

### Post by Aamirsi on 2010-09-04
unver@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:60400000-60403fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:37:36:eb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bg
unver@ubuntu:~$ 

thanks agian pytheas only thing is every time i seem to download a plugin or run a terminal for downloads on software such as itunes i get a crash report this kind:

bcmw kernel didnt seem to update/repair? ill see what happens if i have trouble getting itunes installed but for now iit all seems to work well.

---

### Post by Aamirsi on 2010-09-04
pytheas i was wondering I have saved all those things we talked about on a flash drive along with drivers we created and downloaded. is it safe to remove them from my Ubuntu desktop? Or should I keep the "one time" wifi on desktop and remove the rest?

---

### Post by pytheas22 on 2010-09-04
Thanks, it looks like you are using the b43 driver...if it's still working, so much the better!
> 
thanks agian pytheas only thing is every time i seem to download a plugin or run a terminal for downloads on software such as itunes i get a crash report this kind:

bcmw kernel didnt seem to update/repair? ill see what happens if i have trouble getting itunes installed but for now iit all seems to work well.

Try removing the bcmwl packages, since you don't need them, with:
```

sudo apt-get remove bcmwl-kernel-source bcmwl-modaliases
```

That should get rid of the complaints from the system about bcmwl stuff.
> 
pytheas i was wondering I have saved all those things we talked about on a flash drive along with drivers we created and downloaded. is it safe to remove them from my Ubuntu desktop? Or should I keep the "one time" wifi on desktop and remove the rest?

I meant to mention this.  You can delete all that stuff, since the files that matter have been copied into the system directories.

By the way, how are you trying to install iTunes?  You can't run it natively in Linux as Apple of course won't support Ubuntu.  I think it partially works in wine, but the last I checked, the most important features (like iPod syncing and the online store) won't work.

You can use Rhythmbox, which is already installed in Ubuntu, to connect to iPods.

---

### Post by Aamirsi on 2010-09-04
yes i was trying to use whine, i actually found a post on youtube explaining how to use a older version of itunes on the 10.04 os. it seemed to work flawlessly, but even so trying to install itunes newer version from 9-10. i had no ease. I wasnt able to execute the files. Whine wouldn't read them as .exe as they were tho? thanks agan!

Wifi seems to work perfectly still no problems.!

---

### Post by TheBrinos on 2010-09-04
> **HankB said:**
> This is probably a dumb reply, but just in case...

I found this thread while trying to figure out why networking had stopped working on my Eee PC. I too faced the "Network Disabled" status from the task bar icon. While collecting information, I right clicked the network icon so I could click the "about" button to identify the version and application behind it. I found that there was also an "enable networking" button. When I clicked that, I had working networking in about 10 seconds. I have no idea how it got turned off, but I had allowed the battery to run down while the netbook was suspended and perhaps that had something to do with it.

HTH,
hank

Thank you so much for this. I am completely new to Ubuntu - literally had it installed today and this was being a huge problem for me. Now I can connect to the internet. I was being told it was internal hardware problems, etc. or that I might have to run some advanced code, but this was the only simple fix I needed. Thanks again!

---

### Post by pytheas22 on 2010-09-05
> yes i was trying to use whine, i actually found a post on youtube explaining how to use a older version of itunes on the 10.04 os. it seemed to work flawlessly, but even so trying to install itunes newer version from 9-10. i had no ease. I wasnt able to execute the files. Whine wouldn't read them as .exe as they were tho? thanks agan!


Try right-clicking on the .exe file and selecting to open with wine.  By default Ubuntu does a pretentious thing and won't let you execute .exe files.

---

### Post by Aamirsi on 2010-09-06
for some reason pytheas22, i have tried almost ever version of itunes from 7.2-10 and even right clicking the file to 'open with wine" will not allow me to access the files to install. I have even tried to run terminals for them.

---

### Post by pytheas22 on 2010-09-06
> for some reason pytheas22, i have tried almost ever version of itunes from 7.2-10 and even right clicking the file to 'open with wine" will not allow me to access the files to install. I have even tried to run terminals for them. 

I'm not sure what's wrong there.  My only other suggestion would be to try running it from the command line; it may produce better output about what's wrong.  But wine is really not my specialty...

---

### Post by Aamirsi on 2010-09-06
its ok, ill figure that one out my self. the only other thing i ask of u, if u know how to do it. I have dual booting options, but I do want to remove my Vista from the computer completely, so I run Ubuntu 10.04 as a primary/ only OS on the Laptop. If you know how to do so, can you help me with that?

---

### Post by pytheas22 on 2010-09-06
> its ok, ill figure that one out my self. the only other thing i ask of u, if u know how to do it. I have dual booting options, but I do want to remove my Vista from the computer completely, so I run Ubuntu 10.04 as a primary/ only OS on the Laptop. If you know how to do so, can you help me with that?

Again, this isn't my area of expertise, but I think it would work to:

1. boot to the Ubuntu live CD/USB stick
2. in the live session, open the partition editor from the System>Administration menu
3. use the partition editor to delete your Windows partition(s).  You'll be able to identify these because they should be formatted as NTFS, while your Ubuntu partitions will mostl likely be formatted as ext3, ext4 and swap.
4. resize your Ubuntu partitions to occupy the space freed up by deleting Windows.  Note that you can generally only expand a partition to the "right," so depending on how your partitions are actually laid out, you might not be able to expand them into the freed space.  In that case, you can create a new partition instead that Ubuntu can use later.
5. you might need to edit your grub boot menu after deleting Vista so that grub knows which partition is your bootable one, if the partition order gets changed.  But I can help you deal with that if it's necessary--first, just try rebooting and see if it works.

Modifying partitions is inherently risky, so you should back up any important data first.

Before making these changes, please save the output of these commands somewhere, so you can reference it if there's a problem later:
```

sudo fdisk -l 
cat /boot/grub/grub.cfg
```

If there is a problem and you can't boot back into Ubuntu after changing the partition layout, please boot into the live CD (after the changes have been made) and post the output of:
```

sudo fdisk -l
```

With that information, I'll be able to help you sort out boot issues, if they arise after the change.

---

### Post by mihigeek on 2011-09-03
hi, 
    i installed ubuntu 11.04 few weeks ago , everything was working good but now from somedays it started connecting and disconnecting and now its totally disconnected plz help
:(

---

### Post by pytheas22 on 2011-09-03
**mihigeek**: I'll need more information to help you solve the problem.  The next time it disconnects please open a terminal, run the following commands and post the output here:
```

dmesg | tail -25
lsusb
lspci -nn
lshw -C Network
uname -a
sudo iwlist scan
iwconfig
```

---

