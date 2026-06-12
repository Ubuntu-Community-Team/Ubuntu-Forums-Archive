---
title: "Ubuntu 12.04 beta2 issues with Ralink RT2800 PCI loses connection"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by neilhuang on 2012-04-13
Hi,

I just upgraded from 10.04 LTS to 12.04 Beta 2.
The wireless card I have in my PC is Ralink RT2800 802.11n PCI. This card functioned fine back in 10.04 as it rarely dropped connection and had a very fast and stable transfer speed.

Once I've moved to 12.04 Beta 2 (kernel 3.2.0-23 so far), the wireless card works but every now and then would start dropping all the packets. The connection status is still connected to my AP, but I can't ping... I can't look up DNS, etc.

It still shows the list of AP's around, so I wonder if the scan is working fine, or maybe it could have been the cached list from when the wireless was working...

The easy way to fix it is to click on network-manager and disconnect from the AP, and reconnect to the AP. Once it reconnects, things will be working again.

It's pretty annoying.

I'm not sure what diff it will make between b2 and the actual 12.04 release, but since this is specific to the driver, I have a feeling the only way for me to get back the driver that was in 10.04.

Questions:

1. The driver objects are here:
```

neilhuang@neilhuang-desktop:~$ modprobe -l | grep rt2800
kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko

```Does that mean the drivers are compiled and installed with the kernel? 
I know I can do modprobe -r [driver], which means the drivers are pluggable modules. But do the modules exist within the same kernel (3.2.0-xx vs 2.6.32-yy) source?

2. If the above question is true, is there anyway for me to find the original rt2x00 drivers that came with the 2.6.32 kernel (aka ubuntu 10.04) and somehow modprobe it back to the current kernel? (because the ubuntu 10.04 drivers were stable for me)

3. Where can I find logs for the wireless drivers' so I can hopefully see what's happening when packets start to drop?

Thanks and I hope the above questions make sense. I'm not much of a kernel/driver level guy, heh. Mostly just application level dev for me as my day job.

---

### Post by jawilljr on 2012-04-13
Try turning off power management:

```
sudo iwconfig wlan0 power off
```

Jerry

---

### Post by neilhuang on 2012-04-14
Thanks. Will give it a try.

---

### Post by neilhuang on 2012-04-14
> **jawilljr said:**
> Try turning off power management:

```
sudo iwconfig wlan0 power off
```Jerry

Sorry, this doesn't seem to help.  Thanks anyway.
Any other ideas?

---

### Post by benhurtuna on 2012-04-17
@neilhuang I have a same problem with Ralink RT2800. Did you found any solution?

---

### Post by neilhuang on 2012-04-18
Not yet I'm constantly hitting it, especially during heavy data tx/rx...

Does anyone have experience with driver modules?

---

### Post by neilhuang on 2012-04-18
I found out that "Modules from one kernel can't be loaded into another kernel" so that throws my idea out the window...

I'm kind of lost as to how to debug and contact the right resources to help fix this bug...

---

### Post by BJCV86 on 2012-04-18
> **neilhuang said:**
> Not yet I'm constantly hitting it, especially during heavy data tx/rx...

Does anyone have experience with driver modules?


I think this is my experience as well. It goes fast, than stops. Using RT2800. I don't know how to install anything new and nothing else is in the U.S.C.

---

### Post by neilhuang on 2012-04-20
I did some of my own research and playing around and I think I found a solution. Long story short, I had to rebuild the drivers and reload them into the kernel. I learned something doing this so I figured I can share the process with you guys. Here goes.


[LIST=1]
[*]Download the driver from Ralink's website:
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
Click on ra2860 link and download.
[*]Extract the archive using either a combination of bunzip + tar  or just use archive manager for ease.
[*]At this point you would have the directory "2010_07_16_RT2860_Linux_STA_v2.4.0.0" extracted. You can view the README_STA file or just follow what I did here.
[*]From the README:
> ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
      Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.so ```
vim os/linux/config.mk
``` (or gedit)
and change the two lines accordingly.
[*]run make from the prompt.
If 5 fails, make sure you have the build-essential package. ```
sudo apt-get install build-essential
```
[*]Copy the new dat AND ko file to a directory for safekeeping.
```
sudo mkdir -p /etc/Wireless/RT2860STA/
sudo cp RT2860STA.dat  /etc/Wireless/RT2860STA/
sudo cp os/linux/rt2860sta.ko /etc/Wireless/RT2860STA/
```
[*]To test to see if this new driver module works, you need to try to insert it into the Kernel and then remove the old one.
[*]Removing old modules:
```
sudo modprobe -r rt2800pci
```At this point, your wireless network would disconnect. If you want to reconnect using the old module, simply run.

