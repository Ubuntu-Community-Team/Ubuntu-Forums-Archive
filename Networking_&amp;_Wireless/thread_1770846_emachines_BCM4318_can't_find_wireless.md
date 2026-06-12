---
title: "emachines BCM4318 can't find wireless"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by blavthefaur on 2011-05-29
Just installed Ubuntu on my sister-in-law's emachines. Suddenly, her computer's not finding any wireless networks (although the other two Linux computers in the house find and connect just fine, as did her computer when it ran Windows).

I followed the advice on the bcm43xx Wiki page, but to no avail ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)).

Here's some output I hope helps.

~$ lspci 
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller 
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller 
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller 
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11) 
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller 
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge 
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02) 
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) 
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21) 
03:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller 
03:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller 
03:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller 
03:07.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller 
03:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

```

~$ lshw -C network
```
  *-network               
       description: Ethernet interface 
       product: NetLink BCM5789 Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 21 
       serial: 00:03:25:1a:90:1c 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5789-v3.49a latency=0 multicast=yes port=twisted pair 
       resources: irq:18 memory:d0100000-d010ffff 
  *-network UNCLAIMED 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 9 
       bus info: pci@0000:03:09.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: latency=64 
       resources: memory:d0206000-d0207fff 
```

~$ iwconfig
```
lo        no wireless extensions. 

eth0      no wireless extensions. 

```

~$ ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:03:25:1a:90:1c  
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
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB) fff
```

Thanks in advance for any help!

---

### Post by josephmills on 2011-05-29
hi there could we see a ```
lsmod | grep b43
``` and a ```
dmesg | grep b43 
```

---

### Post by blavthefaur on 2011-05-29
Thanks for the reply, josephmills!

Unfortunately, neither returns any output.

~$ lsmod | grep b43
~$ dmesg | grep b43
~$ 

Should I post the results of each without the grep?

---

### Post by josephmills on 2011-05-29
are you connected to the internet with the ubuntu computer (cat 5 cable)?

---

### Post by blavthefaur on 2011-05-29
Yep.

---

### Post by josephmills on 2011-05-29
please open up ubuntu software center then go to edit-->software sources then make sure all are ticked (see pics )then close out of software sources and ubuntu software center and open your terminal (ctrl+alt+t) and copy and paste this in the terminal  ```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get remove bcmwl-kernel-source && sudo reboot 
``` after reboot open up your terminal again and type in ```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer && sudo apt-get install bcmwl-kernel-source 

``` then restart again anything? if not could we see a ```
lsmod | grep b43 && dmesg | grep b43 
```

---

### Post by blavthefaur on 2011-05-30
In running the first set of commands, I got this error as it tried to upgrade:

```
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up firmware-b43legacy-installer (4.178.10.4-5) ...
Not supported card here (PCI id 14e4:169
14e4:4318)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libisc62 (1:9.7.3.dfsg-1ubuntu2.1) ...
Setting up libdns69 (1:9.7.3.dfsg-1ubuntu2.1) ...
Setting up libisccc60 (1:9.7.3.dfsg-1ubuntu2.1) ...
Setting up libisccfg62 (1:9.7.3.dfsg-1ubuntu2.1) ...
Setting up libbind9-60 (1:9.7.3.dfsg-1ubuntu2.1) ...
Setting up liblwres60 (1:9.7.3.dfsg-1ubuntu2.1) ...
Setting up bind9-host (1:9.7.3.dfsg-1ubuntu2.1) ...
Setting up dnsutils (1:9.7.3.dfsg-1ubuntu2.1) ...
Setting up gnome-nettool (2.32.0-0ubuntu1.1) ...
Setting up xserver-common (2:1.10.1-1ubuntu1.1) ...
Setting up xserver-xorg-core (2:1.10.1-1ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
:~$
```Should I go ahead and run the second set of commands?

---

### Post by blavthefaur on 2011-05-30
After I uninstalled the installer package for firmware for the b43legacy driver, I ran the commands successfully and rebooted twice. However, there's still no networks showing and when I run the last command group

lsmod | grep b43 && dmesg | grep b43

there's still no output.

