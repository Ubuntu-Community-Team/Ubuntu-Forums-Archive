---
title: "Netgear Wireless USB Adapter Out-of-the-box Issues"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by lah7 on 2012-09-09
Hello, it's my first post here on the forums!

I'm having trouble getting the most out of Ubuntu 12.04 for a while now due to my **Netgear WN111v2 USB Wireless Adapter** not functioning properly.

I believe this may be something to do with the **carl9170** driver, because after a period of time (mainly high network usage) the adapter will slow down, eventually to a point it's unusable.

When I use the Ubuntu 11.04 Live CD/installation, this issue is not present and the adapter runs much more speeder and smoothly (using the driver **"ar9170"**) then it has been with Ubuntu 11.10 and 12.04 (using **"carl9170"**)

I've searched all over the forums and other websites and had no success with following solutions to get this fixed!

I don't understand what's going on, according to the [[COLOR="Blue"]Networking Wiki site[/COLOR]]("http://linuxwireless.org/en/users/Drivers/carl9170"), this device is supported, but yet... I'm having trouble with maintaining a fast, stable connection between my Ubuntu PC and access point like I did with Ubuntu 11.04.

If wanted, this is what I get with lsusb:
```
Bus 001 Device 042: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9170+AR9101]

```

As a side note, this also isn't the first time I've had trouble with Ubuntu 12.04's wireless. Something similar happened on my Dell Inspiron Duo, but I honestly had no idea how I fixed that (something to do with installing compiz?)

Please could I have a bit of guidance on fixing this problem? Thank you in advance.

---

### Post by chili555 on 2012-09-09
I just read this: [http://wireless.kernel.org/en/users/Drivers/carl9170](http://wireless.kernel.org/en/users/Drivers/carl9170)> It's worth mentioning that the chip was designed, produced and sold in the early 802.11n-draft period. Compatibility will always be an issue.

A known problem is that hardware can not support frame aggregation and QoS at the same time, meaning the device is not suitable for any serious 802.11n setup. Also the hardware crypto has some serious trouble with encrypting/deciphering at high throughput, therefore if possible use 'nohwcrypt=1' as a workaround. You might try two things. First, turn off N-speeds in your router. Second, try the driver parameter:```
sudo modprobe -r carl9170
sudo modprobe carl9170 nohwcrypt=1
```If it helps, we can write one quick file to make it permanent.

---

### Post by lah7 on 2012-09-09
Thank you for your reply chili555, I completely mis-read that part of the Wiki. Oops.

Unfortunately, I don't have control over turning off N-speeds, which would defeat the point of the router really.

The driver parameter command works... for a few minutes... then the speed dramatically reduced again, to a point nothing would load or respond.

I've had a similar issue with my Dell Inspiron Duo (which has the capabilities of N-speeds) quite a while ago with a fresh Ubuntu 12.04, but I somehow solved it by using compiz-wireless (I can't remember how, it has a Atheros adapter like the Netgear USB).

Is there a way to force the adapter in G mode? Or possibly by using another compatible driver?

I'm not too fond with networking with Ubuntu, I don't understand why it's changed and broke what was working perfectly before...

---

### Post by chili555 on 2012-09-09
> I'm not too fond with networking with Ubuntu, I don't understand why it's changed and broke what was working perfectly before...It's not really Ubuntu. The authors of device drivers are various and not really Ubuntu-ans.```
$ modinfo carl9170 
filename:       /lib/modules/3.2.0-30-generic-pae/updates/cw-3.3/carl9170.ko
alias:          arusb_lnx
alias:          ar9170usb
firmware:       carl9170-1.fw
description:    Atheros AR9170 802.11n USB wireless
license:        GPL
[COLOR="Red"]author:         Christian Lamparter <chunkeey@googlemail.com>
author:         Johannes Berg <johannes@sipsolutions.net>[/COLOR]
version:        1:1.9.4
<snip>
```The development of any driver depends, as in all things Linux, on volunteers that take an interest in a device and diligently update the drivers. Some do really well and some not so well. carl9170 is virtually the same driver across all Linux distributions.

