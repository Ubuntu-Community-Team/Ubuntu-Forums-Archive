---
title: "Flakey wifi after updating to 9.04 on macbook pro 3,1"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by Elshar on 2009-04-24
Wifi under 8.10 was working flawlessly (Although I think I was using madwifi), and after updating to 9.04 I'm having some sporadic flakey problems with it. It seems every 5-10 minutes (sometimes sooner) it de-associates from the AP and then re-associates.

I highly doubt it's a signal problem as the laptop is about 5' from the AP. I am using WPA2, but it was working fine before.

I also tried re-building the madwifi drivers and rebooting, but it hasn't fixed my problem.

Also, I can't seem to connect to svn.madwifi.org, are they having problems or something?

---

### Post by Elshar on 2009-05-23
I still haven't sorted this one out yet. I even grabbed the source off of svn, compiled it like I did in 8.04 and replaced the stock modules to no avail. This is what is happening to me every few minutes:

```
64 bytes from 192.168.0.1: icmp_seq=28 ttl=64 time=1.10 ms
64 bytes from 192.168.0.1: icmp_seq=29 ttl=64 time=1.26 ms
64 bytes from 192.168.0.1: icmp_seq=30 ttl=64 time=1.64 ms
64 bytes from 192.168.0.1: icmp_seq=31 ttl=64 time=1.11 ms
64 bytes from 192.168.0.1: icmp_seq=32 ttl=64 time=2733 ms
64 bytes from 192.168.0.1: icmp_seq=33 ttl=64 time=1734 ms
64 bytes from 192.168.0.1: icmp_seq=34 ttl=64 time=735 ms
64 bytes from 192.168.0.1: icmp_seq=35 ttl=64 time=1.03 ms
64 bytes from 192.168.0.1: icmp_seq=36 ttl=64 time=1.17 ms
64 bytes from 192.168.0.1: icmp_seq=37 ttl=64 time=1.14 ms

```

There's nothing in dmesg or /var/log/messages saying anything about losing association, and this problem does not happen under OSX or XP (I'm triple-booting on this laptop). It also did not happen under 8.04 using the madwifi drivers.


Oh, and that was a "good" one, most often when this happens I'll get about 10-20 seconds of the device being down before it comes back up. This time it was just a few 1000-3000ms pings

---

### Post by seelm on 2009-07-23
Hi Elshar,

I was wondering if you ever figured out a solution to this problem?  Having the same spotty/weak signal issue with my macbook pro 3,1 although this was the first time wireless worked out of the box for me.  Upon forum search it seems some people are pinning their issues to ipv6 being enabled, however I am not yet convinced this is the problem.  Some are also claiming Wicd may be a better than Network Manager.  Have you found anything that is working for our specific macbook pro?  

here is the output of "lshw -C network" command:
[INDENT]> description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:63:c4:99:bf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.27 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:1b:63:a1:a9:70
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:85:ba:8a:8d:b2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/INDENT]

---

### Post by moore.bryan on 2009-07-23
Jaunty automatically uses the FOSS ath5k driver for the Atheros chipset instead of the proprietary Madwifi driver (ath_pci). You can "re-enable" the Madwifi one through your hardware selection tool; it's somewhere in the main menu, under "System" I believe. You can also update to the *latest* kernel, with which I've had much better luck.

---

### Post by seelm on 2009-07-23
Hi Bryan,

Thank you for the response.  Unfortunately in my System->Administration->Hardware Drivers, the madwifi does not show up, and from Elshar's post above this does not seem to be a solution.  The driver currently being used in my kernel 2.6.28-13-generic, is the ath9k.  My readouts are very similar to Elshar:
[INDENT]```
Bytes    Source    Seq    Time    Units
64    69.63.178.11    1    87.6    ms
64    69.63.178.11    2    86.5    ms
64    69.63.178.11    3    133    ms
64    69.63.178.11    4    245    ms
64    69.63.178.11    5    681    ms
64    69.63.178.11    6    757    ms
64    69.63.178.11    7    281    ms
64    69.63.178.11    8    730    ms
64    69.63.178.11    9    738    ms
64    69.63.178.11    10    323    ms
64    69.63.178.11    11    620    ms
64    69.63.178.11    12    626    ms
64    69.63.178.11    13    625    ms
64    69.63.178.11    14    630    ms
64    69.63.178.11    15    629    ms
64    69.63.178.11    16    140    ms
64    69.63.178.11    17    2306    ms
64    69.63.178.11    18    1307    ms
64    69.63.178.11    19    307    ms
64    69.63.178.11    20    86.7    ms
64    69.63.178.11    21    88.8    ms
64    69.63.178.11    22    87.6    ms
64    69.63.178.11    23    94.2    ms
64    69.63.178.11    24    87.2    ms
```[/INDENT]Frustrating how touchy it is.  Also have difficulty connecting to my own Linksys WRT5something router.  Sorry for being such a n00b, but is there an easy way to upgrade the kernel through terminal, tried using [URL="http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/"]this guide
[/URL] which ends in typing something like "sudo apt-get install kernel-image-2.6.30.2" but all I get is "Couldn't find package kernel-image-2.6.30.2".    Thanks for help,