```
~$ lsmod | grep b43 && dmesg | grep b43
:~$ 

```

Thanks for you're help so far!

---

### Post by josephmills on 2011-05-30
```
lspci -vnn | grep 14e4
``` you did not enter the code right to paste something in the terminal press shift+ctrl+v and to copy shift+ctrl_c hope that this helps

---

### Post by josephmills on 2011-05-30
> **blavthefaur said:**
> After I uninstalled the installer package for firmware for the b43legacy driver, I ran the commands successfully and rebooted twice. However, there's still no networks showing and when I run the last command group

lsmod | grep b43 && dmesg | grep b43

there's still no output.

```
~$ lsmod | grep b43 && dmesg | grep b43
:~$ 

```

Thanks for you're help so far!

who said anything about the firmware-b43legacy-installer you just need the firmware-b43-installer it is all there all you have to do is copy and paste so copy this



[b]
sudo apt-get update && sudo apt-get upgrade && sudo apt-get remove bcmwl-kernel-source && sudo reboot

[/b]


and paste it in your terminal then it will reboot auto 


then copy this and paste it in the terminal 

[b]
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer && sudo apt-get install bcmwl-kernel-source

[/b]
then reboot you should have wireless

---

### Post by blavthefaur on 2011-05-31
So I ran both, rebooting twice and all that, yet the computer's still not finding the available networks (only eth0, which is the wired). Also, I didn't get anything with a grep b43  (as you first asked) but I did with a grep 14e4. Hopefully, this  helps:

lspci -vnn | grep 14e4
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express [14e4:169d] (rev 21)
03:09.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Broadcom Corporation Gateway 7510GX [14e4:0449]

```dmesg | grep 14e4```

[    0.085278] pci 0000:02:00.0: [14e4:169d] type 0 class 0x000200
[    0.086231] pci 0000:03:09.0: [14e4:4318] type 0 class 0x000280
```Any clues to the problem?

---

### Post by garvinrick4 on 2011-05-31
Just check these two in Synaptics and check in a "Additional Drivers" in applications to see
if enabled and if not all three things do them and enable and reboot:
###Edit you are a 4318 I am sorry lets find the 4318 driver.###

---

### Post by garvinrick4 on 2011-05-31
Here it is install from synaptics, believe you might have tried to install wrong earlier.
```

rick@rick-HP:~$ aptitude show firmware-b43-installer
Package: firmware-b43-installer          
New: yes
State: not installed
Version: 4.150.10.5-5
Priority: optional
Section: multiverse/kernel
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 49.2 k
Depends: b43-fwcutter (>= 1:012), bzip2, wget
Recommends: linux-image
Conflicts: firmware-b43-lpphy-installer
Description: Installer package for firmware for the b43 driver
 This package installs the firmware needed for usage of the b43 kernel driver. 
 
 Supported chipsets: 
 * BCM4306/3 
 * BCM4311 
 * BCM4312 
 * BCM4318

rick@rick-HP:~$ 

```

---

### Post by garvinrick4 on 2011-05-31
##This is what you tried to install earlier below: Wrong card:
rick@rick-HP:~$ aptitude show firmware-b43legacy-installer
Package: firmware-b43legacy-installer    
New: yes
State: not installed
Version: 4.178.10.4-5
Priority: optional
Section: multiverse/kernel
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 49.2 k
Depends: b43-fwcutter (>= 1:012), wget
Recommends: linux-image
Description: Installer package for firmware for the b43legacy driver
 This package installs the firmware needed for usage of the b43legacy kernel
 driver. 
 
 Supported chipsets: 
 * BCM4301 
 * BCM4303 
 * BCM4306/2

rick@rick-HP:~$

---

### Post by blavthefaur on 2011-06-04
I tried uninstalling and reinstalling this with Synaptics and with Terminal. Neither, however, made a difference. Is there something I need to do after installation in order to make it run? 

Thanks!

---

### Post by garvinrick4 on 2011-06-04
> **blavthefaur said:**
> I tried uninstalling and reinstalling this with Synaptics and with Terminal. Neither, however, made a difference. Is there something I need to do after installation in order to make it run? 

Thanks!
In Additional Drivers see if it needs to be enabled. In 10.10 and older I believe it was
Restricted drivers in System/Admin then needs a reboot.

---

### Post by garvinrick4 on 2011-06-04
If you still have problems;
```
sudo ifconfig wlan0 up 
```
Will see if can get your radio signal up.
```
iwlist scan
```
Can you see your SSID (the name you gave your wifi signal
##### If you still have problems:
Here is the name of the best I have seen on Network cards:
chili555
leave him a message and ask for some help. Do not think he would
mind at all. Give him this link:

---

### Post by blavthefaur on 2011-06-04
In Additional Drivers, I get this message:

> The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with ALSA supportand snd-intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.

Using the Software Center, I installed the sl-modem-source package and rebooted, but I'm still not showing any wireless networks (not even from the one I set up). Perhaps I should try ALSA?

Also, I've attached a screenshot.

Here's what I get from both commands:

```
***@mushroom:~$ sudo ifconfig wlan0 up
[sudo] password for ***: 
wlan0: ERROR while getting interface flags: No such device
***@mushroom:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

