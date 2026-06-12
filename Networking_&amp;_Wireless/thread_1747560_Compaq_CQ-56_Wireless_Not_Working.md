---
title: "Compaq CQ-56 Wireless Not Working"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by theprintingplace on 2011-05-02
Hi everyone. I just got a new Compaq CQ56 and installed 11.04 32 bit on it. Everything is great except the wireless is not working. I can't even get it to detect the wireless card.

Any help would be greatly appreciated:

iwconfig:

no wireless extensions

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02636087&cc=emea_africa&dlc=en&lc=en&jumpid=reg_R1002_EMEA_AFRICAEN](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02636087&cc=emea_africa&dlc=en&lc=en&jumpid=reg_R1002_EMEA_AFRICAEN)

Here is the link to the Compaq website. It doesn't say what brand the wireless card is.

Thanks,

Nick :-)

---

### Post by theprintingplace on 2011-05-02
results of lspci:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by theprintingplace on 2011-05-02
Update: I compiled and installed the drive and the wireless now shows up in iwconfig. I still can not connect to any wireless network and none show as available.

Any help would be great! Thanks!

---

### Post by josephmills on 2011-05-02
please open your terminal and type in 
```

rfkill list 

```
could we also see a 
```

lspci -nn

```
then paste there please
thanks

---

### Post by mjulius on 2011-05-03
I have the same laptop - same problem. I was able to get wireless to work using 10.10, but not 11.04. It says that the driver (from ralink) is active, but cannot see the router. Here is how I got it to work using 10.10:

1.) Ralink Driver 5390 from ralinktech.com  . Make sure it goes to your downloads folder. 
2.) Open Terminal 
3.)  Code: 
 sudo su 
 cd Downloads 

 4.)  Code: 
 unzip 2010_1217_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.zip 
 
5.)  Code: 
 cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/ 
 

6.)  Code: 
 make 
 
7.)  Code: 
 make install 
 
 This is a Ralink Driver 5390 from ralinktech.com

---

### Post by theprintingplace on 2011-05-03
home@home-laptop:~$ rfkill list
home@home-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
home@home-laptop:~$

---

### Post by theprintingplace on 2011-05-03
As you can see I don't see anything in the rfkill list even though I added something I was told to in another tutorial, I don't remember what? Any ideas?

---

### Post by ricardisimo on 2011-09-06
Wireless just dropped out on my ex's laptop (CQ56-201NR) five days ago. Was working flawlessly up to then. She says she just tried to add some app (ktouch, as I recall) via Ubuntu Software Center, and then ppfffffft.

```
:~$ rfkill list
0: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
```
and...
```
:~$ lspci -nm
00:00.0 "0600" "8086" "2a40" -r07 "103c" "1605"
00:02.0 "0300" "8086" "2a42" -r07 "103c" "1605"
00:02.1 "0380" "8086" "2a43" -r07 "103c" "1605"
00:1a.0 "0c03" "8086" "2937" -r03 "103c" "1605"
00:1a.1 "0c03" "8086" "2938" -r03 "103c" "1605"
00:1a.7 "0c03" "8086" "293c" -r03 -p20 "103c" "1605"
00:1b.0 "0403" "8086" "293e" -r03 "103c" "1605"
00:1c.0 "0604" "8086" "2940" -r03 "" ""
00:1c.1 "0604" "8086" "2942" -r03 "" ""
00:1d.0 "0c03" "8086" "2934" -r03 "103c" "1605"
00:1d.1 "0c03" "8086" "2935" -r03 "103c" "1605"
00:1d.2 "0c03" "8086" "2936" -r03 "103c" "1605"
00:1d.3 "0c03" "8086" "2939" -r03 "103c" "1605"
00:1d.7 "0c03" "8086" "293a" -r03 -p20 "103c" "1605"
00:1e.0 "0604" "8086" "2448" -r93 -p01 "" ""
00:1f.0 "0601" "8086" "2919" -r03 "103c" "1605"
00:1f.2 "0106" "8086" "2929" -r03 -p01 "103c" "1605"
00:1f.3 "0c05" "8086" "2930" -r03 "103c" "1605"
00:1f.6 "1180" "8086" "2932" -r03 "103c" "1605"
02:00.0 "0280" "1814" "5390" "103c" "1636"
03:00.0 "0200" "10ec" "8136" -r02 "103c" "1605"
```
I've already identified the killswitch button, F12 (which is amber when the wifi is dead, bright white right now) so it's not that. Any help is appreciated.

