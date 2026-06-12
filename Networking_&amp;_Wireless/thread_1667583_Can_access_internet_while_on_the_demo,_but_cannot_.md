---
title: "Can access internet while on the demo, but cannot after full install."
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by DHart07 on 2011-01-15
I am a computer science major and am in my 2nd year and all of the remaining programming courses I have are required to run in Linux.  Doing some research, most sites referred Ubuntu as the most user friendly Linux distribution.  Anyways...

I downloaded the Ubuntu 10.10 livecd and partioned my harddrive and installed it.  When the install was done I went to go add a few programs through the terminal, but realized there was no internet access.  I remembered accessing my home network on the demo and even used Firefox briefly but once the install was done and I rebooted I couldn't access the internet for the life of me.  I can't access the internet no matter what type of connection I try to connect over.  It doesn't matter if it is wired, over a secure connection or a connection with no security.  I was looking stuff up and found that this is a fairly common problem, but can't really find any decent answers.  I tried downloading wicd but without internet access trying to add things through the terminal doesn't really help.

I tried again with a fresh install, this time with the 32 bit version instead of the 64 bit version, but had the same results.  Throughout the demo I have internet access and can download the packages while I install, but once again once I reboot after the full install I can see all of the various networks but cannot access any or my own no matter how I configure it.

Any tips?  Thanks in advance.

---