```
sudo modprobe rt2800pci
```
[*]Inserting new module:
```
sudo insmod /etc/Wireless/RT2860STA/rt2860sta.ko
```
[*]Verify the module is loaded:
```
neilhuang@neilhuang-desktop:/etc/Wireless/RT2860STA$ lsmod | grep rt
rt2860sta             864748  1 
parport_pc             32866  1 
parport                46562  3 ppdev,parport_pc,lp
```
[*]At this point, your network-manager should pick up your old Access point and your internet would work again.

You may want to add this to your kernel so that this new compiled driver would load everytime. 
I found the instruction from another thread ([http://ubuntuforums.org/showthread.php?t=1369806](http://ubuntuforums.org/showthread.php?t=1369806)), but it applies here so I'll show you what I did more in depth than the thread above.
[*]Make a staging area for your wireless driver. Note that 3.2.0-23 may change per kernel update.
```
sudo mkdir -p /lib/modules/3.2.0-23-generic/kernel/drivers/staging/rt2860
```
[*]Make a soft link pointing to your made driver.
```
sudo ln -s /etc/Wireless/RT2860STA/rt2860sta.ko /lib/modules/3.2.0-23-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
sudo ln -s /etc/Wireless/RT2860STA/RT2860STA.dat /lib/modules/3.2.0-23-generic/kernel/drivers/staging/rt2860/RT2860STA.dat
```
[*]Re-scan the kernel drivers
```
sudo depmod
```
[*]Verify that the driver is now in the list of modprobe:
```
neilhuang@neilhuang-desktop:/lib/modules/3.2.0-23-generic$ modprobe -l | grep 2860
kernel/drivers/staging/rt2860/rt2860sta.ko
```
[*]Blacklist original driver so it doesn't conflict
```
sudo vim /etc/modprobe.d/blacklist.conf
```or
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add the following lines:
```

# Removing old rt2800 buggy generic drivers
blacklist rt2800pci
```
[*]Restart your computer and run step 15 again to see it working. And check again with this:
```
neilhuang@neilhuang-desktop:~$ lsmod | grep 2860
rt2860sta             864748  1 
```
[/LIST]
So just for future reference... I think steps 12-15 may be needed to be repeated per each kernel update. 


Also, note that my card is actually 

**[SIZE=1]TRENDnet TEW-623PI[/SIZE]**

and according to the [wiki]("http://www.wikidevi.com/wiki/TRENDnet_TEW-623PI_v3") I find that I can use the 2860 driver. YMMV so make sure to read up on your individual cards before attempting this.

---

### Post by bearman83 on 2012-04-30
I got the same issue with my linksys wmp600n where it loaded the rt2800 instead of the rt2860 driver, and this solved my problems.

Thanks a bunch!

---

### Post by Bushi86 on 2012-05-07
Hello,

I'm having similar issues with my Ralink card. I followed your instructions, but am getting the following error:

```

sudo insmod /etc/Wireless/RT2860STA/rt2860sta.ko
insmod: error inserting '/etc/Wireless/RT2860STA/rt2860sta.ko': -1 Device or resource busy

```

Can you please help and let me know how to proceed?

Thanks in advance!

---

### Post by neilhuang on 2012-05-08
> **Bushi86 said:**
> Hello,

I'm having similar issues with my Ralink card. I followed your instructions, but am getting the following error:

```

sudo insmod /etc/Wireless/RT2860STA/rt2860sta.ko
insmod: error inserting '/etc/Wireless/RT2860STA/rt2860sta.ko': -1 Device or resource busy

```Can you please help and let me know how to proceed?

Thanks in advance!

Could you try to continue through the steps, more specifically continue on and finish the steps about blacklist and restart your system. See if that helps.

If that doesn't work after restarting your system, could you list the output of
```
lsmod
```
and
```
lspci
```

---

### Post by Bushi86 on 2012-05-08
> **neilhuang said:**
> Could you try to continue through the steps, more specifically continue on and finish the steps about blacklist and restart your system. See if that helps.

If that doesn't work after restarting your system, could you list the output of
```
lsmod
```

I was able to continue with the steps, but it did not seem to help. lsmod shows several modules that I have blacklisted as still in use (even after a reboot). Here is the output:

```

$ lsmod
Module                  Size  Used by
ses                    17417  0 
enclosure              15269  1 ses
vesafb                 13844  1 
snd_hda_codec_hdmi     32474  0 
usb_storage            49198  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  2 
snd_hda_codec_realtek   223867  1 
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
fglrx                3263966  124 
mxm_wmi                12979  0 
sp5100_tco             13791  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
i2c_piix4              13301  0 
fam15h_power           13032  0 
mac_hid                13253  0 
psmouse                87692  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
serio_raw              13211  0 
k10temp                13166  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  2 asus_wmi,mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
e1000e                156693  0 

```

Here is the output from lspci:
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port D)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port E)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port F)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port G)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 683d
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0
02:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
03:00.0 Ethernet controller: Intel Corporation 82583V Gigabit Network Connection
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
06:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
07:05.0 Network controller: Ralink corp. RT2800 802.11n PCI

