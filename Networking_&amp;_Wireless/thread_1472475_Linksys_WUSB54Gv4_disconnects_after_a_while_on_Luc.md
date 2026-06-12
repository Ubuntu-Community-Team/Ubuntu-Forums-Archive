---
title: "Linksys WUSB54Gv4 disconnects after a while on Lucid"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by meithan on 2010-05-04
**Solution**: This problem is fixed in the upcoming kernel, 2.6.34. You can either wait until Canonical releases the update, or download, build and install the 2.6.34 kernel manually. The instructions to do so are [HERE]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild"). It's fairly easy.

-----

I'm having a problem on Lucid (amd64) with a Linksys WUSB54Gv4 usb wifi adapter. 

After some time (varies between ~10 mins to a few hours), the connection is lost. However, in my case I can't connect back. It tries to establish the connection, then pops up the dialog asking for the WEP key again. It will do this repeatedly, not ever connecting back.

This is basically how the disconnect looks in dmesg:

> [ 2657.920014] phy0 -> rt2500usb_set_device_state: Error - Device failed to ente
r state 1 (-16).
[ 2658.120008] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
[ 2658.620152] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
[ 2659.820014] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
[ 2660.240014] phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
[ 2662.740011] No probe response from AP 00:1e:c7:27:2c:b1 after 500ms, disconnecting.

My temporary solution so far has been to manually unload and reload the rt2500usb module in the kernel:

> sudo modprobe -r rt2500usb
sudo modprobe rt2500usb

After that I can connect on the first retry.

I tried installing the linux-backports-modules-wireless-lucid-generic package, to no gain.

I'll try installing the rt2570usb or RT73 drivers later, see if that solves the issue.

Some more info:

> $ lsusb | grep Linksys
Bus 002 Device 004: ID 13b1:000d Linksys WUSB54G Wireless Adapter

```
$ lsmod | grep "rt.*usb"
rt2500usb              19014  0 
rt2x00usb              11243  1 rt2500usb
rt2x00lib              31500  2 rt2500usb,rt2x00usb
mac80211              243373  2 rt2x00usb,rt2x00lib
```

---

### Post by udippel on 2010-05-04
> **meithan said:**
> I'm having a problem on Lucid (amd64) with a Linksys WUSB54Gv4 usb wifi adapter. 

After some time (varies between ~10 mins to a few hours), the connection is lost. However, in my case I can't connect back. It tries to establish the connection, then pops up the dialog asking for the WEP key again. It will do this repeatedly, not ever connecting back.

My temporary solution so far has been to manually unload and reload the rt2500usb module in the kernel:


No need to fiddle with the modules. The archives of the last days are full of this. Maybe the differences are minor only: I have the same here with an Atheros card (ath5k). Let me take a guess: If you are the only user, and low transfer rate, you'll stay connected for eternity. Once you do a bulk transfer over the Linksys, you'll be out within less than a minute. Correct?

Uwe

---

### Post by meithan on 2010-05-04
Well, it seems more random than that in my case. I'm barely doing anything right now (browsing a few websites, chatting on Pidgin) and I'm getting disconnects. 

Is there any 'main' thread I should be looking at regarding this issue? I couldn't find a generic thread about it in the first few pages of the forum.

---

### Post by necromonger on 2010-05-04
I have the same problem.

---

### Post by necromonger on 2010-05-04
nothing on launchpad either.

---

### Post by meithan on 2010-05-04
If your wifi adapter is WUSB54G**C**, then the fix seems to be to blacklist the rt2500usb driver; see the following thread.