***@mushroom:~$ 

```

Thanks for your help so far!

---

### Post by garvinrick4 on 2011-06-04
Smartlink modem is the dial-up modem.
It is still showing you have no wlan0 (your wireless connection) at all.
Get hold of chili555 leave him a message. I have given all I know this
will bumb it up to head of Forum maybe another user with better Network
card skills will jump in.

---

### Post by garvinrick4 on 2011-06-04
I would open up Synaptic Package Manager and type "bcm" in search box in upper right
and see what you have installed, you could have all sorts of things going on by now.
You just need the 2 we talked about. with the 4318 card. Can install and uninstall from there.
firmware-b43-installer
b43-fwcutter

---

### Post by blavthefaur on 2011-06-04
It works! Thank you so much, garvinrick4 and josephmills!

You were right, garvinrick4. I had another bcm file on the computer (bcmwl-kernel-source). Once I removed that with Synaptic Manager, the wireless networks appeared!

Thanks again!

---

### Post by aplima on 2011-06-07
> **josephmills said:**
> who said anything about the firmware-b43legacy-installer you just need the firmware-b43-installer it is all there all you have to do is copy and paste so copy this



[B]
sudo apt-get update && sudo apt-get upgrade && sudo apt-get remove bcmwl-kernel-source && sudo reboot

[/B]


and paste it in your terminal then it will reboot auto 


then copy this and paste it in the terminal 

[B]
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer && sudo apt-get install bcmwl-kernel-source

[/B]
then reboot you should have wireless

Withouth that last reboot advice I had wireless running...
When I rebooted the notebook wireless was gone again.
What went wrong here? :(

---

### Post by blavthefaur on 2011-06-07
I don't know if your computer's the same as my sister-in-law's, but as soon as I uninstalled bcmwl-kernel-source via the Synaptic Package Manager, her computer was able to discover wireless networks. I found garvinrick4's advice (page 2 of the comments) helpful and accurate.

---

### Post by aplima on 2011-06-09
> **blavthefaur said:**
> I don't know if your computer's the same as my sister-in-law's, but as soon as I uninstalled bcmwl-kernel-source via the Synaptic Package Manager, her computer was able to discover wireless networks. I found garvinrick4's advice (page 2 of the comments) helpful and accurate.

The advice worked until I rebooted the machine.

Notebook: ASUS A6K series.
Wireless Lan: BCM 4318 REV 2 (This is what it says on the hardware!)
Wireless Lan from lspci: BCM 4306 REV3

As I said, following excellent advice it worked until I rebooted the notebook.

---

### Post by aplima on 2011-06-09
> **aplima said:**
> The advice worked until I rebooted the machine.

Notebook: ASUS A6K series.
Wireless Lan: BCM 4318 REV 2 (This is what it says on the hardware!)
Wireless Lan from lspci: BCM 4306 REV3

As I said, following excellent advice it worked until I rebooted the notebook.

SOLVED!

I must have tried to many and all those different atempts were screwing the chance to this solution to work.
I reinstalled, went to synaptics manager:
Installed B43-fwcutter and firmware-b43-installer

Problem solved, for good!

Thank you all!

---