```

---

### Post by neilhuang on 2012-05-09
> **Bushi86 said:**
> 

```

$ lsmod
Module                  Size  Used by
ses                    17417  0 
enclosure              15269  1 ses
vesafb                 13844  1 
snd_hda_codec_hdmi     32474  0 
usb_storage            49198  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  2 
snd_hda_codec_realtek   223867  1 
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
fglrx                3263966  124 
mxm_wmi                12979  0 
sp5100_tco             13791  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
i2c_piix4              13301  0 
fam15h_power           13032  0 
mac_hid                13253  0 
psmouse                87692  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
serio_raw              13211  0 
k10temp                13166  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  2 asus_wmi,mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
e1000e                156693  0 

```

I'm curious as to why you have 
```

rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib

```so many modules using all these drivers. I suspect that this causes the drivers conflict. 

You can try to do a modinfo on the modules (left column) to find more information. 

Try [this]("http://ubuntuforums.org/showthread.php?p=5028400") to see if it helps... I'm not exactly sure why at the moment.

---

### Post by mgf on 2012-05-09
Thanks, all the steps in post #9 generally worked, but there were a couple of quirks that may be useful for others to know.

My hardware is a HP probook 4730s, which lspci reports as having a ralink 3592 card.  I went to ralink website at the link above to get correct drivers for me, which is where things are not quite as straightforward as they could be.  After digging a bit for one OK for 3592, and following the steps outlined above, I ended up building and linking to a 3562 driver, which was how it was denoted within the archive, which was a bit confusing. 

The readme included in the archive was also a bit iffy, suggesting commands that can not be done as the directories referred to don't exist. neilhuang's instructions are better.

I did have to do sudo make, not just make. Then just take care with the directories and filenames in the later steps so they correct for your setup. 

Works great now. Ta Muchly.

---

### Post by Bushi86 on 2012-05-09
> **neilhuang said:**
> I'm curious as to why you have 
```

rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib

```so many modules using all these drivers. I suspect that this causes the drivers conflict. 

You can try to do a modinfo on the modules (left column) to find more information. 

Try [this]("http://ubuntuforums.org/showthread.php?p=5028400") to see if it helps... I'm not exactly sure why at the moment.

So I was able to remove all of them and then insmod the rt2860sta.ko, but the connection is still not working (connected to network, but no Internet). rt2860 is the only module showing up:
```

$ lsmod | grep rt2
rt2860sta             864748  0 

```

BTW, I had to reinstall Ubuntu yesterday, so I repeated everything on a fresh OS and am still getting the same results. However, I did notice one difference. Whenever I downloaded the drivers from Ralink site, they were corrupted and wouldn't extract. So I've been using the drivers from Rosewill (my wifi card manufacturer) this whole time. They are the exact same tar as far as I could tell, except that all of the changes needed in the Makefile were already there.

Would it be possible for anyone to share the Ralink drivers, or at least their Makefile? Thanks!

---

### Post by mathfreak on 2012-05-10
I'm experiencing the same problems as the OP. My card was working perfectly under 11.10, but after upgrading to 12.04 my wifi will start cutting out every 10 to 15 minutes. I switched to the RAlink drivers (rt2860sta) but am still experiencing the same issues.

My card is a Rosewill RNX-N300X

Here's the ouput of 'lspci -k|grep -i network --after-context 3'

```

03:05.0 Network controller: Ralink corp. RT2800 802.11n PCI
	Subsystem: Ralink corp. Device 2860
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta, rt2800pci

```

Here's the end of my dmesg after it cuts out.

```