### Post by ashishlukka on 2011-01-15
Same Problem with me..:(

first of all i couldnt install the "desktop version" in sony laptop with windows 7, i tried with Netbook and that was successful but then "ubuntu software center" is not able to access internet although i can surf internet through firefox.. so i cant install any new applications...

pls help..

---

### Post by amsterdamharu on 2011-01-15
Could you post the output of the following commands?

```
sudo ifconfig -a
sudo lspci -k
sudo lsusb

```

To execute the commands you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in &#91;code] &#91;/code] tags. In other words: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by spiky001 on 2011-01-15
If you use the CD to update by adding it to the update manager this might work. Go to System/Administration/Update manager click settings at bottom select Ubuntu software tab tick cd tab down the bottom. It should ask you to Reload make sure CD is in drive, then when it updates it should look on the cd as well, Also check for hardware drivers once you have updated from cd

---

### Post by ashishlukka on 2011-01-15
> **amsterdamharu said:**
> Could you post the output of the following commands?

```
sudo ifconfig -a
sudo lspci -k
sudo lsusb

```To execute the commands you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in ```
 
``` tags. In other words: ```
[COLOR=Red]Your pasted stuff[/COLOR]
```

**[COLOR=DarkSlateBlue]Hi , pls see the outputs of the cmds as below:::[/COLOR]**

root@ashish-VPCEA3BGN:~# sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 54:42:49:6b:05:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2256 (2.2 KB)  TX bytes:2256 (2.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:6e:3e:22  
          inet addr:10.41.251.108  Bcast:10.41.251.255  Mask:255.255.254.0
          inet6 addr: fe80::226:c7ff:fe6e:3e22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11733 (11.7 KB)  TX bytes:11636 (11.6 KB)

root@ashish-VPCEA3BGN:~# 





root@ashish-VPCEA3BGN:~# sudo lspci -k
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Sony Corporation Device 9071
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: intel ips
    Kernel modules: intel_ips
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
03:00.1 System peripheral: Ricoh Co Ltd Device e230
    Subsystem: Sony Corporation Device 9071
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8059 PCI-E Gigabit Ethernet Controller (rev 11)
    Subsystem: Sony Corporation Device 9071
    Kernel driver in use: sky2
    Kernel modules: sky2
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Sony Corporation Device 9071
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Sony Corporation Device 9071
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Sony Corporation Device 9071
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Sony Corporation Device 9071
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Sony Corporation Device 9071
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Sony Corporation Device 9071
root@ashish-VPCEA3BGN:~# 



root@ashish-VPCEA3BGN:~# sudo lsusb
Bus 002 Device 003: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 004: ID 064e:a213 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ashish-VPCEA3BGN:~#

---

### Post by grahammechanical on 2011-01-15
ashishlukka

You do not have the same problem as DHart07. You say:

> "ubuntu software center" is not able to access internet although i can  surf internet through firefox.. so i cant install any new  applications...

So, you have a network connection to your modem/router and you have Internet access. If you look through the listing from ifconfig -a you will see that wlan0 is UP and it is RUNNING and that it has an inet addr:

You have different problem. Please do not take over some else's question. It is confusing when more than one person is responding to advice.

Regards.

---

### Post by DHart07 on 2011-01-15
double post, sorry.

---

### Post by DHart07 on 2011-01-15
```

dave@dave-Satellite-A505:~$ sudo ifconfig -a
[sudo] password for dave: 
eth0      Link encap:Ethernet  HWaddr 00:26:6c:41:a0:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:d3:e4:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:fa778000-fa778100 

dave@dave-Satellite-A505:~$ sudo lspci -k
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff16
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Toshiba America Info Systems Device ff1e
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel driver in use: intel ips
	Kernel modules: intel_ips
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
	Kernel driver in use: rtl819xSE
	Kernel modules: r8192se_pci
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
	Subsystem: Toshiba America Info Systems Device ff1e
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
03:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
	Subsystem: Toshiba America Info Systems Device ff1e
03:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
	Subsystem: Toshiba America Info Systems Device ff1e
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Toshiba America Info Systems Device ff1e
dave@dave-Satellite-A505:~$ sudo lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dave@dave-Satellite-A505:~$ 

```

I also tried updating directly from the disk but apparently it doesn't like the "desktop" disk I used to install.  It wants me to insert the Maverick Meerkat release i386 disk and doesn't take the install disk.

---

### Post by amsterdamharu on 2011-01-15
Strange, they are both UP but have no IP address. Could you check the network settings?

There should be a network icon in your panel (right side where the menus are). Right click and check the settings there.

Do you have to set up DSL or just get an IP address directly (DHCP)?

---

### Post by DHart07 on 2011-01-16
Everything seems to function as normal, I just can't connect to anything.  As stated earlier, while I was running from the CD BEFORE the full install it worked as intended.  But once I installed and rebooted I can't connect to anything.  My router runs from my cable internet connection and is secured over WEP security, but even when I disabled the security I couldn't connect.  The strangest part was when I connected it via ethernet and got the same results.  

I can edit the connections and look at the settings and whatnot, that all works like normal.  The internet connection I have doesn't require me to set anything up, and if I manually enter everything in through the networking tool and try to mimic the connection that way I get the same results as trying to connect to it through the list.

I don't know how much it matters but I'm running a dual boot and am running the Ubuntu off of a partition I created from within the Ubuntu installer.  I can't download any other networking tools, because I have no way of accessing a connection once I boot into Ubuntu.

---

### Post by Butsy on 2011-01-16
Are you wired by ethernet and have the install updates checked  while installing Ubuntu 10.10? I had the same problem. Worked great the last time I installed.

---

### Post by DHart07 on 2011-01-16
Just tried another install this time using a wired connection and installing the updates during the install and no luck.  Same things as before - can detect connections, but can't connect and still no luck connecting through my wired connection.

---

### Post by amsterdamharu on 2011-01-16
Well, looks like the router is refusing to give any card an IP address. You can see if the wireless is switched off (software or hardware) with the following command:
```
rfkill list
```

---

### Post by DHart07 on 2011-01-16
I get 0 results from rfkill list.  Wireless connections are listed, but I cannot actually connect to any of them.  I insert the WEP key and 2 minutes or so later it just asks again after it times out.  I never get to connect.

---

### Post by amsterdamharu on 2011-01-16
That's a first, rfkill doesn't have any output but you have an active wireless card with driver loaded:
```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci

```

Let's try something like this:

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
tail tail /var/log/daemon.log
tail /var/log/faillog
```

Or for wired connection:

```
sudo ifconfig eth0 down
 sudo ifconfig eth0 up
tail tail /var/log/daemon.log
tail /var/log/faillog
```

---

### Post by DHart07 on 2011-01-16
```


dave@dave-Satellite-A505:~$ sudo ifconfig wlan0 down
dave@dave-Satellite-A505:~$ sudo ifconfig wlan0 up
dave@dave-Satellite-A505:~$ tail tail /var/log/daemon.log
tail: cannot open `tail' for reading: No such file or directory
==> /var/log/daemon.log <==
Jan 16 14:13:08 dave-Satellite-A505 NetworkManager[1102]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan 16 14:13:16 dave-Satellite-A505 NetworkManager[1102]: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Jan 16 14:13:16 dave-Satellite-A505 NetworkManager[1102]: <warn> Activation (wlan0) failed for access point (aww yeah ninjas)
Jan 16 14:13:16 dave-Satellite-A505 NetworkManager[1102]: <info> Marking connection 'Auto aww yeah ninjas' invalid.
Jan 16 14:13:16 dave-Satellite-A505 NetworkManager[1102]: <warn> Activation (wlan0) failed.
Jan 16 14:13:16 dave-Satellite-A505 NetworkManager[1102]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jan 16 14:13:16 dave-Satellite-A505 NetworkManager[1102]: <info> (wlan0): deactivating device (reason: 0).
Jan 16 14:13:48 dave-Satellite-A505 avahi-daemon[957]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jan 16 14:13:48 dave-Satellite-A505 avahi-daemon[957]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::721a:4ff:fed3:e454.
Jan 16 14:13:48 dave-Satellite-A505 avahi-daemon[957]: Withdrawing address record for fe80::721a:4ff:fed3:e454 on wlan0.
dave@dave-Satellite-A505:~$ tail /var/log/faillog
dave@dave-Satellite-A505:~$ 

```



Another thing I noticed is that my laptops fan never runs.  I saw other posts saying that things like the heat sensors in some systems are not recognized.  I tried openSUSE but the install disk never detected my disk drive.  What all are my options here?  I used Ubuntu in class, so I was hoping to just install and use that but I'm kind of stuck since I am having so many network problems and can't even download g++ which is the main reason I am trying to install the system.

---

### Post by amsterdamharu on 2011-01-16
```
Activation (wlan0) failed for access point (aww yeah ninjas)
```
I think you put some garbage in your network settings that won't connect, maybe filled out some wrong things during setup.

Could you right click the network icon in your panel and choose "edit connections"
Then in wired tab remove whatever is there (click on it and press delete). Then in wireless click on whatever is there and delete.
Now reboot the computer, when you get your desktop you should be able to click on the network icon (left button) and see available wireless networks.

You only posted results of the wireless connection and not the wired, does wired connection work and if not why didn't you post the output when switching it on and off?

---

### Post by DHart07 on 2011-01-16
```

dave@dave-Satellite-A505 ~ $ sudo ifconfig eth0 down
dave@dave-Satellite-A505 ~ $ sudo ifconfig eth0 up
dave@dave-Satellite-A505 ~ $ tail tail /var/log/daemon.log
tail: cannot open `tail' for reading: No such file or directory
==> /var/log/daemon.log <==
Jan 16 21:39:02 dave-Satellite-A505 avahi-daemon[952]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::226:6cff:fe41:a048.
Jan 16 21:39:02 dave-Satellite-A505 avahi-daemon[952]: Withdrawing address record for fe80::226:6cff:fe41:a048 on eth0.
Jan 16 21:39:02 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): carrier now OFF (device state 3)
Jan 16 21:39:02 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): device state change: 3 -> 2 (reason 40)
Jan 16 21:39:02 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): deactivating device (reason: 40).
Jan 16 21:39:07 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): carrier now ON (device state 2)
Jan 16 21:39:07 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jan 16 21:39:08 dave-Satellite-A505 avahi-daemon[952]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::226:6cff:fe41:a048.
Jan 16 21:39:08 dave-Satellite-A505 avahi-daemon[952]: New relevant interface eth0.IPv6 for mDNS.
Jan 16 21:39:08 dave-Satellite-A505 avahi-daemon[952]: Registering new address record for fe80::226:6cff:fe41:a048 on eth0.*.
dave@dave-Satellite-A505 ~ $ tail /var/log/faillog
dave@dave-Satellite-A505 ~ $ 