There is another parameter you might try:```
sudo modprobe -r carl9170
sudo modprobe carl9170 noht=1
```And you could try them both:```
sudo modprobe -r carl9170
sudo modprobe carl9170 noht=1 nohwcrypt=1
```You can also try the compat-wireless package in the Ubuntu repos:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic[COLOR="Red"]-pae[/COLOR]
```^^^only if you are running a PAE kernel. Find out:```
uname -r
```You could also try the bleeding edge compat-wireless package. Some assembly required.

---

### Post by lah7 on 2012-09-09
> **chili555 said:**
> carl9170 is virtually the same driver across all Linux distributions.
That'll be why the same device doesn't work on the Raspberry Pi neither (I'd bridge the connections with the Ethernet cable if I knew how, I'm still learning -- and that's all a different story.

**Back to the problem,** it appears that when the connection does "weaken", these commands do "liven" it back up:
```
sudo modprobe -r carl9170
sudo modprobe carl9170 noht=1 nohwcrypt=1
```
But this method is inconvenient, such network activities like file transfers would be a problem.

I can verify that I'm using the **3.2.0-30-generic-pae** kernel, so I tried installing the package **linux-backports-modules-cw-3.3-precise-generic-pae** and rebooted, which doesn't make much difference.

The adapter is still using the driver **carl9170** after installing this package, is this normal? I have no idea how the process works, is this package suppose to replace this module?

Many thanks for your support so far.

---

### Post by chili555 on 2012-09-09
> The adapter is still using the driver carl9170 after installing this package, is this normal? Yes.> is this package suppose to replace this module?It is and it did, hopefully with any updates that are available.> But this method is inconvenient, such network activities like file transfers would be a problem.We can certainly write the .conf file so it's permanent, but if the improvement isn't persistent, that won't help much. Are you saying that after invoking these parameters, the transfers eventually slow down anyway?

You might try the compat-wireless-3.5.1-1-snpc package. The carl9170 driver is different, but maybe or maybe not better:> # md5sum drivers/net/wireless/ath/carl9170/carl9170.ko
[COLOR="Red"]a937c3c6e0bf4b2c3abe4b5c47f5c709[/COLOR]  drivers/net/wireless/ath/carl9170/carl9170.ko
# md5sum /lib/modules/3.2.0-30-generic-pae/updates/cw-3.3/carl9170.ko
[COLOR="Red"]0a75b83f4c964b1241de310d35187d18[/COLOR]  /lib/modules/3.2.0-30-generic-pae/updates/cw-3.3/carl9170.koYou seem pretty adept, but if you need guidance compiling it, please feel free to ask.

---

### Post by lah7 on 2012-09-10
> You seem pretty adept, but if you need guidance compiling it, please feel free to ask.
I wouldn't say I'm an expert with Linux only having used it about a year, I've used Windows for a long time and I've decided to try/learn something new (as well as migrating over to it) :)

Surprisingly, I've already downloaded **compat-wireless-3.5.1-1** as an attempt to fix this problem before I posted it to the forums. But this one isn't the **-snpc** package. Oops. After this installation failed, I've typed:
```
sudo make unload
```
Which disconnected my wireless network. Uh oh. (I hope this doesn't mess up the next part!)

I've plugged in my Android (to tether with Wi-Fi) so I have a temporary connection, and downloaded the right package (compat-wireless-3.5.1-1-snpc) and complied and attempted to install using:
```
sudo make
sudo checkinstall
```
Using [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) as a guideline.

Somehow, the **checkinstall** part fails at this point:
> ======================== Installation successful ==========================

Copying documentation directory...
./
./COPYRIGHT
./README

Some of the files created by the installation are inside the home directory: /home

You probably don't want them to be included in the package.
Do you want me to list them?  [n]: n
Should I exclude them from the package? (Saying yes is a good idea)  [n]: y  

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Kernel modules found. Calling depmod in the postinstall script

Building Debian package... FAILED!

*** Failed to build the package

I will give my system a reboot to hope my connection is restored (and working much better) like stated:
> If unsure reboot.

Edit: I've also noticed that there's a software crash when it disconnected/reconnected.
> /sbin/wpa_supplicant crashed with SIGSEGV

---

### Post by lah7 on 2012-09-10
Okay, I have rebooted my system and initially found the login to take longer then usual, I hope this is just a one time thing.

There's no difference - the connection will still die down, and it's sometimes slow to begin with (comparing when I "tether" to use my Android's Wi-Fi connection to the same router via USB)

I feel like giving up with this :( unless it was possible to use obsolete drivers (ar9170) that was used in Ubuntu 11.04. :confused:

If possible, do you know how I can easily uninstall the installation? (if it succeeded?) It's confusing why a newer driver (carl9170) would cause such an issue!! :(

Maybe going wired might be a hassle free way to solve this, I was [very] surprised it worked when I first tried Ubuntu with 11.04, but if this adapter is going to be annoying with newer distributions, I'd hate this time consuming task to break networking altogether!

---

### Post by chili555 on 2012-09-10
I think the process should be:```
cd Desktop/compat-wireless-3.5.1-1-snpc [COLOR="Red"]<--or wherever you extracted it[/COLOR]
./scripts/driver-select restore
make clean
./scripts/driver-select ath
make [COLOR="Red"]<--and if there are no errors[/COLOR]
sudo make install
```

---

### Post by chili555 on 2012-09-10
> If possible, do you know how I can easily uninstall the installation?Sure:```
cd Desktop/compat-wireless-3.5.1-1-snpc [COLOR="Red"]<--or wherever you extracted it[/COLOR]
sudo make uninstall
```

---

### Post by lah7 on 2012-09-10
Thank you chili555 for your support in assisting me in getting the adapter working, but for reliability reasons, I'll consider getting a wired connection instead of using this temperamental USB Adapter.

Networking trouble aside, I'd just like to say thank you to the developers for their hard work on building this incredible OS - Linux! :)

---

### Post by chili555 on 2012-09-10
Networking is a bit hit and miss. Some devices work well pretty consistently. I've had four Intel devices and never had the slightest issue. Broadcoms are usually solid.

Some devices seem to be very good for a couple of releases and stumble for a couple more. Realtek comes to mind. Older devices like your carl and the older Prism cards seem to just fade out. That's the challenge for me, finding a workable solution. Sometimes the only solution is the bin.

I regret I couldn't be of more assistance.

---

### Post by lah7 on 2012-10-19
**[COLOR="Green"]Good news![/COLOR]** The adapter seems to running properly again after I've wiped and freshly installed Ubuntu 12.10.

I can declare this thread **[COLOR="Green"]solved[/COLOR]**, the carl9170 driver is working well at a stable speed of 54 Mb/s connected to a WPA-secured router for the past few hours.

**Just to re-cap:**
Ubuntu 11.04 -- works out-of-the-box flawlessly. Uses older driver.
Ubuntu 11.10, 12.04 -- has connection difficulties, uses new driver.
Ubuntu 12.10 -- works out-of-the-box flawlessly again, uses updated driver.

I would like to thank the Ubuntu and Networking developers, maybe the bug reports have been reflected! :)

---

