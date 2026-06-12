---
title: "Broadcom BCM4313 MONITOR MODE"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by kurci2 on 2010-12-29
Hi!
I'm testing my home wireless security. I heard about _kismet_. But a problem is that if you want to "sniff" you must put your wireless card into MONITOR MODE. I think that i can't do that.

here is what happens if i start kismet:
```
marko@ToShiba:~$ sudo kismet
[sudo] password for marko: 
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.
marko@ToShiba:~$ 
```

i have Broadcom STA Wireless driver (packet-i think: bcmwl-kernel-source, version 5.60)
could it be problem with my wireless drivers??

any ideas what can i do??

---

### Post by bkratz on 2010-12-29
The official Broadcom STA driver does not allow the mode of operation you want. The open source B43 does, but I will have to look and see if your particular card is compatible.

---

### Post by bkratz on 2010-12-29
Well according to this page

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Quote

BCM4313 with b/g (partially supported in 2.6.32, however 2.6.33 or latter is recommended)

Whatever partially supported means!  You may be stuck with STA.

---

### Post by kurci2 on 2010-12-29
do you mabye know for any guide how to install thist driver??
do i have to remove my STA driver first??

---

### Post by bkratz on 2010-12-29
> **kurci2 said:**
> do you mabye know for any guide how to install thist driver??
do i have to remove my STA driver first??



In reverse order, yes they would conflict and try here about 1/2 way down.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by kurci2 on 2010-12-29
ok
i will first uninstall STA driver and than i will fallow that tutorial you gave me...
i will "report" my success here =)

---

### Post by bkratz on 2010-12-29
> **kurci2 said:**
> ok
i will first uninstall STA driver and than i will fallow that tutorial you gave me...
i will "report" my success here =)

Found this for your card


