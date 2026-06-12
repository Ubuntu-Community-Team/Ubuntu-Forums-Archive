---
title: "Solution to Broadcom 43xx Card Problem (12.10 - Quantal Quetzal)"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by Sef on 2010-10-24
Problem in Precise Pangolin 12.04 with the Broadband 43xx Wireless Card: Unable to download firmware for wireless. (Also works for 11.10, 11.04, 10.10 and 10.04)

From the 'Additional Drivers' section:

> This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.Possible Solutions:

**Solution 1:** After installing with the alternate cd, I needed a cable and after updating, I was able to download the STA driver through the 'Additional Drivers' section.

**Solution 2: **Another option is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").

**Solution 3**: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close (This has been removed starting with 11.10 - Oneiric Ocelot. It may be installed with the Ubuntu Software Manager.)

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This solution fixed this problem on my Dell Inspiron 1545 with a Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01))

Note: For 12.04 and earlier models, the original postings are [here]("http://ubuntuforums.org/showthread.php?t=1604868&page=63").

---

### Post by dm_research on 2012-11-18
Hi,

I recently updated my 11 year old daughter's laptop (a hand-me-down Dell Inspiron 1501 she uses to help with her schoolwork) from lubuntu 12.04 to lubuntu 12.10.

Everything seemed to go OK except wifi no longer works.

Previously, I believe I needed to blacklist the ssb and b44 drivers and to enable the b43 driver, to match her wifi-only usage pattern. I recall seeing a post somewhere that said there was some sort of incompatibility between the b43 and (ssb+b44) combination - they should not be loaded in the same session. In any case, it worked in lubuntu 12.04 :)

