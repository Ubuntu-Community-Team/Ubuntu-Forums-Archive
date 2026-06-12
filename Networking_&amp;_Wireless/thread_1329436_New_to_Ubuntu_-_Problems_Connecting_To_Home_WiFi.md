---
title: "New to Ubuntu - Problems Connecting To Home WiFi"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by SwitchUK on 2009-11-17
Hello All;

First Post and first install of a linux based OS ever!

I just installed UNR 9.10 on my Dell Mini 9. Having a few issues connecting to my home WiFi though.

I am at a bit of a loss as most average linux users would register me completly computer illiterate. Its possible I don't have the right drivers but then I wouldnt know how to install a driver or where to get my routers driver from. There doesn't seem to be any kind of automated scan for available wireless networks.

I tried to manually input my routers details but its possible i got the information wrong and its why its not connecting. I know my wifi is working because my android based phone is connecting no problem...

Little help?

Thanking in advance
Switch[uK]

---

### Post by SwitchUK on 2009-11-17
Oh and by the way: I already looked at the trouble shooting it said to input "sudo lshw -C network" to my console.

This displayed:

```

*-network
   description: Network Controller
   product: BCM4312 802.11b/g
   vendor: Broadcom Corporation
   physical id: 0
   bus info: pci@0000:03:00.0
   version: 01
   width: 64bits
   clock 33mhz
   capabilities: pm msi pciexpress bus_master cap_list
   configuration: driver=b43-pci-bridge latency=0
   resources: irq:17 memory: f02000000-f0203fff
*-network
   description: Ethernet interface
   product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
   vendor: Realtek Semiconductor Co., Ltd
   physical id: 0
   bus info: pci@0000:04:00.0
   version: 02
   serial: 00:21:70:b3:07:17
   size: 10MB/s
   capacity: 100MB/s
   width: 64bits
   clock 33mhz
   capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt-fd 100bt 100bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
    resources: irq: 27 ioport:2000(size=256) memory: f0610000-f0610fff(prefetchable) memory: f0600000-f060ffff(prefetchable) memory: f0620000-f063ffff(prefetable)


```

---

