---
title: "No wireless connection"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by the downtown canon on 2010-03-31
Hi,

First time linux user

As with many posts i've read I installed 9.10 from dvd with ethernet plugged in but now i can't connect to the internet through the ethernet or wirelessly.

Do I need network manager? some people seem to suggest this...
the driver for the wireless was downloaded successfully i think - it now comes up in the network settings. I've put the Essid and all the rest into the properties which is under eth2 however in the network tools box the device is set to (lo). When i change it to eth2 and press configure it tells me the interface does not exist?

here is some perhaps useful infomation from the terminal;
```
thedowntowncanon@ubuntustudio-rob:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```
```
thedowntowncanon@ubuntustudio-rob:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0763:2012 Midiman 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b083 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
thedowntowncanon@ubuntustudio-rob:~$ sudo ifconfig
eth2      Link encap:Ethernet  HWaddr 00:21:00:b8:17:b5  
          inet addr:203.181.41.207  Bcast:203.181.41.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:feb8:17b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:16257
          TX packets:62 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:560 (560.0 B)  TX bytes:7050 (7.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```



there are so many treads on this topic i don't know which place to start - e.g. ndiswrapper, network manager!

any help much appreciated! THANKS;)

---

### Post by cchhrriiss121212 on 2010-03-31
Network manager is included on the studio image as a deb package. Here's the directory:
/media/cdrom0/pool/main/n/network-manager
and
/media/cdrom0/pool/main/n/network-manager-applet

Install all the packages in there (just click on them) and then you should have network manager.

As you have a broadcom card you need the STA driver for wireless:
[http://ubuntuforums.org/showthread.php?t=1229614](http://ubuntuforums.org/showthread.php?t=1229614)

---

### Post by the downtown canon on 2010-04-01
Hi Chris cheers for the response...

OK I couldn't get the network manager package till I plugged in the ethernet cable. It's weird it seems the system can connect when looking for stuff on the internet but it won't let me access the web myself. So the network manager appet sits in my desktop window but says wireless not configured. When I right click and try to configure I can tried to add my wireless network by writing in the SSID etc. but it won't connect. As for the driver in /hardware drivers it says STA driver installed and being used (this I did whe first installed the operating system...

On another thread about ndswrapper I got the following command which shows the driver being used as w10? is this the STA driver?

```
thedowntowncanon@ubuntustudio-rob:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:24:81:48:e8:9d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:d3100000-d3103fff ioport:3000(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth2
       version: 01
       serial: 00:21:00:b8:17:b5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=wl0 driverversion=5.10.91.9** ip=203.181.41.207 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d2000000-d2003fff

```Is this the right driver and if not how do I change it?

Many thanks...

---

### Post by cchhrriiss121212 on 2010-04-01
You should not have to resort to ndiswrapper just yet. The out put shows you have networking disabled which you can enable with a network manager right click.

The thread I posted says that the jockey (thats system>hardware drivers) does not always work very well with this card. You need to install the bcmwl packages as well.
Or just try the fix in post #5.

---

### Post by the downtown canon on 2010-04-01
OK - THE bcmwl from this page [http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/](http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/)
I just took the kernal and modalises ones as i thought that was the advice - on istalling it told me "a later version is already installed" - great. So I tried the fix on post 5, this is the readout;

```
thedowntowncanon@ubuntustudio-rob:~$ modprobe -l|grep wl
kernel/drivers/gpio/twl4030-gpio.ko
kernel/drivers/net/wireless/wl3501_cs.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/wl12xx/wl12xx.ko
kernel/drivers/usb/otg/twl4030-usb.ko
kernel/drivers/input/misc/twl4030-pwrbutton.ko
kernel/drivers/rtc/rtc-twl4030.ko
kernel/drivers/watchdog/twl4030_wdt.ko
kernel/drivers/staging/wlan-ng/prism2_usb.ko
kernel/drivers/uwb/wlp/wlp.ko
kernel/drivers/uwb/i1480/i1480u-wlp/i1480u-wlp.ko
kernel/sound/soc/codecs/snd-soc-twl4030.ko
kernel/net/netfilter/ipvs/ip_vs_wlc.ko
updates/dkms/wl.ko

```
 - is there my driver listed there, I can't tell? what is "the wl module" he's referring to?
cheers...

---

### Post by the downtown canon on 2010-04-01
SOLVED ! ! !

Don't quite know how - i basically undid what I had tried to set up (ie inputting network details in wireless tab of internet connections, and checking roaming instead) then following this post [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699) reinstalled the driver restarted and hey presto under the network manager tab my router was listed then typed in my password and away we go :p
even though the driver was listed as present and active in the Hardware drivers bit reinstalling it worked
cheers for your help!

---

### Post by paulq11 on 2010-05-06
I had the 'no wireless' problem after first installing Ubuntu Studio 9.10. 
The wlan0 device was there, and ifconfig showed things in place properly. 
But - I could not associate with the router. 
What worked for me was

[FONT=Courier New]sudo ifconfig wlan0 txpower auto[/FONT]

---