[13564.593665] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[13564.593707] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[13564.601494] RX DESC ffff8800c7813000  size = 2048
[13564.605401] Key1Str is Invalid key length(0) or Type(0)
[13564.605410] Key2Str is Invalid key length(0) or Type(0)
[13564.605418] Key3Str is Invalid key length(0) or Type(0)
[13564.605426] Key4Str is Invalid key length(0) or Type(0)
[13564.605546] 1. Phy Mode = 5
[13564.605547] 2. Phy Mode = 5
[13564.621514] phy mode> Error! The chip does not support 5G band 1!
[13564.621568] RTMPSetPhyMode: channel is out of range, use first channel=1 
[13564.629780] 3. Phy Mode = 9
[13564.634395] MCS Set = ff ff 00 00 01
[13564.634397] <==== rt28xx_init, Status=0
[13564.634464] 0x1300 = 000a4300
[13564.643464] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13564.643474] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13564.644152] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13564.644161] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13564.645825] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13564.645834] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13566.629713] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 2288
[13566.629948] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[13566.851945] Rcv Wcid(1) AddBAReq
[13566.851949] Start Seq = 00000000
[13577.600013] ra0: no IPv6 routers present
[13592.857209] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[13592.857245] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[13592.864828] RX DESC ffff8800c7813000  size = 2048
[13592.868724] Key1Str is Invalid key length(0) or Type(0)
[13592.868732] Key2Str is Invalid key length(0) or Type(0)
[13592.868740] Key3Str is Invalid key length(0) or Type(0)
[13592.868748] Key4Str is Invalid key length(0) or Type(0)
[13592.868868] 1. Phy Mode = 5
[13592.868869] 2. Phy Mode = 5
[13592.884854] phy mode> Error! The chip does not support 5G band 1!
[13592.884905] RTMPSetPhyMode: channel is out of range, use first channel=1 
[13592.893123] 3. Phy Mode = 9
[13592.897631] MCS Set = ff ff 00 00 01
[13592.897633] <==== rt28xx_init, Status=0
[13592.897700] 0x1300 = 000a4300
[13592.903676] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13592.903685] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13592.904383] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13592.904394] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13594.861697] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 2782
[13594.861876] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[13595.114614] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13595.114624] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13595.115393] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13595.115402] /home/chris/src/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
[13597.177692] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3135
[13597.178074] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[13597.368767] Rcv Wcid(1) AddBAReq
[13597.368771] Start Seq = 00000000
[13601.881130] Rcv Wcid(1) AddBAReq
[13601.881133] Start Seq = 00000002
[13605.392015] ra0: no IPv6 routers present
[13638.310715] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3191
[13698.418728] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 2935
[13778.546744] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3229
[13878.694746] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 2630
[13898.726607] ACT - Update2040CoexistFrameAndNotify. BSSCoexist2040 = 1. EventANo = 3. 
[13898.726611] ACT - BuildIntolerantChannelRep , Total Channel number = 1 
[13898.726613] ACT - BuildIntolerantChannelRep , Total Channel number = 2 
[13898.726614] ACT - BuildIntolerantChannelRep , Total Channel number = 3 
[13898.726615] ACT-BuildIntolerantChannelRep(Size=6)
[13898.726708] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3362

```

Any suggestions?

---

### Post by Bushi86 on 2012-05-10
> **mathfreak said:**
> My card is a Rosewill RNX-N300X

I've got the exact same card and the exact same issues! Not sure if I'm getting the same/similar errors in dmesg, but I can check when I get home.

I've been trying to fix this all week, but I can't seem to get it.

---

### Post by sladner84 on 2012-05-10
I did everything stated and this is my output of 

steven@UbuntuDesktop:/etc/Wireless/RT2860STA$ lsmod | grep rt
rt2860sta             864748  0 
parport_pc             32866  0 
parport                46562  3 parport_pc,ppdev,lp

did I do something wrong?

---

### Post by mathfreak on 2012-05-10
> **Bushi86 said:**
> I've got the exact same card and the exact same issues! Not sure if I'm getting the same/similar errors in dmesg, but I can check when I get home.

I've been trying to fix this all week, but I can't seem to get it.

I switched over to ndiswrapper and everything seems to be pretty stable so far. If you're curious, I basically followed the instructions [here]("http://ubuntuforums.org/showpost.php?p=9289963&postcount=1"). The only real change I did was to create a file /etc/modprobe.d/blacklist-wlan.conf that contains the lines

```