### Post by tapas_mishra on 2009-11-17
> **SwitchUK said:**
> 
```

*-network
   description: Network Controller
   product: BCM4312 802.11b/g
   vendor: Broadcom Corporation


```
This wifi card works well in Ubuntu you do not need to install any more driver I also have the same wifi card and it works very very fine I am using Ubuntu 9.04 just check the settings you might have messed with them.
Make sure when you boot to the Ubuntu machine you have your bluetooth and wifi running type as root
iwconfig and paste the output here you mentioned that you installed for the first time so 
open a terminal and type sudo passwd root 
enter a password and then run following 
su -
if iwconfig is not showing any thing then that might be an issue
in otherwise case you would like to see this page
[http://ubuntuforums.org/showthread.php?t=1266620&highlight=wifi+configuration](http://ubuntuforums.org/showthread.php?t=1266620&highlight=wifi+configuration)

---

### Post by bhishan on 2009-11-17
> **SwitchUK said:**
> Hello All;

First Post and first install of a linux based OS ever!

I just installed UNR 9.10 on my Dell Mini 9. Having a few issues connecting to my home WiFi though.

I am at a bit of a loss as most average linux users would register me completly computer illiterate. Its possible I don't have the right drivers but then I wouldnt know how to install a driver or where to get my routers driver from. There doesn't seem to be any kind of automated scan for available wireless networks.

I tried to manually input my routers details but its possible i got the information wrong and its why its not connecting. I know my wifi is working because my android based phone is connecting no problem...

Little help?

Thanking in advance
Switch[uK]

Are you connected to a wired network?

---

### Post by SwitchUK on 2009-11-18
> **tapas_mishra said:**
> 
Make sure when you boot to the Ubuntu machine you have your bluetooth and wifi running type as root

iwconfig and paste the output here



iwconfig shows:

```

lo        no wireless extensions

eth0    no wireless extensions

pan0   no wireless extensions

```

I know my bluetooth is working when i start ubuntu but i can't guarantee that my wifi is. How would I find that out? There doesnt seem to be an on button anywhere and i'm quite sure its turned on via hardware. Although the dell mini 9 function key for turning on wifi doesn't seem to be functioning anymore and it functioned in XP.

---

### Post by tapas_mishra on 2009-11-18
> **SwitchUK said:**
> iwconfig shows:

```

lo        no wireless extensions

eth0    no wireless extensions

pan0   no wireless extensions

```I know my bluetooth is working when i start ubuntu but i can't guarantee that my wifi is. How would I find that out? There doesnt seem to be an on button anywhere and i'm quite sure its turned on via hardware. Although the dell mini 9 function key for turning on wifi doesn't seem to be functioning anymore and it functioned in XP.
The above command shows that your wifi is not detected or configured 
I am pasting a sample out put from my iwconfig

```

root@tapas-laptop:/usr/share/doc/wpasupplicant/examples# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


eth1      IEEE 802.11bg  ESSID:"arrangemyparty"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:40:06:BF:93   
          Bit Rate=36 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=4/5  Signal level=-65 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:217  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```How are you posting this message on forum are you connected to a LAN which does not seems to me or you are saving the output some location.
The above output shows that eth1 is connected to a Wifi whose ESSID is arrangemyparty
paste the output cat /proc/modules here
and in the mean time go to Broadcom

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Download the right driver from there
then compile the driver as the steps given here
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
if you look at this page
[http://wiki.debian.org/WiFi](http://wiki.debian.org/WiFi)
do a Ctrl+F 
Broadcom chipsets (BCM4311, BCM4312, BCM4321, BCM4322) 
you see the icon which says it works with the copyrighted driver
and in the mean time there is also a package named Wicd use it to check your wifi
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Also visit this page
[https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html)

---

### Post by SwitchUK on 2009-11-18
> **tapas_mishra said:**
> The above command shows that your wifi is not detected or configured 
I am pasting a sample out put from my iwconfig

```

root@tapas-laptop:/usr/share/doc/wpasupplicant/examples# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


eth1      IEEE 802.11bg  ESSID:"arrangemyparty"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:40:06:BF:93   
          Bit Rate=36 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=4/5  Signal level=-65 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:217  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```How are you posting this message on forum are you connected to a LAN which does not seems to me or you are saving the output some location.
The above output shows that eth1 is connected to a Wifi whose ESSID is arrangemyparty
paste the output cat /proc/modules here
and in the mean time go to Broadcom

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Download the right driver from there
then compile the driver as the steps given here
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
if you look at this page
[http://wiki.debian.org/WiFi](http://wiki.debian.org/WiFi)
do a Ctrl+F 
Broadcom chipsets (BCM4311, BCM4312, BCM4321, BCM4322) 
you see the icon which says it works with the copyrighted driver
and in the mean time there is also a package named Wicd use it to check your wifi
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)


I was using another PC to post on the forums. I wasn't connected to a lan; but I have a LAN setup that me and my housemates use to share files and game.

How do I output cat /proc/modules?

---

### Post by SwitchUK on 2009-11-18
Oh and ive looked into wicd. It doesnt work through the command sudo apt-get install wicd

says: couldn't find package wicd

plus, i dont think i'm using jaunty. Im using karmic right?

So i tried to get wicd manually; then it said that i might need a package manager? Then when i tried to install it as above using the sudo command it said that i already had the latest version...

Oh and i tried to get the drivers from broadcom but even following the readme txt left me confused...

---

### Post by tapas_mishra on 2009-11-18
> **SwitchUK said:**
> Oh and ive looked into wicd. It doesnt work through the command sudo apt-get install wicd

says: couldn't find package wicd

plus, i dont think i'm using jaunty. Im using karmic right?

I am not sure on this part but I think you need to update the sources list which can be found in /etc/apt/sources.lst
check it you can connect with this Ubuntu laptop to internet on LAN

I am pasting the output of my sources.lst
here 
```

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/fta/ubuntu hardy main
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb http://ftp.debian.org etch main
deb http://security.debian.org/debian-security lenny/updates main
deb http://dl.google.com/linux/deb/ stable non-free




```> 
So i tried to get wicd manually; then it said that i might need a package manager? Then when i tried to install it as above using the sudo command it said that i already had the latest version...

Oh and i tried to get the drivers from broadcom but even following the readme txt left me confused...Let me know what was the confusion and which line was confusing to you.

just open a terminal and type cat /proc/modules
cat command is used to see the contents of a file and copy paste the output on your terminal in a word or text file then paste that out put here or if it is cubersome then just connect using a LAN and then post the output here and also tell me the output of cat /proc/net/wireless 
it is similar to using iwconfig you used above.

---

### Post by mikewhatever on 2009-11-18
I think you may be affected by the bug described [-->here<--]("http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html"). Just hook up a cable and install the required packages.

---

### Post by bobhjon on 2009-11-18
I also am a newbie to Linux, am writing this on a computer at the other side of the house so copying is limited, have the same problem as SwitchUK, and have the additional problem that GRUB's Windows command is to a Windows 7 beta which has been deactivated by Microsoft so I can't get out of ubuntu.

My iwconfig shows a substantial entry for wlan0, but the ESSID is " " so I assume that I need the SSID of my router although Windows picks up the wireless adapter with no problem. But I don't know how to find it in Ubuntu and I can't gat backj to Windows to get it.

What I would like to do is get back to the Windows boot menu and put Ubunto in there since I must use Windows regularly until I can see if Wine will handle my Ameritrade brokerage account.

So... where do I go from here?

---

### Post by SwitchUK on 2009-11-18
I tried the advice of mikewhatever and followed the instructions on the page he refered me to.

my iwconfig now outputs:

```

lo        no wireless extensions.

eth0    no wireless extensions.

eth2    IEEE 802.11 Nickname:""
          Access point: not-associated

pan0   no wireless extensions.

```

I feel like i might finally be getting somewhere!

How do i get this access point associated? 

On a further note: just installed wicd - just about to reboot to try it out

---

### Post by SwitchUK on 2009-11-18
Guys! its offical! I AM WIRELESS!

I got wicd installed and it picked up the drivers that i got and therefore my network and 2 clicks later i don't have to sit in this pokey little corner anymore!

However; this exercise has taught me that i need to know a lot more about ubuntu inorder to use it sucessfully in the future. I have the ubuntu pocket guide and im gonna spend some time and read though that.

Big thanks to all.
Problem solved

---

### Post by tapas_mishra on 2009-11-22
Great :) !!

---