[http://ubuntuforums.org/showthread.php?p=10283175#post10283175](http://ubuntuforums.org/showthread.php?p=10283175#post10283175)

---

### Post by Lupius on 2010-12-31
Tried the b43 driver a few months ago with absolutely no luck. fwcutter did not work as expected. BCM4313 is currently supported by the brcm80211 driver that is still in development. The current version has a partially working monitor mode (after applying the channel -1 patch) but does not yet allow packet capture without authentication. Still waiting on updates on this issue.

---

### Post by kurci2 on 2010-12-31
how can i apply channel -1 patch??

---

### Post by kurci2 on 2011-01-01
```
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

this is the error message i get if i try to install what is written here: [http://ubuntuforums.org/showthread.php?p=10283175#post10283175](http://ubuntuforums.org/showthread.php?p=10283175#post10283175)

this is kernel i have 
-Version-
Kernel		: **Linux 2.6.35-24-generic** (i686)
do i have to install a prior one??

---

### Post by bkratz on 2011-01-01
> **kurci2 said:**
> ```
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here ([COLOR="Red"]PCI id 14e4:4727[/COLOR])!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

this is the error message i get if i try to install what is written here: [http://ubuntuforums.org/showthread.php?p=10283175#post10283175](http://ubuntuforums.org/showthread.php?p=10283175#post10283175)

this is kernel i have 
-Version-
Kernel		: **Linux 2.6.35-24-generic** (i686)
do i have to install a prior one??

Well I believe you are out of luck--if you look at the table here

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

It shows that particular ID is not supported by b43, just STA (wl).

---

### Post by kurci2 on 2011-01-01
partially supported 2.6.33 and later 
what does that mean??
Ok, i fugured this out...only STA driver supports my card...

---

### Post by kurci2 on 2011-01-01
so that's it...
there is no way i could use my wireless card in MONITOR MODE??

---

### Post by kurci2 on 2011-01-01
so that's it...
there is no way i could use my wireless card in MONITOR MODE??

sorry for so many posts... there was something wrong with my internet connection... =(

---

### Post by kurci2 on 2011-01-02
can than anyone tell my whitch USB WIRELESS CARD supports MONITOR MODE???
or witch manufacteurs are supported by b43 drivers??

---

### Post by SamuelBasilio on 2011-05-12
there is no way i could use my wireless card in MONITOR MODE?? [2]
i have the same question.

---

### Post by josephmills on 2011-05-12
if you still would like to give it a shot could we please post a ```
lspci -vnn | grep 14e4
``` thanks

---

### Post by josephmills on 2011-05-12
Is My Card Supported?

A fairly up-to-date list is kept here. At the time of writing this article, chipsets with the following PCI IDs are supported:

To determine the PCI ID of your wireless device under linux, enter:

```
lspci -vnn | grep 14e4
```
Supported VIDs table

PCI ID	       Driver	          Note
14e4:4311	 b43/wl	
14e4:4313	 2.6.33+
14e4:4315	 2.6.33+
14e4:4301	 b43legacy	 B
14e4:4306	 G
14e4:4320	 G
14e4:4307	b43	 G
14e4:4312	 G
14e4:4318	 G
14e4:4319	 G
14e4:4320	 G
14e4:5354	 G
If your device ID is NOT listed here, it means it is not supported by aircrack-ng at this time.

[b]IMPORTANT

Some chips are covered by both the “b43” and “wl” driver. If you have such device, you have to make sure you blacklist the “wl” driver before you utilize b43, otherwise they will collide and your card will stop functioning altogether, let alone hope for injection. The “wl” driver does not support aircrack-ng.
[/b]
Installing the drivers

2.6.24 kernels and newer don't need any patches applied to the driver itself for monitor mode and packet injection. The only patch that is needed (for fragmentation attack support) is the standard mac80211 frag+ack patch.

Important note: If you install or update your b43 driver via compat-wireless, you have to know that the b43/ssb modules are part of your distribution's initramfs image. To avoid problems with loading your new b43 driver, update your initramfs image to complete the process. To do so, simply run:

sudo update-initramfs -u
If you have a card with the 14e4:4315 PCI ID and a kernel lower than 2.6.33, you need to install the compat-wireless package, since today's stable versions of the drivers do not support this card at all. In fact, the b43 driver is constantly being improved and using the development version of it can yield very positive results for all its users. More on this particular card here.

Installing the firmware

Because of Broadcom's licensing, the firmware - which is essential for the card to run - cannot be freely distributed and is obtainable only by “extracting” their proprietary driver. In order to do this, a program called b43-fwcutter is needed. The procedure varies depending on the kernel and driver versions used, but is generally pretty simple. Keep in mind that you also need to apply different steps if you have the card with the 14e4:4315 PCI ID. A very good description containing detailed steps is provided by the wireless-kernel wiki (scroll down to see the actual steps).

Keep in mind that your distribution might offer its own b43-fwcutter package and scripts intended to obtain and extract the firmware. It is up to you if you're going to do it manually or let your distro do the work. If you have the card with the 14e4:4315 PCI ID, you have no choice and have to do everything by yourself.

Testing the new module

After building and installing the new module, it is best to test that injection is working correctly. Use the injection test to confirm your card can inject.

Troubleshooting Tips

Confirm you are running the new module

First, double check that you are in fact running the new module:

 modinfo b43
 modinfo b43legacy
It will give you the fully qualified file name. Do “ls -l <fully qualified file name>” and confirm it has the date/time of when you compiled and installed the new module. If it does not match, then you are not running the patched module. This would, of course, need to be fixed.

This thread has a number of potential fixes to problems you may encounter: Broadcom bcm43xx Injection

"SET failed on device wlan0: Device or resource busy" when setting monitor mode

This is a known issue with all mac80211 drivers. To avoid this error, make sure you do:

 ifconfig wlan0 down
 iwconfig wlan0 mode monitor
 ifconfig wlan0 up
Or:

 airmon-ng start wlan0
This way, you can monitor on mon0 while still being associated on wlan0.

Why do I get ioctl(SIOCGIFINDEX) failed ?

If you get error messages similar to:

Error message: “SIOCSIFFLAGS : No such file or directory”
Error message: “ioctl(SIOCGIFINDEX) failed: No such device”
Then See this FAQ entry and scroll up to see the “Installing the firmware” section of this article.

Ubuntu 9.10 support

See this forum entry: [http://forum.aircrack-ng.org/index.php?topic=6434.0](http://forum.aircrack-ng.org/index.php?topic=6434.0)

---