```

After deleting all of the connections in edit connections and restarting I have the same results.  I am still unable to connect through my wired connection.  And the "aww yeah ninjas" was what my buddy renamed my connection at the time, sorry about that.

---

### Post by amsterdamharu on 2011-01-16
Could you try this command:

```
sudo dhclient
```

I wonder what the output will be, it seems that none of your cards is trying to get an IP address or if they do they fail to get it from your router.

---

### Post by DHart07 on 2011-01-16
```


dave@dave-Satellite-A505 ~ $ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 3420
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:26:6c:41:a0:48
Sending on   LPF/eth0/00:26:6c:41:a0:48
Listening on LPF/wlan0/70:1a:04:d3:e4:54
Sending on   LPF/wlan0/70:1a:04:d3:e4:54
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.136 from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPNAK from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPOFFER of 192.168.2.136 from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.137 from 192.168.2.1
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPNAK from 192.168.2.1
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.137 from 192.168.2.1
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
DHCPOFFER of 192.168.2.136 from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dave@dave-Satellite-A505 ~ $ 

```

I had my ethernet cable plugged in during this.

---

### Post by DHart07 on 2011-01-16
I guess really where my confusion is coming from is as to why everything worked fine on the livecd.  I admit that I am pretty new to the whole linux thing but I don't see why running off of the CD everything works great (fan, wireless, ethernet, it runs the same as my traditional windows it seemed like) but once I do a full install said things simply do not work.  What exactly is the difference between running off of the cd, and not simply along side windows but actually BOOTING from the cd, and running from the new OS?

---

### Post by amsterdamharu on 2011-01-16
What are your router settings? Looks like you assign static ip addresses since you get different output than me:

```
DHCPOFFER of 192.168.0.11 from 192.168.0.1
DHCPREQUEST of 192.168.0.11 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.11 from 192.168.0.1
bound to 192.168.0.11 -- renewal in 37089 seconds.
```

You don't get the DHCPACK from your router and the card doesn't seem to accept the offered IP address from the router.

```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.136 from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
```

I have to admit that I'm at a loss here. 
I am sure if you fixed the wired settings it's a small step to fix the wireless.

---

### Post by amsterdamharu on 2011-01-16
Yes, somehow your router is not sending the DHCPACK or your card(s) are ignoring it. You need it "This packet includes the lease duration and any other configuration information that the client might have requested."
[http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#DHCP_acknowledgement](http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#DHCP_acknowledgement)

You can try that command running from a live CD, it would be strange if it works still. I think someone fiddled with your router.

The difference between live CD and install is that you can update the install, get more programs and use different drivers.

---

### Post by DHart07 on 2011-01-16
Wide area network (WAN) settings  -  Dynamic 	  	 
			
Broadband connection: 	Connected
WAN IP address: 	98.212.219.72
Subnet mask: 	255.255.252.0
Default gateway: 	98.212.216.1
Primary Domain Name System (DNS): 	68.87.72.134
Secondary DNS: 	68.87.77.134
			
			
  	Local area network (LAN) settings 	  	  	  	 
			 	
Local IP address: 	192.168.2.1
Subnet mask: 	255.255.255.0
DHCP server: 	Enabled
	  	 
			
  	Wireless settings 	  	 
			
Wireless network name (SSID): 	MyNetwork
Channel: 	6
Encryption type: 	WEP
	  	 
			
  	DHCP client list 	  	 
			
IP address 	Host name 	MAC address
	  
192.168.2.137 	dave-Satellite-A505 	00-26-6C-41-A0-48
192.168.2.86 	dave-Satellite-A505 	70-1A-04-D3-E4-54
192.168.2.119 	DHart-PC 	00-1E-90-6A-72-4E
192.168.2.68 	192.168.2.68 	00-17-FA-1E-90-16
	  	 

  	Base station information 	  	 
			
Runtime code version: 	02.01.02.0590
Boot code version: 	02.01.02.0590
LAN MAC address: 	00-0D-3A-70-32-E3
MAC address: 	00-0D-3A-70-32-E2
Serial number: 	468091787903
Hardware version: 	00.00.00.0004
	  	 
This is all directly from my device webpage.

---

### Post by DHart07 on 2011-01-16
I understand the difference between the livecd and an install but I don't understand why my hardware operates differently under the two.  And what command do you want me to try while on the livecd?  Thanks for all of the help, time and effort by the way, I greatly appreciate it.

---

### Post by amsterdamharu on 2011-01-16
The last one please:

```
sudo dhclient
```Although the settings of the router are "[COLOR=Red]DHCP server:     Enabled[/COLOR]". So it's probably not related to router settngs.

I would not know why it wouldn't accept the ip address, the command dhclient will just ask for an ip address like ipconfig /renew on Windows.

There might be something funny in your interfaces file but I'd think removing the connections with network manager might have solved that.
You could try and see what's in there using the following command:
```
cat /etc/network/interfaces 
```It usually only says:
```
auto lo
iface lo inet loopback

