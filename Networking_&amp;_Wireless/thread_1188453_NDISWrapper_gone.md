---
title: "NDISWrapper gone"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by Biohmmwv on 2009-06-15
I am running a Dell Inspiron 1721 with Jaunty. I was using NDISWrapper for wireless and wanted to get a better networking manager then the one that came with Ubuntu. I installed Wicd Network Manager and it was working until I rebooted the system, I could not get wireless working. I saw that NDISWrapper was no longer showing up on restricted drivers. I did a manual reinstall of NDISWrapper from a thumbdrive, and everything worked fine for a couple of days. 
I rebooted my system, NDIS disappeared again, and manually reinstalling it does not work. 
O, and I am a Linux Newb.
 Thank you in advance.

---

### Post by dmizer on 2009-06-15
Make sure that ndiswrapper is added to the modules startup list in /etc/modules. It should look something like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

[COLOR="Red"]ndiswrapper[/COLOR]
```
You may have other things listed in this file. Don't remove them if that's the case. All you have to do is add "ndiswrapper".

---

### Post by Biohmmwv on 2009-06-16
Thank you. I did not want to reply too fast until I put your solution through its paces. I did as you said, and it worked until I rebooted the system.
 Now when the system is rebooted, the restricted hardware driver says "this driver is activated but not currently in use." To clear this, I have to Deactivate, then quickly cancel the un-installation and activate the driver. It then says "This driver is activated and currently in use." The wireless works after this. 
I uninstalled Wicd and reinstalled the manager that came with Ubuntu, and NDiS disappeared completely, no wireless. I reinstalled NDiS, rebooted several times, but to no avail. I reinstalled Wicd, and NDis re-appeared. But, I have to deactivate, and reactivate the NDis drivers upon every reboot for it to work.

---

### Post by dmizer on 2009-06-16
Before you deactivate and reactivate the drivers, please run the following command:
```
lshw -C network
```
and
```
lsmod
```
And post the results here.

---

### Post by Biohmmwv on 2009-06-16
The output for lshw -C network is:


  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8d:b9:73
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 42:17:d4:50:12:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


The output for lsmod is :

Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxnetflt             91016  0 
vboxdrv               117544  1 vboxnetflt
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
ndiswrapper           193436  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
uvcvideo               63240  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
compat_ioctl32          9344  1 uvcvideo
psmouse                61972  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci              15232  0 
video                  25360  0 
i2c_piix4              18448  0 
shpchp                 40212  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
serio_raw              13316  0 
pcspkr                 10496  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ricoh_mmc              11904  0 
sdhci                  23940  1 sdhci_pci
output                 11008  1 video
k8temp                 12416  0 
dcdbas                 15264  0 
btusb                  19608  2 
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
b44                    35984  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
ssb                    41220  1 b44
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

Hopefully you can tell me what I did wrong;). There is a real learning curve coming from M$.
Thank you in advance.

---

### Post by dmizer on 2009-06-16
Add these two lines:
```
blacklist b44
blacklist ssb
```
To the end of /etc/modprobe.d/blacklist

Reboot and all should be well.

---

### Post by Biohmmwv on 2009-06-16
I put the two lines of code in the /etc/modprobe.d/blacklist.conf  file
I rebooted, and no wireless. I checked the restricted drivers, and nothing was listed. So, I removed the two lines of code and rebooted, still no wireless. I then uninstalled Wicd, rebooted, and the restricted drivers listed the wireless card again, but was not being used by the system. I deactivated, reactivated it, reinstalled wicd and everything is back to working. 
I think if I reboot the system I will have to deactivate and reactivate the drivers for the card again.

---

### Post by Ayuthia on 2009-06-16
I am not for sure if you are using NDISwrapper.  From your information in lshw -C network, it shows that the b43 module was in use, not NDISwrapper.  You then mentioned that you activated your card in the restricted drivers.  I am not for sure about which restricted drivers screen you are referring.  There is one in System->Administration->Hardware Drivers that allows you to activate your card.  There is also another section for Windows Wireless Drivers (or something like that) that is used for NDISwrapper.

You can confirm which module you are using by checking lshw -C network again.

The other thing that I want to mention is that you do have a Broadcom 44xx series wired network card.  This means that it uses the b44 module.  If you try to use the Broadcom STA driver or NDISwrapper, you will need a workaround to make your wireless card work.  If you blacklist the b44 module, you will not be able to use your wired connection.

If you do find that you are using the b43 module, you might want to go and blacklist the ndiswrapper module so that it does not cause conflicts with the b43 module:
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist.conf
```
This command is for Jaunty.  If you are using a different version of Ubuntu, you will need to use blacklist as the filename instead of blacklist.conf.

---

### Post by dmizer on 2009-06-16
If you have wicd installed, you should uninstall network-manager:
```
sudo aptitude remove network-manager
```
network-manager and wicd conflict with each other and cause your network to be non-functional.

Rather than going crazy with uninstalling and reinstalling things that only need to be reloaded, next time do this:
```
sudo rmmod b43
sudo rmmod ssb
sudo modprobe ndiswrapper
```
You'll have to do that every time you boot. If this works, we can add those lines to a boot script to make it permanent.

If you uninstall network-manager, and you find that the b43 module works, then simply uninstall ndiswrapper rather than trying to blacklist it as suggested above.

---

### Post by Biohmmwv on 2009-06-23
I apologize for not getting back sooner, I has my wifi working and was afraid to reboot and lose it. When I got to a point where I could work with it for a few hours, I rebooted the system to see what would happen.
Of course, I lost wifi again:(. So, I followed your advice and use the code:

echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist.conf

Then, I went into Blacklist-bcm43.conf and comented out 
#blacklistb43
#blacklist ssb
#load wl before b44 so that both work
#blacklist b44

Rebooted the system, and reinstalled Wicd, it worked!:D

In system> Administration> Hardware Drivers, the Broadcom sta wireless driver is not activated, nor will it activate.
I guess the Broadcom wireless card is natively supported in Ubuntu now, unlike previous versions of Ubuntu. And apparently ( as both of you pointed out) my system is not using NDISwrapper as I had been led to believe.
Thank you both again. Since I am a newbie, I only have one question left. What did I do right? And where did I go wrong in the beginning? 
Also, where do I go to get as educated about Linux as you dmizer?
Thanks again
          Bio

---

### Post by dmizer on 2009-06-23
> **Biohmmwv said:**
> Thank you both again. Since I am a newbie, I only have one question left. What did I do right? And where did I go wrong in the beginning? 
Also, where do I go to get as educated about Linux as you dmizer?
Thanks again
          Bio
That looks more like three questions ;)

Well, coming here for help was better than trying to sift through ages of blog posts and other questionable suggestions. Probably your biggest mistake was the continuous uninstalling and reinstalling of everything. This simply confused the issue rather than providing assistance in fixing the actual problem.

My education was obtained almost entirely during my 3 year membership on this forum. If you look at my earliest posts, you'll find that I was as noob as (if not more than) you.

Just in case there was any doubt ... I'm still very much a noob. There are a huge number of people on this forum who know way way more than I could ever hope to know, especially since my knowledge is mostly Ubuntu specific.

If you want advice on furthering your education, I can't stress how important it is to learn the CLI. By that, I don't mean that you should sit down with a book and read about commands and what they do. Rather, I mean that you should always strive to accomplish system admin tasks (as much as possible) via the CLI.

---