max

---

### Post by moore.bryan on 2009-07-23
[Here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc4/")'s the latest kernel. Download the correct kernel image for your architecture (AMD or i386) and the linux headers for "all."

If that doesn't seem to fix your problem, post back and we can start troubleshooting.

---

### Post by seelm on 2009-07-23
Well, this seems to have helped the wifi issue as connections are now established quickly and no major flakiness.  Definitely a significant improvement.  However, I should have read the forums warning about no NVIDIA driver support as it crashes on bootup, then doesn't allow you to activate the driver, leaving me with no graphics:
[http://ubuntuforums.org/showthread.php?p=7646462](http://ubuntuforums.org/showthread.php?p=7646462)

I think I will have to find a Goldilocks solution of which kernel fits just right between graphics and wifi connectivity.

Linux 2.6.31-020631rc4-generic #020631rc4 SMP Thu Jul 23 09:04:59 UTC 2009 x86_64 GNU/Linux

---

### Post by moore.bryan on 2009-07-23
Sorry about that one... I should have thought to ask if you're running any proprietary stuff like Nvidia.

Well, with the older kernel, did you install linux-restricted-modules-common?

---

### Post by seelm on 2009-07-24
As stated above upgrading has definitely improved my wireless experience...night and day.  As far as getting the NVIDIA driver here is what I did for us n00bs, now everything works flawlessly including WOW at 70+fps.

Navigate to NVIDIA's site where they post their latest beta drivers:
[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

I downloaded the current release 190.18 to my desktop.
I reinstalled my linux headers from the site Bryan mentioned above.  Next I went into system->administration->synaptic package manager and uninstalled my "wine" packages and "nvidia" packages.  To prevent a gcc compiler error that I kept getting during driver installation I searched for "gcc" (still in package manager) and installed all 4.2 packages.

Now the fun part. ```
 fn ctrl alt f1
``` to get to terminal. ```
sudo apt-get purge nvidia*
``` to make sure I got everything. ```
sudo /etc/init.d/gdm stop
```   to stop X from running.  Then navigate to where you placed your downloaded driver file, in my case cd Desktop.
 ```
sudo CC=gcc-4.2 sh NVIDIA-Linux-x86_64-190.18-pkg2.run
``` (I have this all in one line) hit enter, enter you password, and this should start installation process.  I clicked "yes" on every question.  After its done just sudo /etc/init.d/gdm start, or sudo reboot if you want. 

Errors that I got that should be prevented by above process:

[LIST]
[*]gcc error saying kernel compiler 4.3 didn't match 4.2 compiler, this is solved by CC=gcc-4.2 line,
[*]4.2 compiler error saying it doesn't have library or files, solved by installing all gcc 4.2 packages,
[*]Kernel source error where it couldn't find the source of my kernel, solved by reinstalling headers, per Bryan's site.
[/LIST]
Reinstall wine, drag your game files back into program files folder and good to go.  If you go to system->Administration, you should now see NVIDIA X server settings menu for nvidia driver info.  This installation did not update the "Hardware drivers" menu, but added an annoying NVIDIA beta driver startup screen during booting process, I guess to ensure everyone that the driver was installed.

Bryan thank you again for the upgrade advice, I still cannot believe the amount of improvement in the wireless!

---

### Post by moore.bryan on 2009-07-24
I was pining about the poor performance of the ath5k driver in another thread when someone posted they had better performance with the latest kernel. Voila.

Glad to hear you got things working and kudos to you for Gerry-rigging the Nvidia fix.

---