blacklist rt2800pci
blacklist rt2860sta
```

Then when I rebooted it worked. It's been stable so far with no cutting out. I'll see how it continues.

---

### Post by Bushi86 on 2012-05-11
OK now I'm just confused. I went ahead and bought a 3RD wifi card (this one is a D-link DWA-556 with an Atheros chipset) to try out, and it's acting the exact same! I decided to give up for the day and boot back into Windows, and I'm having the same symptoms there!? For science, I shut down and threw my old card back in (the RNX-N300NX) to see if it was still working in Windows, but it was acting the same!

I should mention that I've also tried two different routers, so I don't think that's the issue. My laptop (Macbook Pro running OS 10.7.4) has 100% reception on my computer desk, so it's not a problem with range...wifi on my desktop was running perfectly fine in Windows before I added a new SSD and dual-booted Ubuntu.

WTF is going on?? I'm going to start a new thread since my issue seems to be bigger than the Ralink 2800 modules.

---

### Post by mathfreak on 2012-05-11
> **mathfreak said:**
> I switched over to ndiswrapper and everything seems to be pretty stable so far. If you're curious, I basically followed the instructions [here]("http://ubuntuforums.org/showpost.php?p=9289963&postcount=1"). The only real change I did was to create a file /etc/modprobe.d/blacklist-wlan.conf that contains the lines

```

blacklist rt2800pci
blacklist rt2860sta
```

Then when I rebooted it worked. It's been stable so far with no cutting out. I'll see how it continues.

Well, the ndiswrapper driver is exhibiting the same behavior. I'm beginning to suspect that it's just a huge coincidence and not realted to 12.04. Ugh.

---

### Post by mathfreak on 2012-05-15
> **mathfreak said:**
> Well, the ndiswrapper driver is exhibiting the same behavior. I'm beginning to suspect that it's just a huge coincidence and not realted to 12.04. Ugh.

Actually, that may have been a hiccup in the router. I've stress tested my wireless for four days and haven't had a another problem. It appears that using ndiswrapper solved this for me.

---

### Post by hernacar on 2012-06-15
Hi, neilhuang, just wanted to thank you for posting the solution to my issue. I followed the steps you posted and it worked right away. I also took the liberty of linking the post and copying the steps in my personal blog so I could reference this information quicker in the future (giving you full credit for actually doing the research and stuff :) ).

Thanks again for your help!

---

### Post by neilhuang on 2012-06-26
Sure. No problem.

For those who don't have this scripted yet,  I've posted a script that I currently use.
No guarantees, but I run it everytime my Ubuntu updates the kernel and breaks my wireless. 

It follows my previous post #9 pretty much line by line. 
Feel free to tweak it to your heart's content to make it work the way you want. 

Just a few pre-req's that the script assumes:
1. The wireless driver of RT2860STA has already been downloaded and extracted at /home/________/wireless_card_driver
2. You've tried the steps manually first to understand how the process works and to get it working so you can fix the script to make it work for yourself for the future.

Blessings,
-Neil

---

### Post by Skybolt83JL on 2012-06-29
Does anyone have the rt2860sta driver working on kernel 3.2.0-25 x86_64?

It will load ok without the nic installed, but locks my system up hard with the nic in place.

---

### Post by neilhuang on 2012-08-01
Not sure who still uses this driver, but I find it to be the root cause of a lot of my system freezes. 

For now, I've removed the blacklist on the original wireless driver and using that. It seems to work fine now. 

At least, it doesn't cause my system to freeze anymore. Will need to dig deeper.

---

### Post by txavi on 2012-08-30
Ok.

[http://ubuntuforums.org/showthread.php?t=1958059](http://ubuntuforums.org/showthread.php?t=1958059)

---

### Post by bearman83 on 2012-10-24
Just a small update with relationship to this post.

So on ubuntu 12.04 i had to use the solution provided by neilhuang and install the rt2860sta driver which worked just fine. The standard rt2800pci driver would drop and disconnect continously.

Two days ago i upgraded to quantal and i noticed that rt2800pci is still standard, so i proceeded to install the rt2860sta driver. But with that driver i got lockups and kernel panics related to graphics so i removed it and tried out the standard rt2800pci driver instead.
And so far it's been working just fine.

So i'm not sure if the driver is finally working as it should. Anyone else noticed this now working as it should out of the box, or did you have to install the rt2860sta driver instead?

My card is a linksys wmp600n.

---

### Post by Geof3010 on 2012-11-17
Hi there:

I was pretty happy to find this thread since I am having the exact same problem as you describe here.. I just installed linux mint 13 and my wireless connection is very unstable. I actually found out that this was happening only with WIFI N mode, not when I use the B/G mode.

I have the RT2800PCI module installed and I want to follow the instruction to install the one that worked for you, but when I follow the link for ralink website and after downloading the file, I cannot decompress it: the archive manager gives me this error:

An error occurred while loading the archive

Command Line Output:
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now

Any idea how I can overcome this problem ??

Thanks a lot !!

---

### Post by neilhuang on 2012-11-18
Weird... I tried just now and saw the same error.
I've uploaded my local copy of the wireless driver for you here temporarily.

[http://ubuntuone.com/7gQxrha6oUiVwPzaXRQFIh](http://ubuntuone.com/7gQxrha6oUiVwPzaXRQFIh)

That's the one I have that I used in my original solution post. Let me know if this helps.

---

### Post by bearman83 on 2012-11-19
I think i got the same problem with the extraction and i think i concluded that it was mislabelled as a bz2-file even though it weren't. Extract with "tar -xvf filename" and it should work.

---

### Post by Geof3010 on 2012-11-21
neilhuang: YOU ARE THE MAN !!!

One of my friend helped me with the ralink driver: he actually decompressed the file with 7zip, under windoze...

Once I had the driver, I followed your instructions: the instability problem with the WIFI N mode was fixed instantly !! And to my surprise, I also noted that the quality of the wireless link greatly improved after I installed the RT2860STA module. Before, the maximum link quality I was getting was 50% and now I am almost all the time at 96% ! Impressive !!

Thanks a lot for your help !!!

---

### Post by azdavef on 2013-01-18
On a kernel upgrade you will indeed need to repeat step 9, then steps 12-15. I just upgraded to -36 and wireless did not work at all on reboot until I repeated step 9.  Steps 12-15 to keep it.  You do need to remember to change code references to the kernel (in my case -36)you now have

---

### Post by adri76 on 2013-06-10
Hi, I'm a new member (from Italy, so please forgive my language errors), using Ubuntu from 2 years, but i'm a newbie with problem of network (and with many other things). 
My release is Rarin Ringtail, and I've got the problem of ralink2800.
I'm trying to follow the guide at the first page of this thread ([http://ubuntuforums.org/showthread.php?t=1958059&p=11858549#post11858549](http://ubuntuforums.org/showthread.php?t=1958059&p=11858549#post11858549)).
I can follow the guide up to point 5, but I don't understand when the guide says: "run make from the prompt".
Which command should I write on terminal? 
According to "man make" I tried to run "make" in the folder Download/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux, but the output is:

*"make: *** Nessun obiettivo specificato e nessun makefile trovato.  Arresto."* 
Translated: *"No target specified and no makefile found. Arrest."*.

It's strange, because there are two makefile in that folder: "Makefile4" and "Makefile6".
Can you help me to understand?


PS: I extracted the archive in "Download" folder.

---

### Post by neilhuang on 2013-06-11
Please make sure that you've downloaded the correct Linux Drivers, not Windows.
Once you've extracted the contents, you should see a file called "Makefile" inside of that directory. If you don't, you may have downloaded the wrong package.

I just checked the website again. It seems that they've made things a little more confusing, but should still be there. The driver is under GNU so I've posted it here.

---

### Post by adri76 on 2013-06-15
Forgive me for my late answer.
The driver I donwloaded was on "Linux" section, I'm sure of it.
But I checked in "connection information" menu, and i saw that the driver rt2800pci was already installed in my release (Ubuntu 13.04).
Because of the connection problem was persisting, i run "lspci" to see the correct driver i should install on my pc.
The output is: 

```
ambra@kina:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0  VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
ambra@kina:~$ 

