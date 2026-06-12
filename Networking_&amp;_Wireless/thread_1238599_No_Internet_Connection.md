---
title: "No Internet Connection"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by tinyfunkmaster on 2009-08-12
I'm quickly running out of options here and need some help!!  I'm running an HP DV5000 series laptop with the 64-bit version of Jaunty (recently zapped Windows).  I was initially trying to get the wireless working but didn't have a wired connection to the internet to download the b43-fwcutter package.  Tried the wired network but no luck.
 
Result of [FONT=Lucida Console]lspci[/FONT][FONT=Verdana]:[/FONT]
 
[FONT=Times New Roman][SIZE=2]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=1][FONT=Nimbus Roman No9 L]06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/FONT][/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2][FONT=Nimbus Roman No9 L][/FONT][/SIZE][/FONT] 
[FONT=Lucida Console][SIZE=2]lshw -c network:[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]*-network:0             [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       description: Network controller[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       vendor: Broadcom Corporation[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       physical id: 2[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:06:02.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       version: 02[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       width: 32 bits[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       capabilities: bus_master[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       configuration: driver=b43-pci-bridge latency=64 module=ssb[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       description: Ethernet interface[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       product: RTL-8139/8139C/8139C+[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       vendor: Realtek Semiconductor Co., Ltd.[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       physical id: 6[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:06:06.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       logical name: eth0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       version: 10[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       serial: 00:0f:b0:c4:f1:ee[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       size: 10MB/s[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       capacity: 100MB/s[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       width: 32 bits[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network:0 DISABLED[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       description: Wireless interface[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       physical id: 2[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       logical name: wlan0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       serial: 00:14:a5:7a:41:8c[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       capabilities: ethernet physical wireless[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network:1 DISABLED[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       description: Ethernet interface[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       physical id: 3[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       logical name: pan0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       serial: f6:e7:09:41:31:e3[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       capabilities: ethernet physical[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Any help would be greatly appreciated!![/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Lucida Console][/FONT]

---

### Post by Crafty Kisses on 2009-08-12
So I'm going to guess you have a newer kernel, first post the results of the following:
```
uname -r
```
You should have a newer kernel, so if you do have a newer kernel like a kernel that's 2.6.27 or later. Then you need to grab this right **[here.]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.30/compat-wireless-2.6.30.tar.bz2")** Once you have done that, you are going to need something called "build-essential" so in a terminal, run the following:
```
sudo apt-get install build-essential
```
Once build-essential has installed, you can go along with the compile of compat-wireless. Now once you have the package and build-essential, and now I'm just guessing here you have the file saved to your desktop, so run:
```
cd /home/username/Desktop/compat*
```
Where "username" is put your username, so once your in the compat directory, you need to untar the file:
```
tar xvjf compat*
```
Then you can go ahead and compile the file:
```
make
sudo make install
```
Then you should be set, if it isn't working instantly you might want to reboot, by running:
```
sudo shutdown -r now
```
Then see if you're wireless works. I wrote a great HOWTO on this, it's a lot more indepth than my reply to you, you might want to check it out right **[here.]("http://ubuntuforums.org/showthread.php?t=1233770")**

---

### Post by tinyfunkmaster on 2009-08-13
Codename... Thanks for helping out.  I swear I'm five minutes shy of throwing this computer off the top of a very large building.  It thanks you for saving its life.  Okay, you were right about the kernel version.  The [FONT=Lucida Console]uname -r [/FONT][FONT=Verdana]says that it's version 2.6.28.11- generic.  So I ran [/FONT][FONT=Lucida Console]sudo apt-get install build-essential [/FONT][FONT=Verdana]but it didn't install.  It came back and said, "E: Couldn't find package build-essential."  I have no connection to the internet whatsoever so if the sudo apt-get command is looking online then I wouldn't be able to see it.[/FONT]

---

### Post by tinyfunkmaster on 2009-08-13
Crap!!  I just looked at your HOWTO and it answered my question...  Let me try to download build-essential from the install CD...  *stupid*

---

### Post by harry2006 on 2009-08-13
follow the steps already mentioned and that shud do the job..else revert back. thank you.

---

### Post by tinyfunkmaster on 2009-08-13
Okay... So I downloaded the compat-wireless file from the link you gave me via a working connection and a flash drive and accessed your HOWTO to download the build-essentials package.  However, none of these commands were successful:
 
sudo mount -o loop cd.iso /mnt/image
sudo rm /cdrom
sudo ln -s /mnt/image /cdrom
sudo apt-cdrom -m add
sudo apt-cdrom add
 
Then I realized that I could just download build-essentials from the install CD but now when I try to download the package with Synaptic, it tells me "E: Unable to stat the mount point /cdrom/ -stat (2 No such file or directory)"  I suspect it was one of the commands in the HOWTO.  Anyways, if I can get the 'build-essentials' package off the CD then I'm good to go.

---

### Post by Crafty Kisses on 2009-08-13
> E: Unable to stat the mount point /cdrom/ -stat 


That sounds like you didn't have the CD in your drive when you ran the commands stated in the Howto. This is coming from the top of my head but try running the following:
```
sudo apt-cdrom -d /media/cdrom0 add
```
Then try running:
```
sudo aptitude update
sudo aptitude install build-essential
```
Make sure you have the CD in before you run the first command. Then get back to me.

---

### Post by tinyfunkmaster on 2009-08-14
Okay... Managed to download build-essentials from the install disc by establishing a symbolic link between my mount point and the /cdrom directory.  Followed your instructions for untaring and compiling wireless-compat.  Looked like everything installed like a dream.  I rebooted but nothing.  Still isn't seeing the wireless.  So now we have:
 
[FONT=Times New Roman][SIZE=3]tinyfunkmaster@tinyfunkmaster-laptop:~$ sudo lshw -c network[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network:0             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Network controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       vendor: Broadcom Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:06:02.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       version: 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: bus_master[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: driver=b43-pci-bridge latency=64 module=ssb[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Ethernet interface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       product: RTL-8139/8139C/8139C+[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       vendor: Realtek Semiconductor Co., Ltd.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 6[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:06:06.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       logical name: eth0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       version: 10[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       serial: 00:0f:b0:c4:f1:ee[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       size: 10MB/s[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capacity: 100MB/s[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network DISABLED[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Ethernet interface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       logical name: pan0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       serial: 4e:22:1a:33:eb:1e[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: ethernet physical[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][FONT=Times New Roman][EMAIL="tinyfunkmaster@tinyfunkmaster-laptop:~$"]tinyfunkmaster@tinyfunkmaster-laptop:~$[/EMAIL][/FONT][/FONT]
[FONT=Nimbus Roman No9 L][/FONT] 
[FONT=Times New Roman][FONT=Nimbus Roman No9 L]So at least Ubuntu is seeing the wireless card but it still can't see the ethernet and I suspect the card needs the firmware that the b43-fwcutter has that I need.  What do you think?[/FONT][SIZE=3] [/SIZE][/FONT]

---

### Post by tinyfunkmaster on 2009-08-14
Codename... Got it working!!  Re-installed Jaunty and for whatever reason the ethernet NIC card liked this latest install and I downloaded fwcutter and the wireless came up.  I guess the native b43/b43legacy drivers work fine it's just they need the proprietary firmware.  I scrubbed ndiswrapper from my machine and it's still humming along so.. Thanks for all the help!!

---