Interesting... sudo lshw reveals that the network controller is under "*-network UNCLAIMED". It knows it's Ralink, but has no other details for it. It's not quite invisible to Ubuntu; more like translucent. Odd.

---

### Post by wildmanne39 on 2011-09-06
Hi, please run these commands and post the results here:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
Thank you

---

### Post by nm_geo on 2011-09-06
chili555 is the Ralink doctor

[http://ubuntuforums.org/showthread.php?t=1779005](http://ubuntuforums.org/showthread.php?t=1779005)

i would recommend reading that one.  I also just checked the ralink website the driver recommend is still current.

2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL.bz2

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by ricardisimo on 2011-09-12
sudo lshw -C network:
```
[sudo] password for roxanne: 
  *-network UNCLAIMED     
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:93500000-9350ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 98:4b:e1:b3:d4:24
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:91420000-9142ffff
```
lspci -nn | grep 0280:
```
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
```
iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```
rfkill list all:
(nothing)
lsmod:
```
Module                  Size  Used by
rt2860sta             494649  0 
crc_ccitt              12595  1 rt2860sta
nls_utf8               12493  1 
udf                    83795  1 
crc_itu_t              12627  1 udf
parport_pc             32111  0 
ppdev                  12849  0 
snd_hrtimer            12680  1 
joydev                 17322  0 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  4 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
hp_wmi                 13418  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
sparse_keymap          13666  1 hp_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  451033  4 
psmouse                73312  0 
soundcore              12600  1 snd
drm_kms_helper         40745  1 i915
drm                   184164  5 i915,drm_kms_helper
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3 
libahci                25548  1 ahci
r8169                  42534  0 

```

I'm perplexed that her wireless was working flawlessly up until about a week ago, without having to do anything other than toggle the wifi killswitch on the keyboard. What gives?

I downloaded the latest Ralink driver from the thread listed above, but either it's a completely different version, or I'm misunderstanding something, because some of the folders he asks to cd into or work with are not there. Going to reread and retry right now.

---

### Post by ricardisimo on 2011-09-12
OK, I figured it out, and nothing. Networking is enabled, and I know there are at least three open connections right around here (and a dozen password protected ones), but nothing is appearing as available.

I really don't think the driver was the issue in the least, since as I stated before this laptop was connecting flawlessly up until about a week ago. What the hell is going on?

Edit: sure enough, I just popped a D-Link USB Wireless adapter, and voila. Connections available all over the place. Pull it out and all I'm left with is the wired connection.

---

### Post by ricardisimo on 2011-09-13
Anyone? Why does lshw know that what's there is Ralink, but it can't actually identify what it is? Weird, no? Any help is appreciated.

---

### Post by wildmanne39 on 2011-09-15
Hi, for some reason your lsmod is showing the wrong driver unless you have another wireless adapter plugged in then in that case it is showing no drivers.

nm_geo links are good to get this card working or you could upgrade the kernel the latest 3.0 and it has support for your adapter built in to it.

You can also try this.
```
sudo rmmod -f rt2860sta
```
```
sudo modprobe rt5390sta
```
that may work if this driver was installed already.
Thank you

---

### Post by ricardisimo on 2011-09-16
```
:~$ sudo rmmod -f rt2860sta
ERROR: Removing 'rt2860sta': No such file or directory

:~$ sudo modprobe rt5390sta
FATAL: Error inserting rt5390sta (/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt5390sta.ko): Invalid module format
```
Odd, no?

---

### Post by wildmanne39 on 2011-09-16
Hi, not so much. I recommend going to post 10 and following the directions in those links to compile the driver and install it.
Thank you

---

### Post by ricardisimo on 2011-09-18
I did (or at least I think I did.) Didn't work. I'm very suspicious of this, because the wireless worked flawlessly before, but not now. I decided to back up all of her files and do a fresh install... no change. The USB adapter works perfectly, though.

Fried wireless card, perhaps? Any way to tell?

---

### Post by wildmanne39 on 2011-09-18
Hi, the card is being seen, so my question is after you reinstalled ubuntu did you go to post 10 and follow the links to install the 5390 driver, you would know if you did, you would of have to compiled it.
Thank you

---

### Post by ricardisimo on 2011-09-22
The card was working - without my having to do anything - out-of-the-box up until a few weeks ago. I suppose I can try again with the new install, but I'd rather just loan her the USB wireless, I think.

---

### Post by chili555 on 2011-09-22
> **ricardisimo said:**
> The card was working - without my having to do anything - out-of-the-box up until a few weeks ago. I suppose I can try again with the new install, but I'd rather just loan her the USB wireless, I think.Unless you are running a beta version of Ubuntu 11.10, Ralink 5390 devices don't work out of the box. If you want to lend the USB device, that's a simple fix. If you want to troubleshoot the rt5390sta compile problems, the Wild Man and I will be happy to help.

---

### Post by ricardisimo on 2011-09-24
> **chili555 said:**
> Unless you are running a beta version of Ubuntu 11.10, Ralink 5390 devices don't work out of the box. If you want to lend the USB device, that's a simple fix. If you want to troubleshoot the rt5390sta compile problems, the Wild Man and I will be happy to help.

I would love to fix it, get my USB back and be done with it. But tell me this: Will a fresh install of 11.10 fix the problem (hypothetically, that is... I know life is complicated, even virtual life)? She has her laptop right now anyways, so it might be worth my while just to let her make do until Oneric. What do you think?

---

### Post by chili555 on 2011-09-24
> **ricardisimo said:**
> I would love to fix it, get my USB back and be done with it. But tell me this: Will a fresh install of 11.10 fix the problem (hypothetically, that is... I know life is complicated, even virtual life)? She has her laptop right now anyways, so it might be worth my while just to let her make do until Oneric. What do you think?It's easy to find out; download the live CD and try it. Posts #47 et seq may be helpful: [http://ubuntuforums.org/showthread.php?t=1685430&page=5](http://ubuntuforums.org/showthread.php?t=1685430&page=5)

If you want to troubleshoot the rt5390sta compile problems, the Wild Man and I will be happy to help.

---

### Post by ricardisimo on 2011-09-30
I just tried the LiveCD of 11.10 Beta, and the wireless is working flawlessly, I'm pleased to report. Yay. Now I'm going to install, and lord knows I've experienced problems after install that weren't present during the LiveCD session, so...

Wish me luck!

---

### Post by zaheer116 on 2011-09-30
I've installed ubuntu 11.10 beta 2, Its nice but for some reasons i'm not getting good wifi reception on it, even if I place it next to the wireless router i get only one bar. while its working fine in windows 7, getting full wifi signals. Any help would be highly appreciated.

---

### Post by ricardisimo on 2011-10-01
Installed 11.10, and something funny was definitely going on. The laptop's wireless was a little sluggish. Not a lot, but a little. But while it was tapping into the router, the desktop's *wired* signal (from the same router) came to a near standstill. Bizarre.

My guess is that the laptop was soaking up a _lot_ of bandwidth and not really using all of it, or at least that's how it felt.

---

### Post by chili555 on 2011-10-01
> **zaheer116 said:**
> I've installed ubuntu 11.10 beta 2, Its nice but for some reasons i'm not getting good wifi reception on it, even if I place it next to the wireless router i get only one bar. while its working fine in windows 7, getting full wifi signals. Any help would be highly appreciated.Would you please start your own new thread and leave a link here so I can respond? Please include:```
lspci -nn | grep 0280
```Thanks.

---

