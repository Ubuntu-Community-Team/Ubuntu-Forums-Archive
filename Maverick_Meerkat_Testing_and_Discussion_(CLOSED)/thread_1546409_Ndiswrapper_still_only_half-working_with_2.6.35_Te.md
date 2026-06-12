---
title: "Ndiswrapper still only half-working with 2.6.35? Testing needed!"
date: 2010-08-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-08-05
I'm finding myself only able to scan for routers and unable to actually connect when ndiswrapper is set up properly on kernels newer than 2.6.34-5.14.

I'd deeply appreciate it if someone could help me confirm this bug:

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/613796](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/613796)

If you don't have a 2.6.34 or 2.6.32 kernel, install these (x86) simultaneously with a wildcarded dpkg call:

[http://launchpadlibrarian.net/49660925/linux-headers-2.6.34-5_2.6.34-5.14_all.deb](http://launchpadlibrarian.net/49660925/linux-headers-2.6.34-5_2.6.34-5.14_all.deb)
[http://launchpadlibrarian.net/49660936/linux-headers-2.6.34-5-generic_2.6.34-5.14_i386.deb](http://launchpadlibrarian.net/49660936/linux-headers-2.6.34-5-generic_2.6.34-5.14_i386.deb)
[http://launchpadlibrarian.net/49660935/linux-image-2.6.34-5-generic_2.6.34-5.14_i386.deb](http://launchpadlibrarian.net/49660935/linux-image-2.6.34-5-generic_2.6.34-5.14_i386.deb)

---

### Post by k3lt01 on 2010-08-07
I just posted about this issue cause the forum search function didn't show this thread.

Mine works with Karmic and Lucid kernels but not with 2.6.35-14 in Maverick. Thanks for posting this now I know its not just me.

---

### Post by Starks on 2010-08-07
I'm glad it's not just me and my wonky hardware either.

---

### Post by k3lt01 on 2010-08-07
I have added myself to that bugreport. Tomorrow when I have some time I will remove Maverick's ndiswrapper and install Lucid's to see if that works. I had a similar, not identical though, issue with Gutsy. I had to use Feisty's ndiswrapper to get it to work. I'm hoping it may be as easy as that.

---

### Post by Starks on 2010-08-07
As I said in the bug report, the ndiswrapper library version doesn't matter and even if it did, you'd have a hard time overriding the newer module version in the kernel.

---

### Post by k3lt01 on 2010-08-07
> **Starks said:**
> As I said in the bug report, the ndiswrapper library version doesn't matter and even if it did, you'd have a hard time overriding the newer module version in the kernel.I have seen bugs that affect some hardware/application combinations and not others. I was testing out a theory that had worked for me before. As for overriding a newer version, if you mean stopping it from downloading that is simple all you have to do is "Pin" the version you want and it will not download a new version unless you the user ask it to. It is obvious it has worked for some kernels and then stopped after a kernel update and then started working again after yet another update, so we need to know what Maverick kernels it has worked on and what ones it hasn't. Then we need to know the difference between them so we can override it.

I will do it again tonight and copy down all the messages it is throwing cause it is something about upcoming versions not needing the code I use to install the driver (something about .conf). Maybe it is as simple as the driver install procedure we used to use is now incorrect.

---

### Post by Starks on 2010-09-01
It's the kernel, not ndiswrapper.

Kernel version is the ultimate determinant of whether ndiswrapper can connect or not.



 2.6.32: Connects automatically on ndiswrapper 1.56-2
2.6.34: Connects automatically or after modprobe and modprobe -r on ndiswrapper 1.56-2
2.6.35: Connects under no circumstances on ndiswrapper 1.56-2

---

### Post by JDShu on 2010-09-02
Thanks for posting this, I have the same problem. Good to know I'm not the only one.

---

### Post by Tracy177 on 2010-09-02
> **Starks said:**
> I'm finding myself only able to scan for routers and unable to actually connect when ndiswrapper is set up properly on kernels newer than 2.6.34-5.14.

I'd deeply appreciate it if someone could help me confirm this bug:

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/613796](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/613796)

If you don't have a 2.6.34 or 2.6.32 kernel, install these (x86) simultaneously with a wildcarded dpkg call:

[http://launchpadlibrarian.net/49660925/linux-headers-2.6.34-5_2.6.34-5.14_all.deb](http://launchpadlibrarian.net/49660925/linux-headers-2.6.34-5_2.6.34-5.14_all.deb)
[http://launchpadlibrarian.net/49660936/linux-headers-2.6.34-5-generic_2.6.34-5.14_i386.deb](http://launchpadlibrarian.net/49660936/linux-headers-2.6.34-5-generic_2.6.34-5.14_i386.deb)
[http://launchpadlibrarian.net/49660935/linux-image-2.6.34-5-generic_2.6.34-5.14_i386.deb](http://launchpadlibrarian.net/49660935/linux-image-2.6.34-5-generic_2.6.34-5.14_i386.deb)

hi i have iwl4965 and iwl5100

and i think there is no bug or anything why did you use ndiwrapper?

did you ever hear about compat-wireless ?

if your dmesg doesnt show any problems with your card than it means u got firmware in propper place mean home/firmwares it is basic to sort wifi card in ubuntu.

check up compat-wireless.org 
there u will find fimware for your card and extra drivers for pen testing testing your network etc. 

at the end your card if u got laptop u have somewhere button to swich wireless on and off switch it on cuz if it is off even if u got propper drivers u wont be able to connect to internet.

just to show you that 4965 4950 5000 5100 is working thats my output 

```
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6000g2b-5.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-1000-3.ucode
srcversion:     8BEA3A15EF75E9324B7D3B9
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005311bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005321bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005301bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005207bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005206bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005201bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005107bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005125bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005115bc*sc*i*
alias:          pci:v00008086d0000008Fsv*sd00005105bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001207bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001201bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,mac80211,cfg80211
vermagic:       2.6.35-19-generic SMP mod_unload modversions 686 
parm:           swcrypto50:using crypto in software (default 0 [hardware]) (deprecated) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num50:number of hw queues in 50xx series (deprecated) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable50:disable 50XX 11n functionality (deprecated) (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (deprecated) (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart50:restart firmware in case of error (deprecated) (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_announce:Enable BT channel announcement mode (default: enable) (bool)
```

u can check your drivers for your card by typing modinfo iwlagn

so there is no bug or problems with your card at all

Linux matrix 2.6.35-19-generic #25~lucid1-Ubuntu SMP Wed Aug 25 04:24:28 UTC 2010 i686 GNU/Linux


over here is a propper driver for your card and any other iwl [http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads](http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads)

install it in your no matter kernel u got /firmwares 

than if i was u i would download [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)  latest driver this is whole bunch of drivers for iwl rt zd etc etc etc cards there u will find drivers updated daily download the newest one


and make sudo make install

and your internet will work for sure

just remember if u got laptop to press the network button

---

### Post by Starks on 2010-09-02
As I mentioned in the bug, iwl3945 is crippled and is currently useless.

---

### Post by JDShu on 2010-09-10
Oops, should have mentioned this, I'm using Marvell's mrv8335 driver.

---

### Post by QwUo173Hy on 2010-09-10
I'm using the 2.6.31-22 kernel to connect. Thanks for posting the bug report. I'll go to it now.

---

### Post by QwUo173Hy on 2010-09-12
I see a fix has been released - has anyone noticed it in the updates yet? I've been looking at the updates but haven't seen anything for the kernel yet.

---

### Post by pauljayd on 2010-09-30
Upgraded to Maverick, and b43legacy driver runs my Broadcom 4306 at 1mbs.
On Jaunty, I was able to install ndiswrapper (from "https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff" and run at 56mbs, but I hardly remember all the steps I took (I'm not a Linux programmer, and it took several attempts!)
After much googling, I'm now lost: Is there a definitive url for successful Broadcom wireless under Maverick?
Is there a definitive url for ongoing testing for this?
Is this the url?

Help!!!

pauljayd

---

### Post by Starks on 2010-09-30
If the most recent XP driver .inf (extract from zip or exe) doesn't work with ndisgtk, try to find one that's at least 2 or 3 years old.

---

### Post by pauljayd on 2010-09-30
Thanks for the quick response, but don't I have to 'blacklist' something?
After ndisgtk, I've got 2 wireless connections available: 1. Auto dpnet (created automatically when Maverick installed), and 2. dpnet (created when ndisgtk executed).
It seems that #1 is always used (...driver=b43legacy... from "lshw -C network" command.

??

---

### Post by Starks on 2010-09-30
What is your alternate driver listed in "ndiswrapper -l"

Whatever that driver is, that's the one you need to blacklist.

---

### Post by pauljayd on 2010-09-30
This is what I get:

paul@paul-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)
paul@paul-laptop:~$

If I do the following:

sudo gedit /etc/modprobe.d/blacklist
 
and add the line:
 
blacklist bcmwl5

Then I don't  connect at all.
 
What to do next?
Thanks.

---

### Post by ktp on 2010-09-30
Isn't the "alternate driver: ssb"?  So don't you have to blacklist ssb and not bcmwl5.

Also this might help:

[http://ubuntuforums.org/showpost.php?p=4881538&postcount=6](http://ubuntuforums.org/showpost.php?p=4881538&postcount=6)

---

### Post by Starks on 2010-10-01
On my machine, iwl3945 comes up as my alternate and ssb is my for my BCM4401 ethernet and BCM2046 bluetooth.

If I blacklist ssb, I would lose both unless I did some trickery:

[http://ubuntuforums.org/showthread.php?t=796932](http://ubuntuforums.org/showthread.php?t=796932)

---

### Post by pauljayd on 2010-10-01
1,000 pardons, please.
Frustration with my ignorance of Linux is causing me to blank out.
I tried "blacklist ssb" - no connection
I tried "blacklist ssb" and "blacklist b43legacy" - no connection.

Now, I don't really know where I'm at at all.
I'm going to wait until final Maverick release, and other user's efforts are successful...

Thanks all, anyway.

---

### Post by Starks on 2010-10-01
Try reading these:

[http://ubuntuforums.org/showthread.php?t=780590](http://ubuntuforums.org/showthread.php?t=780590)
[http://ubuntuforums.org/showthread.php?t=780692](http://ubuntuforums.org/showthread.php?t=780692)

---

### Post by pauljayd on 2010-10-02
[SOLVED]
I saw some info about "wicd", so I installed it.
Wireless worked at full speed. There was some conflict at connection: wrong password/authentication...
So, I removed wicd.
Now, default network manager works perfectly, and I'm getting full speed with ndiswrapper.

Again, thanks to all for quick responses and great advice.

Paul

---

### Post by Starks on 2010-10-03
ndiswraper doesn't work with 2.6.36 now...

great.

---

