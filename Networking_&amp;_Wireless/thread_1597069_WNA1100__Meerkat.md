---
title: "WNA1100 : Meerkat"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by marcagio on 2010-10-14
Netgear WNA1100 , 

Fresh Ubuntu 10.10 install.

I have installed everything required...

I have somehow found out on other forums that I needed to get ath9k_htc running in order to get the wireless working. sudo modprobe ath9k_htc did get everything to show up in my lsmod...

No lights on the device comes on and no access to wireless..

although the card appears in lsusb as shown : 

[I]marilyn@Patate:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 05ac:020c Apple, Inc. Extended Keyboard [Mitsumi]
Bus 004 Device 002: ID 05ac:1003 Apple, Inc. Hub in Pro Keyboard [Mitsumi, A1048]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15d9:0a33 Trust International B.V. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
[COLOR="DarkRed"]Bus 001 Device 004: ID 0846:9030 NetGear, Inc.[/COLOR] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

And the ath9k_htc is running in lsmod (lsmod | grep ath*):

[I]marilyn@Patate:~$ lsmod | grep ath*
ath9k_htc              40674  0 
ath9k_common            5982  1 ath9k_htc
ath9k_hw              292297  2 ath9k_htc,ath9k_common
mac80211              231541  2 ath9k_htc,ath9k_common
ath                     8153  2 ath9k_htc,ath9k_hw
cfg80211              144470  4 ath9k_htc,ath9k_common,mac80211,ath
led_class               2633  1 ath9k_htc[/I]

I have read on [http://wireless.kernel.org](http://wireless.kernel.org) that compat-wireless has the drivers required were included in the latest package... So i have installed the linux-backports-modules-wireless-lucid-generic using apt-get...

Now i'm totally lost and confused... I usualy find my way out reading in the forums but this time, i feel like this is getting nowhere... I have been trying to get it working for 2 nights and have slept about 3 hours last night and the night before just to get this going for my girlfriend... can anybody help? PLEAAAASE!!!! (ndiswrapper did not seem like a good idea for most of the ppl I read that have tried with the same device BTW)

---

### Post by Messier 66 on 2010-10-15
Hi 
this worked for me, hope it do for you too.
[URL="http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100"] 

:guitar:

---

### Post by walt.smith1960 on 2010-10-15
Perhaps have a look at this:
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)
I haven't tried with 10.10 but it worked nicely in 10.04. I've only just installed this but it's simple to install and made my WNA1100's blue light come on ;). I can connect with WPA and don't see any big problems.  The only potential glitch I've seen is an unwillingness to wake up from suspend.  I searched on that problem and found a fix but haven't done enough suspend/un-suspend cycles to judge the fix effectiveness.

Edit-- I installed Meerkat and this package will not install.  The Atheros package already exists as part of the kernel.  The WNA1100 does not become active when booting Maverick.  I enabled wireless backports and that didn't help.  The adapter is working fine in Lucid with the package installed.  I was able to edit etc/modules and add the line "ath9k_htc" to the file.  If I then reboot ath9k appears a few places in "lsmod"  Still no blue light in meerkat.

---

### Post by marcagio on 2010-10-15
> **Messier 66 said:**
> Hi 
this worked for me, hope it do for you too.
[URL="http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100"] 

:guitar:

Does not work with 10.10, tried many times.

---

### Post by Messier 66 on 2010-10-15
> **marcagio said:**
> Does not work with 10.10, tried many times.

Weird, I made a fresh 10.10 install just yesterday, followed the tutorial as it is and it worked. Are you doing everything the tutorial say you must do? Are you installing the firmware? What version of compat-wireless are you using? (I got it working with compat-wireless-2010-10-10).Did you modprobe ath9k_htc?

---

### Post by scullr on 2010-10-16
I'm trying to install ath9k_htc into a freshly installed 10.10.  I keep getting this message:  An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related. tasks.  Please report the error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

I also have problem downloading and installing certain files under Update Manager."

Are there plans to fix aptdaemon ??

---

### Post by aniruddha on 2010-10-17
Hey, I am having the same problem as the previous poster. I'm attaching the screenshot of the error I receive. This GUI problem used to work with Lucid. 

Any ideas?

---

### Post by walt.smith1960 on 2010-10-18
There are many reports of problems with NDIS GTK but I decided to take a chance.  I copied the Netgear drivers files from a WinXP install to a USB drive and booted into Maverick. I'm fortunate in that I have a warhorse G adapter that works on all Ubuntu versions & machines I've tried it on--Trendnet TEW424UB v3.1R.  It's slow but it works.  Downloaded NDISGTK via synaptic.  I then unplugged all WiFi adapters.  Started NDISGTK, pointed it at the .inf file and clicked 'install'. It completed and I could then see in network manager 'wireless networks' grayed out.  I plugged in the WNA1100 and it connected!!!! YAY!!!!.  

The signal strength meter shows a weaker signal than I get with the same adapter in Lucid using the ath_9k deb file found on source forge-90+% signal strength in Lucid or windows driver in windows vs. 70% signal strength using the NDISGTK installation.  However, 70% is better than 0%.  I still hope the NetgearWNA1100 will become as reliably "plug and play" as my TrendNet adapter is.  It doesn't appear to be there yet.

Edit:  Hmmm, I just checked connect speed 54 Mb/sec.  Ran a speed test and it does appear to be connecting at G speeds, not N speeds. Rats.  But it does still work. I think I'll continue to use Lucid as my primary O.S.

---

### Post by dps7215 on 2010-10-23
I am having the same issue.  All fixes for 9.10, and 10.04 tried.  I keep receiving the same error message when attempting to install the .deb file.
Help please, wife is going to cut my computer's umbilical cord soon!!!

---