```

Now I'm not sure if the driver rt2800pci is correct for my wi-fi card.
So i downloaded another driver: "2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2".

Do you think it's the correct driver for my wi-fi card?
My problem is that, following the istructions of the file "readme", I'm not able to configure it... 
And another dubt is that the problem is in the kernel as described in this page: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1171281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1171281)

In any case, i'll put here the text of the file "readme_STA_pci":

```
* README
*
* Ralink Tech Inc.
* 
* http://www.ralinktech.com
*

=======================================================================
ModelName:
===========
RT2860 Wireless Lan Linux Driver


=======================================================================
Driver lName:
=============
rt2860.o/rt2860.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2860 ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile            : Makefile
*.c                    : c files
*.h                    : header files


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make            
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    
6> load driver
    #[kernel 2.4]
    #    $/sbin/insmod rt2860sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2860sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt2860sta
    
=======================================================================
CONFIGURATION:  
====================
RT2860 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)modify configuration file "RT2860STA.dat" in /etc/Wireless/RT2860STA/RT2860STA.dat.
           
Configuration File : RT2860STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT2860STA/RT2860STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi -b rt61sta.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.
# 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0

-----------------------------------------------
*NOTE:
    WMM parameters
            WmmCapable            Set it as 1 to turn on WMM Qos support                
            AckPolicy1~4        Ack policy which support normal Ack or no Ack
                                (AC_BK, AC_BE, AC_VI, AC_VO)        
    
    All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡&#352;¡&#352;, 
    please store all parameter to RT2860STA.dat, and restart driver.     