[http://ubuntuforums.org/showthread.php?p=9236202](http://ubuntuforums.org/showthread.php?p=9236202)

I haven't tried that for my adapter (which is WUSB54G - without the final C), because it has a different radio chip, but I guess trying that couldn't hurt too much (if it doesn't fix it, you can simply un-blacklist it).

---

### Post by necromonger on 2010-05-04
it is not a wusb 54gc, it is a wusb 54g ver 4.

---

### Post by necromonger on 2010-05-04
Please make this thread a sticky.

---

### Post by meithan on 2010-05-04
You have the same wifi adapter as me then, WUSB54G. 

Have you tried blacklisting the rt2500usb driver anyway, as indicated in the thread I linked?

---

### Post by necromonger on 2010-05-04
yes no luck.

---

### Post by necromonger on 2010-05-04
I have been searching for 2 hours and still nothing.Any one else?

---

### Post by udippel on 2010-05-04
> **necromonger said:**
> I have been searching for 2 hours and still nothing.Any one else?


If I knew, I'd have told you!

(I really suggest to make this sticky! It seems to be not only me, and not only on m0n0wall, as well as Tomato, and not only on ath5k; but on any (?) card; on a busy access point.

I suggest also, to stop this nonsense of blacklisting all our drivers. It can't help to blacklist the rt2500usb, ath5k, bcom, and whatnot. It is not the problem of a specific driver.

Uwe

---

### Post by necromonger on 2010-05-05
Yes I agree it is not a driver problem.There are a lot of posts with the same problem with different cards a sticky would be great!

---

### Post by meithan on 2010-05-05
I wouldn't say it's not a driver problem, even though it's affecting different ones. I'm not an expert. Blacklisting and trying other drivers can't hurt.

What we need is some official word on this issue. Maybe we should post a serious bug report, if there isn't one already?

Edit: Has anyone tried going back to a previous kernel? The Karmic one, for instance?

---

### Post by necromonger on 2010-05-05
I had to revert back to 9.10 to get my wireless working.It works flawless!

---

### Post by grumo on 2010-05-05
I'm not going to help much, but wanted to contribute with some feedback:

·Blacklisting the rt2500usb driver makes my wireless connection disappear completely (no available networks to connect to)

·Blacklisting the rt2800usb driver (as suggested for the WUSB54Gv4**C** model) driver makes no difference, or so it seems...

What I do (please excuse my neanderthal procedures, I've only been using Ubuntu for the past three weeks) is simply unplug the USB cord and plug it back in, instead of unloading/loading the modules, but that only fixes the problem temporarily.

What settings are you using to connect? just the WEP password or are you entering gateway/mask/IP/DNS settings as well? I've done the second...

> **meithan said:**
> 
I tried installing the linux-backports-modules-wireless-lucid-generic  package, to no gain.

I'll try installing the rt2570usb or RT73 drivers later, see if that  solves the issue.



backports modules were of no help to me either, please give us some feedback when you install the other drivers. I'll have a look in the Spanish language forums to see if there has been any luck.

---

### Post by udippel on 2010-05-05
> **meithan said:**
> I wouldn't say it's not a driver problem, even though it's affecting different ones. I'm not an expert. Blacklisting and trying other drivers can't hurt.

What we need is some official word on this issue. Maybe we should post a serious bug report, if there isn't one already?

Edit: Has anyone tried going back to a previous kernel? The Karmic one, for instance?

Since the 'connect-disconnect after some time' affects many people, with most different chipsets (ath, rtl, bcom, etc.) chances of a driver problem are low. There is no reason at all to blacklist drivers. There are thousands of drivers in the kernel, and at boot it loads the ones for which it finds hardware, and leaves the others untouched. Blacklisting is only for quite special and exceptional cases, when one doesn't want the kernel to load a specific driver for a specific hardware; for example because you want to load your own later.

Your second question is more more interesting. I have unfortunately removed the old kernel, but some may still have it lying around. Just boot to it, and check if this solves the problem.

Uwe

---

### Post by necromonger on 2010-05-06
I found this in the wiki.
 Version
	

Chipset
	

Driver
	

Supports network install?
	

Supported in installed system?
	

Works "out of the box"
	

Comments
	

Last Updated

(Ver.1)
	

Prism54
	

p54
	

Yes
	

Yes
	

Unknown
	

According to prism54.org, this card is supported by the p54 driver. It is unconfirmed whether this works in Ubuntu or not. Also reported to work well with ndiswrapper. See ndiswrapper's wiki entry
	

2010-03-13

(Ver.4)
	

Ralink
	

rt2500 / rt2570
	

Yes
	

Yes
	

Yes
	

Works "out of the box" in Karmic and Gutsy. Older systems: Works fine with WEP on 6.06/Breezy when installed, but hung at activating using LiveCD; works on 7.04/Feisty w/ WEP with manual config and roaming other connections. The Windows driver can be downloaded from linksys but not the version for Vista. Use ndiswrapper 1.9 to install driver then used > System > Administration > Network to configured this wireless device. Hardy: works with rt2570
	

2010-03-13 
nothing about lucid!

---

### Post by parmruss on 2010-05-07
I'm surprised you got farther than I have with this card on any kernel above 2.6.28. I've not been able to get this card to authenticate with WPA2 on any linux version using the newer kernels.

Here's some more links to explore:
[http://wireless.kernel.org/en/users/Drivers/p54/devices](http://wireless.kernel.org/en/users/Drivers/p54/devices)
[http://wireless.kernel.org/en/users/Drivers/p54](http://wireless.kernel.org/en/users/Drivers/p54)
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383)
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/472953](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/472953)
[http://wiki.debian.org/prism54#supported-p54usb](http://wiki.debian.org/prism54#supported-p54usb)
[http://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4](http://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4)
[http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB](http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB)
ubuntuforums.org/showthread.php?p=9027055#post9027055

---

### Post by necromonger on 2010-05-08
There are so many wireless problems with this release there might be a fix by next year.

---

### Post by meithan on 2010-05-09
There was an update for the Lucid kernel today, to 2.6.32-22-generic. The problem is still there.

---

### Post by meithan on 2010-05-11
People, it's time we try installing old kernels (from the 9.04 era) to see if they work better with our wireless. I don't have time to try it right now, but here are some kernels:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by ljerabek on 2010-05-16
This issue is a known bug and will be fixed in released in 2.6.34 of the kernel :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549585]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549585")

I have tried to get a patch made however the flags value "rt2x00dev->hw->wiphy->flags" is not valid for the 2.6.32-22 version of rt2500usb.c and headers. The compile fails because that value doesn't exist in the structure. I have asked for more information and I hope to hear back. If I get a reply on how to fix the issue I will post directions on how to get the code to compile.

It's a bit disappointing they broke something which was working. I switched to Lucid in hopes of better performance... on the flip side the OS if free so I can't complain.

---

### Post by meithan on 2010-05-18
Thanks for the info, ljerabek. Looking at [http://www.kernel.org/](http://www.kernel.org/), it seems the 2.6.34 kernel has just been released (May 16th), but it hasn't been marked for update by Canonical. I wonder how long will it take the Ubuntu developers to make it available through the update manager.

**Edit**: We might try building the upstream kernel manually to see if that fixes our issue, as explained here: 
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
It involves downloading ~700MB, so I'll try it tonight. Will report.

---

### Post by meithan on 2010-05-20
Ok people, I built the 2.6.34 kernel manually, as explained [here]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild"), and the connection has been rock solid for ~3 hours. :)

While configuring the kernel, I was careful to say **yes** to anything related to the rtxxxusb driver. Not sure if that made a difference (probably not). My lsmod now shows a slightly different wifi driver listing:

```
$ lsmod | grep rt
rt2500usb              18894  0 
rt2x00usb              11155  1 rt2500usb
rt2x00lib              31034  2 rt2500usb,rt2x00usb
led_class               3377  1 rt2x00lib
mac80211              252978  2 rt2x00usb,rt2x00lib
cfg80211              167337  2 rt2x00lib,mac80211
```

I'll keep testing the internet, hoping the problem's gone. It's looking good! :)

**Edit**: Left my computer on all night, downloading a torrent, and it's still rock solid. Nothing to report on dmesg. I think it's solved :D

**Edit 2**: Almost 24 hours without disconnections, and I've been constantly downloading/seeding. I think it's safe to say the problem is solved.

---

### Post by ahbart on 2010-06-20
Or you install the new kernel from ppa:
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)
ppa:kernel-ppa/ppa

---

### Post by necromonger on 2010-06-20
Well at least thing's are looking up .I will try the new kernel and let people know.

---

### Post by cnidus on 2010-06-28
Here is a slightly different solution (and maybe I had a slightly different problem).
Same set up as above: Lynksys WUSB54Gv4 with random disconnections. It was never stable for more than about 20 minutes. And wicd could never automatically reconnect. Manual connection seemed to work just find. This had been going on for more than six months and I have upgraded through several releases of Ubuntu, finally ending up with 10.04  with a 2.6.32-22 kernel. Changing the kernel made no difference. 

Last week my PSU crapped out after a power outage at the house. After I replaced the PSU with a new one, the WUSB54G has been rock solid at holding a connection. It has been up for more than 48 hours without so much as a hiccup. The only difference between the old PSU and the new PSU is the wattage; 240 v. 300. 

The only thing I can think of is that my PSU was underpowered after I added new hard drives. And the USB ports were getting less then their fair share causing the wifi to turn off.

Cnidus

---

### Post by atulkakrana on 2010-08-07
> **meithan said:**
> Thanks for the info, ljerabek. Looking at [http://www.kernel.org/](http://www.kernel.org/), it seems the 2.6.34 kernel has just been released (May 16th), but it hasn't been marked for update by Canonical. I wonder how long will it take the Ubuntu developers to make it available through the update manager.

**Edit**: We might try building the upstream kernel manually to see if that fixes our issue, as explained here: 
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
It involves downloading ~700MB, so I'll try it tonight. Will report.

It will only be available in next release of Ubuntu  that is 10.10 Maverick Meerkat and definitely not in released versions.

---

### Post by robtynan on 2010-09-05
> **cnidus said:**
> Here is a slightly different solution (and maybe I had a slightly different problem).
Same set up as above: Lynksys WUSB54Gv4 with random disconnections. It was never stable for more than about 20 minutes. And wicd could never automatically reconnect. Manual connection seemed to work just find. This had been going on for more than six months and I have upgraded through several releases of Ubuntu, finally ending up with 10.04  with a 2.6.32-22 kernel. Changing the kernel made no difference. 

Last week my PSU crapped out after a power outage at the house. After I replaced the PSU with a new one, the WUSB54G has been rock solid at holding a connection. It has been up for more than 48 hours without so much as a hiccup. The only difference between the old PSU and the new PSU is the wattage; 240 v. 300. 

The only thing I can think of is that my PSU was underpowered after I added new hard drives. And the USB ports were getting less then their fair share causing the wifi to turn off.

Cnidus

This problem does not happen in any of MS's crap OS ever! with my wireless dongle... only my Ubuntu install... ver 10.04, latest firmware ........25. By my logic it has noting got to do with power mate.

Please, anyone have a fix?
Or will I just have to wait for 10.10 ? ? ?

---

### Post by SeijiSensei on 2010-09-16
I had the problem of random disconnections using a WUSB54G v.4 and Lucid.  I decided to try the Maverick (10.10) release a few months ago because it included the newer kernel where these problems were supposed to be fixed.

Everything went well through a few kernel upgrades until the most recent upgrade was released, 2.6.35-21-generic.  On that kernel the device intermittently drops signal and needs to reconnect.  For the time being I've gone back to 2.6.35-20-generic which seems not to have these problems.

---

### Post by SeijiSensei on 2010-10-01
I'm now running the 9/28 Maverick daily build with kernel 2.6.35-22-generic, and the problems with my rt2500 device seem resolved.  It reports being connected at 54 Mbit which a speed test confirms.  It's also been running continuously for well over twenty-four hours, which has not been my experience in quite some time.  Thanks to our intrepid developers for fixing what has been one of the most annoying and persistent bugs I've encountered in quite some time.

---

### Post by auburn on 2011-07-15
I got this to work (got it to stop disconnecting) by reverting back to a former kernel, but keeping lucid 10.04. It is successfully working with kernel 2.6.31-23-generic...IOW the last 2.6.31 released by Ubuntu. I did not have success with the first or the latest 2.6.32 kernels that I tried. So simply sudo apt-get install linux-image-2.6.31-23-generic 

Then it helps to remove all later kernels so it will default to booting 2.6.31-23

---

### Post by Fernando Negro on 2011-12-29
Same problem here. And it's easily solved.

As of December 2011, and using that same "version 4" model on Ubuntu 10.04 lucid, I can confirm that switching to a different kernel - simply by installing the right "linux-image-*etc*" package(s) and choosing the new kernel(s) in GRUB - solves the problem.

I've installed the latest kernel of the 2.6 series (from the official lucid package repositories, that appear in Synaptic) - kernel 2.6.38-13-generic - and, using this kernel, not only did I immediately noticed a huge boost in the signal, but I have had a stable connection functioning at optimal conditions ever since.

(NVIDIA users: I had to uninstall the proprietary Nvidia driver, that I was using with the default kernel, and install the driver again, using the new kernel, so that I could see my desktop when I switched to the new kernel.)


***(Edited, after some days of use)***
However... Although I did had a stable connection during a whole day, for the first time, in my first day of using it with a new kernel, in the following days I used it, the connection did drop again a few times. Although much less frequently than before. So the result is: it solves the problem, more or less... Switching to a new kernel made it work more decently for me, although still with a few flaws...
But the problem, I suspect, is not the kernel itself now. Since a guy at a local computer store told me the same thing happens with him in Windows, with a USB model he has. He says it's because it's USB. So that may be the real problem after all, that some kernels manage to cope with more easily than others. (I don't know...) I noticed that the connection was still slow, most of the times. So I suspect that using a USB cable to power up, and connect through, a device, in order to connect to a wireless network, is not a good way to go.
The guy says that in Windows, when the connection hangs or drops, refreshing the browser re-establishes the connection. So that may be what's missing in this more recent kernels - some functionality that re-establishes the connection when it occasionally drops. Anyway, this was an old model that I had around and USB cable-powered models seem to be a bad way to connect to a wireless network. So I ended up buying a [PCI card]("http://ubuntuforums.org/showthread.php?p=11632784#post11632784") that works like a charm in Ubuntu.

---

### Post by thampiverghese on 2012-03-19
Thanks.My Ubuntu is 10.04.1I tried ndis wrapper.But I don't have very clear idea of how to do it.If you can give me detailed steps, I would appreciate it.Thanks.

---

### Post by parkham on 2012-04-07
I know this is an older thread, but maybe this will help anyone.  I turned power saving OFF for my wireless NIC and I am surfing like a champ.  This post explains everything:

[http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/](http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/)

I don't use Ubuntu (Debian Squeeze), but I've found a lot of helpful information on the Ubuntu forums.

---

### Post by Fernando Negro on 2012-09-23
Thank you very much for that information, parkham.

It might be an old thread, but the equipment is still laying around anyway, in case it might be useful someday. And if I need it again, now I know what to do.

Nice.

---

