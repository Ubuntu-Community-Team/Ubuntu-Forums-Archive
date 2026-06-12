---
title: "WLAN problems with Easy Peasy (ubuntu 8.04) at Lenovo S10e"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by Kai loipon on 2009-04-06
Hi all,

I am a newbie in the world of linux and so far my experiences have been on the positive side. I Installed Ubuntu 8.10 at my desktop and haven't used windows since then.
That was until I bought a Lenovo S10e Netbook (which come with Windows XP Home Edition installed) and to which I decided to partition the hard drive and install Easy Peasy (looks like distribution of Ubuntu 8.04 for netbooks). All went down fine up to the point of trying to make the WLAN work. I HIT A WAll. I have spent hours trying to make it work following advice from forums dealing with the issue:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)
{even though I have not compilled ndiswrapper-after all is done I get that the driver is installed but no device found eventhough when I do 
lspci | grep Broadcom/ Corporation I get that it is a BCM4312 rev01; when doing lshw -C network at the configuration line I get latency=0}
I have also tried following this one:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312)
which I of course adopted to the BCM4312 rev01 in the neccesary step but at the last step I get something about the LSB headers. Also when I do 
ndiswrapper -l i get that the driver is installed but no device present.
Finally I followed [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old) using the bcm43xx driver for linux 2.6.25 or newer (mine is 2.6.28-eepc the distribution is easy peasy 1.0)but again no luck (before this I uninstalled ndiswrapper and removed from the blacklist bcm43xx and blacklist wl (i don't know how that got there). This method was recommended here: [http://ubuntuforums.org/showthread.php?t=765448](http://ubuntuforums.org/showthread.php?t=765448) Although this is one of the three versions described, my levels of frustration have mounted to the point that I am glad that I did not completely wipe out the Windows installation as the WLAN works seamlessly with it. 
Please I have foun dvery little about Lenovo S10e Ubuntu installation (in English) and I don't want to resort to using GPARTED to remove Linux

Thanks in advance

---

### Post by mastery82 on 2009-10-12
Did you manage to find a solution about this?

---