-----------------------------------------------
syntax is 'Param'='Value' and describes below. 

@> CountryRegion=value                                 
    value
        0: use 1 ~ 11 Channel
        1: use 1 ~ 13 Channel
        2: use 10 ~ 11 Channel
        3: use 10 ~ 13 Channel
        4: use 14 Channel
        5: use 1 ~ 14 Channel
        6: use 3 ~ 9 Channel
        7: use 5 ~ 13 Channel
       31: use 1 ~ 14 Channel (ch1-11:active scan, ch12-14 passive scan)
                                                  
@> CountryRegionABand=value                                  
    value    
        0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
        1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
        2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
        3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
        4: use 149, 153, 157, 161, 165 Channel
        5: use 149, 153, 157, 161 Channel
        6: use 36, 40, 44, 48 Channel
        7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
        8: use 52, 56, 60, 64 Channel
        9: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 132, 136, 140, 149, 153, 157, 161, 165 Channel
       10: use 36, 40, 44, 48, 149, 153, 157, 161, 165 Channel
       11: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 149, 153, 157, 161 Channel

@> CountryCode=value
    value
        AG, AR, AW, AU, AT, BS, BB, BM, BR, BE, BG, CA, KY, CL, CN, CO, CR, CY, CZ, DK, DO, EC, SV, FI, FR, DE, 
        GR, GU, GT, HT, HN, HK, HU, IS, IN, ID, IE, IL, IT, JP, JO, LV, LI, LT, LU, MY, MT, MA, MX, NL, NZ, NO,
        PE, PT, PL, RO, RU, SA, CS, SG, SK, SI, ZA, KR, ES, SE, CH, TW, TR, GB, UA, AE, US, VE
        "" => using default setting: 2.4 G - ch 1~11; 5G - ch 52~64, 100~140, 149~165
                                                           
@> SSID=value                    
    value
        0~z, 1~32 ascii characters.
                        
@> WirelessMode=value
    value    
        0: legacy 11b/g mixed 
        1: legacy 11B only 
        2: legacy 11A only         //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
        3: legacy 11a/b/g mixed     //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
        4: legacy 11G only
        5: 11ABGN mixed
        6: 11N only
        7: 11GN mixed
        8: 11AN mixed
        9: 11BGN mixed
       10: 11AGN mixed    
                     
@> Channel=value
    value
        depends on CountryRegion or CountryRegionABand
                        
@> BGProtection=value
    value
        0: Auto 
        1: Always on 
        2: Always off
                        
@> TxPreamble=value
      value
        0:Preamble Long
        1:Preamble Short 
        2:Auto
                        
@> RTSThreshold=value
    value
        1~2347                                                       
                                                               
@> FragThreshold=value
    value           
        256~2346
                        
@> TxBurst=value
    value
        0: Disable
        1: Enable

@> NetworkType=value                
    value 
        Infra: infrastructure mode
           Adhoc: adhoc mode
                                                                                                                                                                                                                      
@> AuthMode=value
    value
        OPEN         For open system    
        SHARED          For shared key system    
        WEPAUTO     Auto switch between OPEN and SHARED
        WPAPSK      For WPA pre-shared key  (Infra)
        WPA2PSK     For WPA2 pre-shared key (Infra)
        WPANONE        For WPA pre-shared key  (Adhoc)
        WPA         Use WPA-Supplicant
        WPA2        Use WPA-Supplicant

@> EncrypType=value
    value
        NONE        For AuthMode=OPEN                    
        WEP            For AuthMode=OPEN or AuthMode=SHARED 
        TKIP        For AuthMode=WPAPSK or WPA2PSK                    
        AES            For AuthMode=WPAPSK or WPA2PSK                     
        
@> DefaultKeyID=value
    value
        1~4

@> Key1=value
    Key2=value
    Key3=value
    Key4=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
    (usage : "iwpriv" only)     

@> Key1Type=vaule
    Key2Type=value
    Key3Type=vaule
    Key4Type=vaule
    value
        0   hexadecimal type
        1   assic type
    (usage : reading profile only)

@> Key1Str=value
    Key2Str=value
    Key3Str=vaule
    Key4Str=vaule
    value
        10 or 26 characters (key type=0)
        5 or 13 characters  (key type=1)
    (usage : reading profile only)    

@> WPAPSK=value                  
    value
        8~63 ASCII          or 
        64 HEX characters
                                                                                                                                                            
