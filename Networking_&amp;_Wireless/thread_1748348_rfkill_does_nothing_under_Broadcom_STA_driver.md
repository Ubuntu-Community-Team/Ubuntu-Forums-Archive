---
title: "rfkill does nothing under Broadcom STA driver?"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by northd_tech on 2011-05-03
I've been seeing a lot of people checking for hardware and software blocks using the rfkill command.  I can't seem to get it to do anything at all on my Broadcom "4321AG"/"4328" wireless using the Broadcom STA driver.  Of course, I have an old-fashioned hardware switch on the front of my laptop.

Here is some information on my **working** wireless setup (that **rfkill **can't seem to see):

> 
**lspci | grep work**
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=wl0 driverversion=5.60.48.36 **ip=192.168.2.2 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f2200000-f2203fff memory:f2000000-f20fffff(prefetchable)
[B]
dmesg | grep wl[/B]
[    9.661026] wl: module license 'MIXED/Proprietary' taints kernel.
[    9.667906] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[    9.667912] wl 0000:03:00.0: setting latency timer to 64

**lsmod | grep wl**
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
[B]
iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:227  Noise level:168
          Rx invalid nwid:0  invalid crypt:5  invalid misc:0

**ifconfig**
eth1      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe13:2412/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135191 errors:1553 dropped:0 overruns:0 frame:153271
          TX packets:87546 errors:21 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:180836189 (180.8 MB)  TX bytes:16063449 (16.0 MB)
          Interrupt:19 
[B]
cat /etc/lsb-release[/B]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

**uname -a**
Linux xxxx-laptop 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 GNU/Linux

**rfkill --version**
rfkill 0.3
I do find **rfkill **installed and **locate**'d among other places at:
> /etc/bash_completion.d/rfkill
/sbin/rfkill
/usr/sbin/rfkill
/var/cache/apt/archives/rfkill_0.3-3_amd64.deb
When I run just **rfkill** with no parameters, it says:
> Usage:    rfkill [options] command
Options:
    --version    show version (0.3)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps
When I try **rfkill list all**, it does nothing, just returns me to my BASH prompt.  The wifi, wlan, bluetooth, and wwan identifiers also seem to do nothing with **rfkill list**.  It looks to me like it "hooked" IRQ19 in the BIOS, and the wireless does work quite stably (although it does need several seconds to auto-reestablish wireless when Linux goes to "sleep," say overnight).

This page doesn't really tell me much more than **rfkill** did with no parameters:

[http://manpages.ubuntu.com/manpages/lucid/man1/rfkill.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/rfkill.1.html)

Is this just because I have an electromechanical wireless switch, or is it a 64-bit problem, or...

:confused:

EDIT:  Oh yes,** sudo rfkill list all** also just returns me to my BASH prompt without any whistles or bells (after entering a password)...

---

### Post by josephmills on 2011-05-03
EDIT try and uninstall rfkill and re-install it

---

### Post by northd_tech on 2011-12-06
> **josephmills said:**
> EDIT try and uninstall rfkill and re-install it  UPDATE:  I have since found/discovered that the problems with **rfkill** and Monitor Mode in the STA driver are apparently gone in the newer 5.100.82.xxxx STA driver modules.  

Although this is for Gentoo linux (I'm currently trying to hack some wireless updating of Kaspersky's otherwise excellent Gentoo-based KAV10 Rescue Disk), this is consistent with my recent experience under [COLOR=Red]**multilib** (32-bit AND 64-bit)[/COLOR] Red Hat-based Scientific Linux 6.1 (SL6.1, which is similar to Fedora 15/16, CentOS6, and Red Hat Enterprise Linux6 or RHEL6):

> **Optional: Monitor mode **

 Since 5.100.82.111 broadcom-sta driver supports [monitor mode]("http://www.wikipedia.org/wiki/Monitor_mode"). To enable it run 
 [COLOR=#000000][FONT=monospace]echo 1 > /proc/brcm_monitor0[/FONT][/COLOR]
 and to disable: 
 [COLOR=#000000][FONT=monospace]echo 0 > /proc/brcm_monitor0[/FONT][/COLOR]
 
When monitor mode is enabled, prism0 network interface appears.... 
[http://en.gentoo-wiki.com/wiki/Broadcom_43xx](http://en.gentoo-wiki.com/wiki/Broadcom_43xx)

Also, here is some of my recent output which supports the Gentoo information (after converting from Ubuntu 10.04.3 LTS to SL 6.1):

> **CAELinux2011-Ubuntu 10.04.3 LTS]  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       driver=wl0 [B]driverversion=5.60.48.36
[/B]
$ **rfkill list all**
caelinux@caelinux:~$

caelinux@caelinux:~$ iwconfig eth1 mode **Monitor**
Error for wireless request "Set Mode" (8B06) :
    [COLOR=Red]**SET failed on device eth1  said:**
> 


Although I'm in Vista now (mainly to verify my new GRUB installation for SL 6.1 and do some housekeeping), I remember **rfkill** telling me there were no hardware and no software blocks using my newly-compiled Broadcom 5.100.xxxx.xxxx "wl.ko" driver under Scientific Linux 6.1 early this morining.  

(I compiled the newer **rfkill**-capable driver module from the newest 64-bit version 5.100.82.112 STA sourcecode found on Broadcom's website since there were no Broadcom CentOS6 .RPM packages anywhere):

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

From the 5.100.82.112 README.txt file:

> ISSUES FIXED AND WHAT'S NEW IN THIS RELEASE ------------------------------------------- 
+ Added cfg80211 API support. The choice of API is done at compile time. If kernel version >= 2.6.32, cfg80211 is used, otherwise wireless extension  is used. (End users should notice little difference.) 
+ Supports Linux kernel 2.6.38 
+ Fix for problem with rebooting while wireless disabled via airline switch. 
+ Fixed a kernel panic observed on some 64-bit systems  

HOW TO USE MONITOR MODE ----------------------- 
To enable monitor mode: 
$ echo 1 > /proc/brcm_monitor0  

Enabling monitor mode will create a 'prism0' network interface. Wireshark and other network tools can use this new prism0 interface.  

To disable monitor mode: 
$ echo 0 > /proc/brcm_monitor0   

ISSUES FIXED AND WHAT'S NEW IN RECENT RELEASES ------------------------------------------- 
+ **Supports monitor mode** 
+ Supports cfg80211 
+ Supports hidden networks 
+ Supports **rfkill**[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Now if I could only get those weeks back that I spent messing around with the b43 driver for my Broadcom 4321AG to get those things "supported?"...

---