After the lubuntu upgrade, there seems to be a link now between b43 and ssb. See example session below, where you can see that there is a new ssb_hcd driver that seems to be needed for b43, but it also brings the full ssb along too :(

```
$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  1 ssb_hcd

$ sudo modprobe -r ssb_hcd

$ lsmod | grep ssb

$ sudo modprobe b43

$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  2 ssb_hcd,b43

$ sudo modprobe -r b43
$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  1 ssb_hcd

$ sudo modprobe -r ssb_hcd
$ sudo modprobe -r ssb
$ sudo modprobe b43

$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  2 ssb_hcd,b43
```


Here is the output of sudo lsh -C network (with b43 and b44 enabled)

```
$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:d0200000-d0203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:d0300000-d0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:35:be:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.5.0-18-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg
```

Note that the last > DISABLED block disappears if b43 is not enabled. The first block mentions b43-pci-bridge which is not recognised by modprobe. Interestingly, the last block has a serial that looks like a MAC address (of the Broadcom BCM4311 card?), the first one does not. Perhaps some combination of these blocks would be enough to get it working, but I've had no success so far with this.

I have noticed the wifi indicator light on the laptop case flash on briefly (< 1 second) when the laptop boots up.

I should mention the laptop has an F2 hotkey, which in its past Windows XP life, caused wifi to toggle on/off, but lubuntu does not seem to recognise it.

If I could get it to boot with wifi enabled, that would be great. As administrator, I am happy to enable a wired connection if necessary, but for obvious reasons I would prefer not to give extra privileges (e.g., to run modprobe) to my daughter.

I would be very grateful for any advice on how to resolve the issue- I have spent several fruitless hours trying various 'fixes' suggested in this and other forums :confused:

---

### Post by HunkirDowne on 2012-11-18
Before either of us get too excited, I have not yet upgraded from Precise and have a different network card.  That said, here is a bit of (somewhat) useful information that I've found so far today.

Impatient Executive version:
Try installing the Broadcom-STA driver (wl) via these instructions:
[HTML]<a href="http://wiki.debian.org/wl"> Debian Wiki on WiFi using Broadcom driver </a>[/HTML]

OK, let's hope you're not too impatient just in case I'm wrong about the above.

More Detailed version:

Reference 1: [HTML]<a href="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers"> Reference 1 </a>[/HTML]
Reference 2: [HTML]<a href="https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010"> Reference 2 </a>[/HTML]

According to the Ubuntu Docs (Reference 1) you (BCM4311) and I (BCM4312) should be using the 'wl' driver which *does* instruct the blacklisting of ssb and others, as I recall.  I say this because I'm currently using a different driver but I've used the 'wl' (broadcom-sta) driver in the past with great success.  But somewhere I got steered away from it on this card because it is one of the 'low power' cards.

Care to share your lspci information?  Here's mine:

```
$ lspci -vvnn|grep 14e4
```
yields:
```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

For me, the "LP-PHY" means (from some source) that I should use the following (from dpkg):
b43-fwcutter					install
firmware-b43-lpphy-installer			install

This is in agreement with what I found earlier in the thread (actually, the original post):
"Had the same problem, then I noticed that instead of firmware-b43-installer I had to install (manually, via synaptic) firmware-b43-lpphy-installer."  --Kontza in LaunchPad.
[HTML]<a href="https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010" Ref 2 </a>[/HTML] (Reference 2)

But also see (again, from the original post):
[HTML]<a href="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers" Ref 1 </a>[/HTML] (Reference 1)

I think our situations are sufficiently different that what I'm currently using is not your solution despite Mr. Konza's expert advice (which applies to me).  I am much more familiar with the Debian advice as that is what I've used in the past for some really old hardware using a PCMCIA wifi card (Linksys, I think, but a Broadcom chipset nonetheless).

Care to share what you've tried that hasn't worked?

General comment: This thread started over two years ago.  62 pages is quite a lot and I won't read all of them unless I'm stuck on an elevator and the rest of the Internet is down.  :^)


> **dm_research said:**
> Hi,

I recently updated my 11 year old daughter's laptop (a hand-me-down Dell Inspiron 1501 she uses to help with her schoolwork) from lubuntu 12.04 to lubuntu 12.10.

Everything seemed to go OK except wifi no longer works.

Previously, I believe I needed to blacklist the ssb and b44 drivers and to enable the b43 driver, to match her wifi-only usage pattern. I recall seeing a post somewhere that said there was some sort of incompatibility between the b43 and (ssb+b44) combination - they should not be loaded in the same session. In any case, it worked in lubuntu 12.04 :)

After the lubuntu upgrade, there seems to be a link now between b43 and ssb. See example session below, where you can see that there is a new ssb_hcd driver that seems to be needed for b43, but it also brings the full ssb along too :(

```
$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  1 ssb_hcd

$ sudo modprobe -r ssb_hcd

$ lsmod | grep ssb

$ sudo modprobe b43

$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  2 ssb_hcd,b43

$ sudo modprobe -r b43
$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  1 ssb_hcd

$ sudo modprobe -r ssb_hcd
$ sudo modprobe -r ssb
$ sudo modprobe b43

$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  2 ssb_hcd,b43
```


Here is the output of sudo lsh -C network (with b43 and b44 enabled)

```
$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:d0200000-d0203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:d0300000-d0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:35:be:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.5.0-18-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg
```

Note that the last  block disappears if b43 is not enabled. The first block mentions b43-pci-bridge which is not recognised by modprobe. Interestingly, the last block has a serial that looks like a MAC address (of the Broadcom BCM4311 card?), the first one does not. Perhaps some combination of these blocks would be enough to get it working, but I've had no success so far with this.

I have noticed the wifi indicator light on the laptop case flash on briefly (< 1 second) when the laptop boots up.

I should mention the laptop has an F2 hotkey, which in its past Windows XP life, caused wifi to toggle on/off, but lubuntu does not seem to recognise it.

If I could get it to boot with wifi enabled, that would be great. As administrator, I am happy to enable a wired connection if necessary, but for obvious reasons I would prefer not to give extra privileges (e.g., to run modprobe) to my daughter.

I would be very grateful for any advice on how to resolve the issue- I have spent several fruitless hours trying various 'fixes' suggested in this and other forums :confused:

---

### Post by dm_research on 2012-11-19
Thanks @HunkirDowne!

I will take a look again at those references and will report back.

I did look at them before (when I installed 12.04) but I think I reverted to the b43 driver at the time (can't remember the reason why...).

However, it is possible that the Broadcom wl driver would work with 12.10 - definitely worth a try :)

Thank you.

---

### Post by dm_research on 2012-11-22
Unfortunately, the problem is still there...

Firstly, here is the output of lspci, as requested by @HunkirDowne:

```
$ sudo lspci -vvnn | grep 14e4
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

```

As you can see, there is no reference to LPPHY (so I did not follow the rest of @HunkirDowne's suggestions). 

I followed the advice in one of the suggested references
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)
in particular the "STA - Internet Access" > "11.10 (Oneiric Ocelot) - 12.10 (Quantal Quetzal)".

Because b44 depends on ssb, I needed to add that to the modprobe -r line.

When wl is enabled, it seems to bring in ssb and b44 :(

```
$ sudo modprobe -r b43 b44 ssb wl
$ sudo lsmod | grep ssb
$ sudo modprobe wl
$ sudo lsmod | grep ssb
ssb                    50087  1 b44

```

I found the webpage that suggested that the ssb driver is not compatible with wl:

> [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

On that page, there is a section "Remove any other drivers for the Broadcom wireless device." which mentions b43, ssb, etc. The recommended approach is to rmmod the incompatible drivers. I tried this, ran modprobe wl again and, you guessed it, they were back in the list of modules returned by lsmod!

The other thing I tried was to add the problematic drivers (b43 b44 ssb, etc) to /etc/modprobe.d/blacklist.conf and rebooted. Again, the b44, ssb and wl modules were loaded.

Then I thought that maybe there is an explicit reload of these modules that happens after processing the blacklist file. I checked /etc/modules and the only uncommented line was
> lp

which I assume enables printing, but seems to be "safe".

At the moment, I am beginning to suspect there is a bug somewhere in the wifi setup in 12.10 - it probably does not help that both cards are Broadcom and may share driver features. I would have given up long ago if I did not know that wifi *was working* in 12.04 and I am reasonably certain that the "fix" involved 'disabling' b44 and ssb.

Lastly, if it helps understanding, to access the internet when both Broadcom cards are inoperable, I use a tethered 3G connection (to check advice pages), but that's not a practical solution in the long term given the intended use of the laptop.

> **dm_research said:**
> Thanks @HunkirDowne!

I will take a look again at those references and will report back.

I did look at them before (when I installed 12.04) but I think I reverted to the b43 driver at the time (can't remember the reason why...).

However, it is possible that the Broadcom wl driver would work with 12.10 - definitely worth a try :)

Thank you.

---

### Post by Simm2 on 2012-11-29
I have got the same problem with 12.10.
To note : during installation of 12.10, and for some time after installation, Wifi worked nicely. It seems to me that it stopped working after a kernel update (3.5.0-18, a second update 3.5.0-19 did not improve anything wrt this problem).

---

### Post by rsavage on 2012-11-30
> **dm_research said:**
>  When wl is enabled, it seems to bring in ssb and b44 :(
 
```
$ sudo modprobe -r b43 b44 ssb wl
$ sudo lsmod | grep ssb
$ sudo modprobe wl
$ sudo lsmod | grep ssb
ssb                    50087  1 b44

```
 
..... 
 
At the moment, I am beginning to suspect there is a bug somewhere in the wifi setup in 12.10 - it probably does not help that both cards are Broadcom and may share driver features. I would have given up long ago if I did not know that wifi *was working* in 12.04 and I am reasonably certain that the "fix" involved 'disabling' b44 and ssb.

 
If you have a b44 ethernet card then you have these lines in /etc/modprobe.d/blacklist-bcm43.conf
 
```

blacklist b44
install wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe --ignore-install b44

```
 
So when you modprobe wl, it automatically modprobes b44 too. Play around with this line and see if removing the "modprobe --ignore-install b44" fixes the problem. If it does then you need to raise a bug.
 
P.S. It is easy to miss new posts in sticky threads and this is why they sometimes don't get replies. It is much better to create a new thread with your problem. Then people with the same problem can easily find it, rather than wading through a 63 page thread (and if you want to be super helpful, update the community wiki page!).

---

### Post by Simm2 on 2012-12-01
Thanks to **Sef** for creating this new thread for Quantal Qetzal.

On the french Ubuntu forum, somebody claimed that the problem - which apparently came along with a kernel update 3.5.0-18 - could be solved by installing kernel 3.6.
Did anybody try that ?

---

### Post by nas123 on 2012-12-01
3.6 didn't solve it.

It seems the install uses wl0 and works just fine but when installed its trying to use brcmsmac and it just doesn't work for me.

---

### Post by nas123 on 2012-12-01
To confirm I had to install dkms and bcmwl-kernel-source and wireless is fine.

Now just to sort out my Atheros driver ...alx is it ?

---

### Post by rioguia on 2012-12-03
Reposted as new thread / accidentally posted to a sticky thread

---

### Post by T C on 2012-12-29
Hello,

I am also having wifi problems. I am using Broadcom BCM4312. With Ubuntu 10, everything worked fine, but today I upgraded to Ubuntu 12 and wifi doesn't work.

I'm trying my best to follow the advice in this thread, but I'm still an Ubuntu novice, so I'm not sure I'm doing things right. In particular, there are places where the instructions say to install from the "restricted repository", and I don't know how to do that because the Ubuntu Software Center never asks me where to install from.

From what I've read, I believe I need the driver called "wl", which can be installed with the packages "bcmwl-kernel-source". The Ubuntu Software Center tells me that package is already installed. As long as it isn't blacklisted, wl should allow me to activate the "Broadcom STA wireless driver" through System Settings / Hardware / Additional Drivers. When I look through the blacklist file, I see no evidence that it is blacklisted. Nevertheless, when I try to activate Broadcom, I get an error saying "Sorry, installation of this driver failed". It refers to a log file, but I don't know how to interpret the log.

Can anyone tell me what step to try next?

-TC

---

### Post by Simm2 on 2012-12-31
The only way I got to solve the problem was to install kernel 3.7.0
I proceeded this way :
```
mkdir kernel3.7.0 && cd kernel3.7.0

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-headers-3.7.0-030700_3.7.0-030700.201212102335_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-headers-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-image-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-raring/linux-image-extra-3.7.0-030700-generic_3.7.0-030700.201212102335_amd64.deb

sudo dpkg -i *.deb

cd ..

rm -r kernel3.7.0
```
Note : this works only for a 64 bits computer.

---

### Post by T C on 2012-12-31
My problem was solved in a separate thread: [http://ubuntuforums.org/showthread.php?t=2100005](http://ubuntuforums.org/showthread.php?t=2100005)

---

### Post by nholloway2007 on 2013-01-24
Hi guys,

I just installed Lubuntu 12.10 Quantal on an old Dell Inspiron e1505. I have a Broadcom wireless card; I've installed b43-fwcutter, dkms, bcmwl-kernel-source, and the STA Linuxx driver, and still have no possible way to connect wirelessly. Any suggestions, guys?

---

### Post by wolfgentleman on 2013-01-28
I am having problems with linux mint 13 maya kde and my BCM4306 14e4:4324 card, I have a thread [HERE]("http://ubuntuforums.org/showthread.php?t=2109390").

---

### Post by ebola42 on 2013-01-29
how do you do that, ive tried and can't get it to work?

---

### Post by thesoothsayer on 2013-01-30
For me, the problem cropped up with BCM4313 after I installed the backport to support my Atheros R8161 LAN card.

What happened was that it was loading the old module for lib80211 and failing to load the newer lib80211_crypt* and wl modules after that.

I manually fixed it by rmmod the lib80211 module, and insmod the lib80211.ko from the backport directory, followed by the lib80211_crypt* modules from the same directory, and modprobe wl.

Question is how can I set it to automatically load the lib80211 module from my backport directory at /lib/modules/3.5.0-22-generic/kernel/net/wireless?

There's another existing /lib/modules/3.5.0-17-generic existing as well.

---

### Post by Hans-N on 2013-02-01
I have been having this problem as well.  I have a BCM4312, and followed the instructions in the first post.  It did not seem to work the first time, but it works if I run

```
sudo modprobe b43
```

Of course, I have to do this every time I start up.

I noticed that b43 was blacklisted in both the blacklist-bcm43.conf and blacklist-sta-common.conf files.  I commented them out (I think--put a # in front of them), but to no avail.  It does not seem to work without running the command each time I start up.  Any thoughts?

---

### Post by billwww on 2013-02-01
The Broadcom 43xx problem has apparently resurfaced. After a kernel update about a week ago, Broadcom BCM4313 quit working in12.04 on an Acer Aspire One 722-0879 (AMD processor). There is a bug report #1110139 that reports these symptoms:

The wifi card searches for a network without ever finding it even though it reports a connection. 2 most recent kernel updates do not fix the problem. My temporary solution is to connect a usb wifi card and disconnect the Broadcom reported connection as soon as the added card connects. This is cumbersome.

I hope there is a fix soon.

---

### Post by billwww on 2013-02-05
I waited for one new kernel (they're coming often these days), but when that didn't help, I followed the procedure linked to in TC's reply (#14 above). That seems to have worked for my BCM4313 card in an Acer Aspire One 722.

I'm happy for now, but updates shouldn't break working drivers.

---

### Post by billwww on 2013-02-05
I spoke too soon. When I booted ubuntu (12.04) the next time, the same symptoms were back (network shows connected in list but browser reports no connection; wireless icon shows continuous scanning). I tried doing just a modprobe wl: that didn't work. I then ran the reconfiguration followed by another modprobe wl, but that no longer fixed the problem even once.

So . . . Try other fixes? Wait for another kernel update? Upgrade? (though 12.10 seems fraught with the same problems).

---

### Post by sushi80 on 2013-02-14
My wifi also suddenly stop to work

I have a new Lenovo G580 with  Broadcom 4313
Last week i've installed 12.10, update the os using wifi (i don't use lan) and no problem (maybe had some intermittent problems but i was able to stream and download)
On Tuesday 12th Feb I've received some update (i think there was the kernel) and my wifi was gone!
Was keep trying to connect but failing every time. i got connected just few times to my AP but i wasn't able to browse internet

I've tried different things but i'm stuck now...

---

### Post by Camilo Cienfuegos on 2013-02-14
> **sushi80 said:**
> My wifi also suddenly stop to work

I have a new Lenovo G580 with  Broadcom 4313
Last week i've installed 12.10, update the os using wifi (i don't use lan) and no problem (maybe had some intermittent problems but i was able to stream and download)
On Tuesday 12th Feb I've received some update (i think there was the kernel) and my wifi was gone!
Was keep trying to connect but failing every time. i got connected just few times to my AP but i wasn't able to browse internet

I've tried different things but i'm stuck now...

Hi I had similar problem possibly related to this one, although I am running 12.04.2. The network manager totally bummed after the update, couldn't get any connections.

Try looking in the archives directory:
```
ls -r /var/cache/apt/archives
```I found the old driver in there for my system (for me it was called bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_i386.deb it might be similar for you). I then reinstalled this package using "sudo dpkg -i <drivername.deb>"

After a restart the connections worked perfectly as they did before.  Still trying to figure out what exactly went wrong though.

---

### Post by sushi80 on 2013-02-14
i can't find any driver in there!!  :(

i opened a new tred for my problem
[http://ubuntuforums.org/showthread.php?t=2116035](http://ubuntuforums.org/showthread.php?t=2116035)

---

### Post by arashiko28 on 2013-03-05
I have solved the problem halfway... every post works... halfway... every time I shutdown or reboot the laptop, the wifi is off and the button does not work. I have to open menu> preferences> software sources> additional drivers and choose to not to use the drivers and then choose the drivers again...
It is tiresome to have to do this every time I turn on my laptop.

This is an Acer Aspire One netbook D250
I have installed Lubuntu 12.10

> Aspire-one:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)


>  lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)


---

### Post by ATW136 on 2013-03-19
Linux Newbie

Xubuntu Desktop 12.10 via downloaded ISO.

This morning's software updates (3/19/13) included an update for the Linux Kernel to 3.5.0-26. After installing, my WPA2-PSK Wifi no longer worked.

I fixed the problem using the steps below and am posting since it might help others. Because the problem is likely to happen again (see the reason why below), I have asked a question at the end about whether or not there is an even better way to fix the problem.

What I Discovered
As I went through each step of Gnusci's guidelines for information needed to provide answers, I discovered that there were
no differences in the requested information for the installations for the two kernels.  The details are:

PC
Dell Mini 1011

$ lspci -nn | grep '14e4'
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:c4:3b:88  
          inet addr:192.168.100.9  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fec4:3b88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40291 (40.2 KB)  TX bytes:12398 (12.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:26:5e:10:ee:74  
          inet addr:192.168.100.7  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe10:ee74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:99
          TX packets:68 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19684 (19.6 KB)  TX bytes:15009 (15.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8296 (8.2 KB)  TX bytes:8296 (8.2 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:223  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

$ lsmod | grep "wl"
wl                   2442880  0 
lib80211               14041  2 lib80211_crypt_tkip,wl

$ dmesg | grep "wl"
[   23.790688] wl: module license 'MIXED/Proprietary' taints kernel.

$ dmesg | grep "Broadcom"
[   23.803618] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.112

$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:10:ee:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 ip=192.168.100.7 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:c4:3b:88
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.100.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

$ lsb_release -d
Description:    Ubuntu 12.10

$ uname -mr
3.5.0-26-generic i686 (32 bit)  Previous kernel was 3.5.0-25-generic i686

$ sudo /etc/init.d/networking restart
I got error messages with this and after googling replaced with "sudo service networking restart".  It didn't do anything and later discovered that a working wifi would stop working after running the command.

What I Did
I had gotten this network card to work previously following the WifiDocs/Driver/bcm43xx wiki instructions for the wl module by installing the bcmwl-kernel-source as described for 12.10. I decided to repeat the steps to try to resolve the problem.  The dialog said that it recompiled against the new kernel... and it worked!!  The previous kernel, 3.5.0-25, no longer works but I can live with that.

Now, my question: 
The .../bcm43xx instructions also indicate that a 4312 LP-PHY controller should be updated using these instructions:
" or, if you need a LP-PHY version (e.g BCM4312), use:
sudo apt-get install firmware-b43-lpphy-installer"

That sounds like a permanent solution (I am assuming that it means no more reinstalls as updated kernels are released.).  But, if I do that update, will I still be able to dual-boot this machine with Windows and Wifi or will the update restrict me to Ubuntu only?

Thanks.

---

### Post by Silverflyer on 2013-03-24
Do any of the fixes listed here work on 12.04?

---

### Post by zafar142003 on 2013-04-07
> **HunkirDowne said:**
> Before either of us get too excited, I have not yet upgraded from Precise and have a different network card.  That said, here is a bit of (somewhat) useful information that I've found so far today.

Impatient Executive version:
Try installing the Broadcom-STA driver (wl) via these instructions:
[HTML]<a href="http://wiki.debian.org/wl"> Debian Wiki on WiFi using Broadcom driver </a>[/HTML]

OK, let's hope you're not too impatient just in case I'm wrong about the above.

More Detailed version:

Reference 1: [HTML]<a href="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers"> Reference 1 </a>[/HTML]
Reference 2: [HTML]<a href="https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010"> Reference 2 </a>[/HTML]

According to the Ubuntu Docs (Reference 1) you (BCM4311) and I (BCM4312) should be using the 'wl' driver which *does* instruct the blacklisting of ssb and others, as I recall.  I say this because I'm currently using a different driver but I've used the 'wl' (broadcom-sta) driver in the past with great success.  But somewhere I got steered away from it on this card because it is one of the 'low power' cards.

Care to share your lspci information?  Here's mine:

```
$ lspci -vvnn|grep 14e4
```
yields:
```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

For me, the "LP-PHY" means (from some source) that I should use the following (from dpkg):
b43-fwcutter                    install
firmware-b43-lpphy-installer            install

This is in agreement with what I found earlier in the thread (actually, the original post):
"Had the same problem, then I noticed that instead of firmware-b43-installer I had to install (manually, via synaptic) firmware-b43-lpphy-installer."  --Kontza in LaunchPad.
[HTML]<a href="https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010" Ref 2 </a>[/HTML] (Reference 2)

But also see (again, from the original post):
[HTML]<a href="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers" Ref 1 </a>[/HTML] (Reference 1)

I think our situations are sufficiently different that what I'm currently using is not your solution despite Mr. Konza's expert advice (which applies to me).  I am much more familiar with the Debian advice as that is what I've used in the past for some really old hardware using a PCMCIA wifi card (Linksys, I think, but a Broadcom chipset nonetheless).

Care to share what you've tried that hasn't worked?

General comment: This thread started over two years ago.  62 pages is quite a lot and I won't read all of them unless I'm stuck on an elevator and the rest of the Internet is down.  :^)

I agree with HunkirDowne. I had Ubuntu 12.04 and Broadcom STA driver (with BC4312 lp-phy card) installed. After a kernel update the Wifi refused to connect to scanned networks. After reading his advice, I unistalled the STA driver (from the 'additional drivers' section) and installed firmware-b43-lpphy-installer from synaptic. This solved the problem and wifi works as before. Thanks HukirDowne.

---

### Post by md_shafiq_sumon on 2013-09-17
Every body thank for the question and answer.

---