@> WmmCapable=value
    value
        0: Disable WMM
        1: Enable WMM
        
@> PSMode=value
    value
        CAM                Constantly Awake Mode
        Max_PSP            Max Power Savings
        Fast_PSP        Power Save Mode

@> FastRoaming=value
    value
        0                Disabled
        1                Enabled

@> RoamThreshold=value
    value
        Positive Interger(dBm)

@> HT_RDG=value
    value
        0                Disabled
        1                Enabled

@> HT_EXTCHA=value (Extended Channel Switch Announcement)
    value
        0                Below
        1                 Above

@> HT_OpMode=value
    value
        0                HT mixed format
        1                HT greenfield format

@> HT_MpduDensity=value
    value (based on 802.11n D2.0)
        0: no restriction
        1: 1/4 £gs
        2: 1/2 £gs
        3: 1 £gs
        4: 2 £gs
        5: 4 £gs
        6: 8 £gs
        7: 16 £gs

@> HT_BW=value
    value
        0                20MHz
        1                40MHz

@> HT_AutoBA=value
    value
        0                Disabled
        1                Enabled

@> HT_BADecline
    value
        0                Disabled
        1                Enabled <Reject BA request from AP>

@> HT_AMSDU=value
    value
        0                Disabled
        1                Enabled

@> HT_BAWinSize=value
    value
        1 ~ 64

@> HT_GI=value
    value
        0                long GI
        1                short GI

@> HT_MCS=value
    value
        0 ~ 15
        33: auto

@> HT_MIMOPSMode=value
    value (based on 802.11n D2.0)
        0                Static SM Power Save Mode
        1                Dynamic SM Power Save Mode
        2                Reserved
        3                SM enabled
    (not fully support yet)

@> EthConvertMode=value
    value
        dongle
        clone
        hybrid

@> EthCloneMac=value
    value
        xx:xx:xx:xx:xx:xx
        
@> IEEE80211H=value
    value
        0                Disabled
        1                Enabled

@> TGnWifiTest=value
    value
        0                Disabled
        1                Enabled

@> WirelessEvent=value
    value
        0                Disabled
        1                Enabled <send custom wireless event>
        
@> MeshId=value
    value
        Length 1~32 ascii characters

@> MeshAutoLink=value
    value
        0                Disabled
        1                Enabled

@> MeshAuthMode=value
    value
        OPEN         For open system    
        WPANONE        For WPA pre-shared key  (Adhoc)

@> MeshEncrypType=value
    value
        NONE        For MeshAuthMode=OPEN                    
        WEP            For MeshAuthMode=OPEN
        TKIP        For MeshAuthMode=WPANONE
        AES            For MeshAuthMode=WPANONE

@> MeshWPAKEY=value
    value
        8~63 ASCII          or 
        64 HEX characters

@> MeshDefaultkey=value
    value
        1~4

@> MeshWEPKEY=value
    value
        10 or 26 characters
        5 or 13 characters

@> CarrierDetect=value
    value
        0                Disabled
        1                Enabled

MORE INFORMATION
=================================================================================
If you want for rt2860 driver to auto-load at boot time:
A) choose ra0 for first RT2860 WLAN card, ra1 for second RT2860 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2860sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'     


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
    add the line
    GATEWAY=x.x.x.x   
    in /etc/sysconfig/network
   
=======================================================================
Dongle/Clone Features:
======================
A) Dongle mode: 
       Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
       can transparently connect to the AP.

B) Clone mode:
    Provides a 1-to-1 MAC address mapping mechanism. 
    STA can use own MAC as SA MAC or 
            use user desired MAC as SA MAC or
            use source MAC of first packet coming from wired device as SA MAC.
    NOTE: In this mode, only the PC who own the specified MAC can connect to the AP.

 
C) Hybrid mode(Dongle+Clone):
    Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
       can transparently connect to the AP.
    STA can use own MAC as SA MAC or 
            use user desired MAC as SA MAC or
            use source MAC of first packet coming from wired device as SA MAC.

D) Please refer to "Config STA to link as dongle mode..." in iwpriv_usage.txt for releated commands.
```

Can you please help me to understand how to configure this driver?

---

### Post by neilhuang on 2013-06-18
> Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe

Not sure if this card is compatible. I'm not an hardware chipset expert... but the mdoel seems different enough.

---

### Post by expositojorge on 2013-08-20
Hello I'm kinda new to this, I've followed all the steps and finally it worked, but now everytime I boot up everything freezes up completely, any ideas?
Ubuntu 12.04LTS

---

