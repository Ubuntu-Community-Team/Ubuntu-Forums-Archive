---
title: "broadcom drivers in Linux v. 2.6.17"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by sanchrts on 2006-06-19
I am a linux noob and was frankly amazed when ubuntu installed on my Dell Latitude X300 with no scary (for a non-coder!) error messages apart from the fact that, surprise surprise, my Dell Latitude X300's Truemobile 1450 card (4309 Broadcom) is not playing nicely...

I desperately want to banish Windows for good from my home (other computer is a Mac mini) and I was therefore happy to read on [slashdot]("http://linux.slashdot.org/linux/06/06/19/0138242.shtml") that the [new Linux is out ]("http://lkml.org/lkml/2006/6/17/125")and that it apparently includes Broadcom drivers.  

Not having installed anything or customised my ubuntu install I am happy to tinker with the "new Linux" (I assume this means a new kernel?) but was wondering if anyone here had tried the new version?  Also - cheeky question - I assume that the new kernel will automatically appear in Synaptics Package Manager so I can install it that way?

Will report back if it makes the Broadcom driver issue disappear...

regards
Rafael

---

### Post by ssam on 2006-06-19
dappers kernel already has the broadcom driver, as the developers backported it to the 2.6.15 kernel. it is the latest braodcom driver as of a few days before the dapper release.

in 2.6.17 the driver is included in the main kernel code, rather than distro developers having to patch it in.

putting 2.6.17 into dapper could cause problems. it is highly unlikely that it will be put into the repos so that you can get it through synaptic. it has been imported into the developement branch of ubuntu (edgy) which will be released in october.

if you can't wait until then, you could try building your self a 2.6.17 kernel. i expect there are some howtos around some where.

---

### Post by sanchrts on 2006-06-19
ssam

Many thanks for the explanation - I understand now that the Broadcom drivers are already in the 6.06 kernel.  

I have absolutely no idea how to build a kernel (am still figuring out the basics of linux) so will wait for stable releases!

thanks
Rafael

---

### Post by odysseus_nz on 2006-06-20
Broadcom is well covered off in the Wiki at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx).  My recommendation from experience with my Dell/Trumobile is that the kernel drivers are not yet ready so go with the ndiswrapper solution for now, works fine for me, especially with NetworkManager and KNetworkManager under Kubuntu.

John.

---

### Post by finite9 on 2006-06-20
I think the wiki is a bit of a mess at the moment.  It assumes that the user simply wants to get connected, i.e. wireless w/o encryption or using WEP, and that they are willing to use custom scripts that need to be manually run.  To get connected with WPA, which *everyone* should be doing, has not really been well documented.  I have managed, through trial and error, to get things working with ndiswrapper solution, but this doesn't interoperate with network manager.  I am extremely interested in getting the native driver working with WPA and network manager, so that I don't have to create custom scripts for ipup/ifdown, and although this seems possible, I cannot find any documentation on it, and despite this, it only seems to operate at 11Mbit, not 54Mbit, and that bug has existed since release.

Does anyone have a link to a forum thread or another wiki page that documents step for step how to get the native driver working with WPA and network manager nicely, so I can change from wireless to wired or from one AP to another (predefined) through network manager instead of dropping to a terminal?  I can live with 11Mbit at the moment, but really hope that bug gets fixed soon.

--finite9

---

### Post by eindgebruiker on 2006-06-29
[QUOTE=finite9]Does anyone have a link to a forum thread or another wiki page that documents step for step how to get the native driver working with WPA and network manager nicely, so I can change from wireless to wired or from one AP to another (predefined) through network manager instead of dropping to a terminal?  I can live with 11Mbit at the moment, but really hope that bug gets fixed soon.[/QUOTE]

Well, I got a Broadcom card working with ndiswrapper and network manager, at 54 Mbps. See [http://ubuntuforums.org/showthread.php?t=197706](http://ubuntuforums.org/showthread.php?t=197706)

I used the information at: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper) (1.1)
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

My steps were:
1. ndiswrapper with no security
2. ndiswrapper with WEP
3. ndiswrapper with WPA
4. ndiswrapper with network manager

For step 4 you need to remove the configuration done in the earlier steps as network manager takes care of this. See the wiki post for this.

Good luck,

Gaele

---

### Post by finite9 on 2006-07-13
Yeah, I now realise that wpasupplicant has no support (apparently) for the new bcm43xx driver anyway, so it's back to ndiswrapper for WPA.

---

### Post by krazyd on 2006-07-14
WPA does work with bcm43xx.

---

### Post by finite9 on 2006-07-14
not the wpasupplicant in the repositories though.  I've heard that version 0.5.0 does work, but it involves compiling it yourself.

---

