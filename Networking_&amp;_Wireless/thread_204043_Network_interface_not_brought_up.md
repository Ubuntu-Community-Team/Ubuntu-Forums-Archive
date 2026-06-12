---
title: "Network interface not brought up"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by TD-Linux on 2006-06-26
I just upgraded Kubuntu Breezy to Dapper without a problem. Until I restarted, that is.

The startup screen dosen't show 'Waiting for network to come up...' like it used to. In fact, the Connection light on my switch dosen't even come on! ifconfig gives me Link enccap:Local Loopback and everything seems set to loopback :(

I can't use any graphical tools, because the upgrade also hosed my ATI proprietary drivers. I'll ignore that for now.

---

### Post by ashrack on 2006-06-26
[QUOTE=TD-Linux]I just upgraded Kubuntu Breezy to Dapper without a problem. Until I restarted, that is.

The startup screen dosen't show 'Waiting for network to come up...' like it used to. In fact, the Connection light on my switch dosen't even come on! ifconfig gives me Link enccap:Local Loopback and everything seems set to loopback :([/QUOTE]
try doing
'sudo ifconfig eth0 up'

> I can't use any graphical tools, because the upgrade also hosed my ATI proprietary drivers. I'll ignore that for now.

just change in 'xorg.conf' the driver from FGLRX to RADEON

---

### Post by TD-Linux on 2006-06-26
Okay, I tried 'sudo ifconfig eth0 up', but it said that no device by eth0 exists. I did a 'ls | grep eth' and found that there were no ethernet devices listed at all!
It worked just perfect (I didn't have to do anything at all to make it work) in Breezy!
It's the built-in Gigabit Ethernet adapter (only connected to 100M network tho), on a Intel 925XE motherboard. (Yes, a real Intel brand motherboard, with an Intel chipset, of course)

BTW, haven't tried the xorg.conf thing, but I think I can make the proprietary drivers work by downloading the newest driver from ATI and seeing if that is compatable with X.org 7.0.0. The one on my HDD isn't. I can't test that yet, as my network is down and I can't download it :(

---

### Post by ashrack on 2006-06-27
For ATI, why dont U just install the drivers in the REPO?? 
Much less work.

For ETH0 what does 'sudo lspci -v' show?

And also please copy paste the content of:
'/etc/network/interfaces'

---

### Post by nzruss on 2006-06-27
excuse me, i'm new (noob)

*I did a 'ls | grep eth' and found that there were no ethernet devices listed at all!*

Maybe try ```
lshw -C network 
```

"ls" will only list the files/folders in the current directory (you could an '-r' for recursive i think)

---

### Post by TD-Linux on 2006-06-27
The repo drivers don't work for me, and from what I hear are broken for all Dapper users, as they aren't compatable with X.org 7.0.0. (Or that's what I gather...)

'sudo lspci -v' showed my Marvell Technology Group Ltd. 88E8050 Gigabit Ethernet Controller just fine, and I saw nothing wrong with it. Unfortunately, I forgot to copy it over here. If you need it, I can go back and get it.

/etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp
```

Nothing seems wrong there.

However, 'lshw -C network' gave me some important info. Besides displaying most of the same stuff that 'lspci -v' did, it displayed a very important message:
*-network DISABLED

How do I fix that, and get networking to work on each boot?

---

### Post by ashrack on 2006-06-28
[QUOTE=TD-Linux]The repo drivers don't work for me, and from what I hear are broken for all Dapper users, as they aren't compatable with X.org 7.0.0. (Or that's what I gather...)[/QUOTE]
The repo drivers are almost the same as ATIs drivers.  And the latest driver is X.org 7 compatible.
But if U have a custom build kernel then U must use the ATIs drivers's since the ones from repo have a huge bug that wont allow them to compile. Its a bug report older than 3months but DEV still arent doing anything about it.

> 'sudo lspci -v' showed my Marvell Technology Group Ltd. 88E8050 Gigabit Ethernet Controller just fine, and I saw nothing wrong with it. Unfortunately, I forgot to copy it over here. If you need it, I can go back and get it.

/etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp
```

Nothing seems wrong there.

However, 'lshw -C network' gave me some important info. Besides displaying most of the same stuff that 'lspci -v' did, it displayed a very important message:
*-network DISABLED

How do I fix that, and get networking to work on each boot?
am sorry but Ive run out of ideas.

ps. Are U running a custom kernel or a DAPPER one???

---

### Post by TD-Linux on 2006-06-28
Thanks for the help. I haven't gotten it to work any farther yet. I'm using the standard Dapper kernel 2.6.15-25, though I added about 4 modules (shouldn't affect anything). Dapper is installed on an external USB drive, but that shouldn't make a difference.

Possibly the ATI drivers will work when I get a network connection and download the newest from the repository. Or, maybe I'll download the latest ATI ones. But I am fairly confident I can solve that one myself.

I'll wait another day or two on this thread, then I'll paste in every semi-important file I find to see if that attracts attention. Then, I'll file another bug report to make everyone happy ;)

BTW, maybe I could try installing the drivers for my adapter, if there is any. Where could I find a list of network adapters and their corresponding repository packages?

Edit #2: I just found an old thread about someone saying something about deactivating and reactivating the card. Maybe I could try that? How is it done?

---

### Post by TD-Linux on 2006-06-28
Yay! I got it working!
I just realized my problem was that my network adapter had decided to change to eth1 from eth0, probably because it was a full moon when I upgraded or something :/
That was easy enough to fix, I just modified /etc/network/interfaces to eth1 and it all works :)

---

### Post by ashrack on 2006-06-28
I thought U already checked ifconfig eth0 and ifconfig eth1

Glad to see U got it working.

---

### Post by ciscosurfer on 2006-08-23
QUICK NOTE:  I've used Ubuntu for a while now, and have never bothered to mess with the following problem b/c I was able to use a different NIC from the get-go / at the outset.  Hopefully some fellow Ubuntonians out there know how to make this right.

Perhaps I haven't read this thread correctly, and I'm glad TD-Linux got his card to work, but I'm having the same issue with my Marvell controller as well.  Both my eth0 and eth1 interfaces are "up" but only my eth0 (Realtek) interface functions.

I use an add-on card [Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)] to get my network up and running.  My Marvell on-board NIC doesn't seem to work at all (have tried various options, to no avail).  My Marvell info is: Marvell Technology Group Ltd. 88E8050 Gigabit Ethernet Controller (rev 17).  When I issue```
sudo lshw -C network
```it tells me the driver for my Gigabit Ethernet Controller is driver=sky2 (for my Realtek, it's driver=8139too, and it works just fine).  I will 'modprobe' the sky2 driver, but it still fails.  Any help here would be much appreciated!

I've gone to the Marvell site in the hopes of downloading a new driver to fix this issue, but I don't know which one to pick (if any) b/c the options are for "Linux - 2.6 -- Fedora" and "Linux Kernel 2.4.13 and up" but these give me USB options and that won't work b/c it's not USB (or will they, am I missing something?)
If someone knows how to remedy this situation, that would be great.  In the meantime, I will continue to use my add-on card and surf happily (but I would like my Gigabit to work).  

I know this post is all over the place.  I've tried to condense the info to exactly the crucial aspects of the problem.

So, if anyone knows a solution, I'd be eternally grateful! And you'll forever have a Gold Star in my book! :KS

---

### Post by riondluz on 2006-09-25
I have a toshiba satellite with the same Marvell card and sky2 drivers and the exact same problem. I'm pretty good at solving stuff, but was hoping others had come up with a fix for this. Can you provide the URL's to Marvell's website. Maybe i can create a derivative fix for this by rebuilding 
the latest driver. FWIW, my default ubuntu install is the 2.6.15 kernel and i am currently running a source-built 2.6.16 xen kernel. Both must have the same marvel drivers, cuz both blow chunks on connnectivity.
riondluz_at_gmail_dot_com

---