```Sorry I can't be of more help, it might have something todo with the day the install detected the network. If it's driver related then it's a huge coincidence that both work in live cd and both don't after install.

---

### Post by amsterdamharu on 2011-01-16
After you removed the connections by right clicking the network icon in the panel and choose edit you restarted and there should have been an item added called "Auto Ethernet".
When you click on the icon it should show.

If not you can right click and choose edit connections then delete all the connections in the wired tab and close.
Now open a terminal and restart network-manager with the following commands:
```
sudo service network-manager stop
sudo service network-manager start
```

Now when you (left) click on the network icon in the panel the "Auto Ethernet" should show. You can click on it to connect.

---

### Post by DHart07 on 2011-01-16
From the livecd I ran sudo dhclient 3 seperate times.
The first time not connected to any connections
```

ubuntu@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 4963
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/70:1a:04:d3:e4:54
Sending on   LPF/wlan0/70:1a:04:d3:e4:54
Listening on LPF/eth0/00:26:6c:41:a0:48
Sending on   LPF/eth0/00:26:6c:41:a0:48
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.86 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST of 192.168.2.86 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Connected via ethernet
```

ubuntu@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 5021
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/70:1a:04:d3:e4:54
Sending on   LPF/wlan0/70:1a:04:d3:e4:54
Listening on LPF/eth0/00:26:6c:41:a0:48
Sending on   LPF/eth0/00:26:6c:41:a0:48
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.86 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.136 from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.136 from 192.168.2.1
bound to 192.168.2.136 -- renewal in 575732 seconds.

```
And finally connected via wireless.
```

ubuntu@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 5131
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:26:6c:41:a0:48
Sending on   LPF/eth0/00:26:6c:41:a0:48
Listening on LPF/wlan0/70:1a:04:d3:e4:54
Sending on   LPF/wlan0/70:1a:04:d3:e4:54
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.2.86 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.86 from 192.168.2.1
bound to 192.168.2.86 -- renewal in 455269 seconds.
ubuntu@ubuntu:~$ 

```

And yes, those are the only 2 lines in the interfaces file.

---

### Post by DHart07 on 2011-01-18
Bring Up My Post.

---

