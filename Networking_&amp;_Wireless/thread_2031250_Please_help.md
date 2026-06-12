---
title: "Please help"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by Harkawy on 2012-07-21
I purchased a used Tablet PC (made in China) that had Windows 7 as its OS. The OS had WiFi and connected to my LAN.  It also had bluetooth capabilities.   I found that the hdd was partitioned into 4 drives; C, D, E and F.  
Like a fool that I am, I failed to backup the drive.  I removed the two lower drives and enlarged drive d.  Then I set drive C to "Compress this drive to save space."  Once the update completed, I attempted to reboot but I kept receiving an error message stating that "Bootmgr has been compressed.  Press Ctl-Alt-Delete to reboot."  After a few days of frustration, I reinstalled Windows 7 only to find that the device no longer recognized the wifi or bluetooth devices and I was unable to locate any driver for the wifi.  Within the System/Device Manager/Unknown Devices, it shows four items:
[LIST=1]
[*]Unknown Device
[*]Video Controller
[*]WiFi USB Dongle
[*]Wifi USB Dongle
[/LIST]
I attempted to install all kinds of drivers for the Wifi but nothing functioned.

So.... I downloaded and created a bootable memory stick and then installed the latest version of Ubuntu on the device in hopes that the Ubuntu OS would recognize the unknown devices....  But it didn't.  I attempted from the Terminal, the commands lspci -v and lspci -nn in hopes of seeing what the Wifi device is so that I could download drivers for it, but nothing showed up relating to the wifi or bluetooth devices.

With all this, I come here in hopes that someone... anyone, can either provide me with information, recommend drivers or provide me with some method of determining what the wifi device is so that I can get this little PC functioning properly.

---

### Post by wildmanne39 on 2012-07-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Harkawy on 2012-07-21
Thank you, wildmanne39

cat /etc/lsb-release; uname -a
[INDENT]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux LilBunny 3.2.1-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012
i686 i686 i386 GNU/Linux[/INDENT]
lspci -nnk | grep -iA2 net
[INDENT]Nothing was returned[/INDENT]
lsusb
[INDENT]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e1:0100 Syntek Semiconductor Co., Ltd 802.11g + Bluetooth Wireless Adapter
Bus 001 Device 005: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 003: ID 20b3:0a18 Hanvon 10.1 Touch screen overlay
Bus 001 Device 006: ID 0bda:5801 Realtek Semiconductor corp.
Bus 001 Device 009: ID 04f2:0841 Chicony Electronics Co., Ltd[/INDENT]
iwconfig
[INDENT]lo    no wireless extensions.[/INDENT]
rfkill list all
[INDENT]Nothing returned[/INDENT]
lsmod
[INDENT]Module			Size 	Used by
joydev			17393 	0
hid-multitouch		12851 	0
snd_hda_codec_realtek	174055 	1
snd_hda_intel		32765 	3
snd_hda_coded		109562 	2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep		13276 	1	snd_hda_codec
snd_pcm			80845 	2 snd_hda_intel,snd_hda_codec
snd_seq_midi		13132 	0
snd_rawmidi		25424 	1 snd_seq_midi
snd_seq			51567 	2 snd_seq_nidi,snd_seq_midi_event
uvcvideo		67203 	0
videodev		86588 	1 uvcvideo
snd_timer		28931 	2 snd-pcm,snd-seq
snd-seq_device		14172 	3 snd_seq_midi_,snd_rawmidi,snd_seq
usbhid			41906 	1 hid_multitouch
rfcomm			38139 	0
bnep			17830 	2
hid			77367 	2 hid_multitouch,usbhid
bluetooth		158438 	10 rfcomm,bnep
snd			62064 	15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_deq_divice
parport_pc		32114 	0
ppdev			12849 	0
i915			414603 	3
drm_kms_helper		45466 	1 i915
drm			197692 	4 i915,drm_kms_helper
i2c_algo_bit		13199 	1 i915
soundcore		14635 	1 snd
snd_page_alloc		14108 	2 snd_hda_intel,snd_pcm
video			19068 	1 i915
mac_hid			13077 	0
lp			17455 	0
Parport			40930 	3 parport_pc,ppdev,lp[/INDENT]

---

### Post by wildmanne39 on 2012-07-21
Hi, I do not see a wireless device.

Are you using a usb adapter still? if so please make sure it is plugged in then post the output of:
```
lsusb
``` 
if it is internal please check in the bios and make sure wireless lan is enabled then post the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by Harkawy on 2012-07-21
It looks like you missed it...

susb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 1.1 root hub
**Bus 001 Device 004: ID 05e1:0100 Syntek Semiconductor Co., Ltd 802.11g + Bluetooth Wireless Adapter**

---

### Post by wildmanne39 on 2012-07-21
Hi, no I saw that but you did not say it was a bluetooth device, I am not sure if I can help with a bluetooth device but I will try, is it an internal or usb adapter that you plug in?
Thanks

---

### Post by NikTh on 2012-07-21
Hi , 
I think our friend here has deal the same situation as in this thread --> [http://ubuntuforums.org/showthread.php?t=1815093](http://ubuntuforums.org/showthread.php?t=1815093) , 
i am not sure , but seems that this device its something like mix wireless and bluetooth. 

Thanks

---

### Post by wildmanne39 on 2012-07-21
Hi NikTh, I know I read that thread before posting my last reply but I sure hate to go that route because that driver is not for 12.04 and there would have to be modifications, so I am trying to see if there is a better solution for 12.04.
Thanks

---

### Post by NikTh on 2012-07-21
Hi wildmanne39 , 
just tried to help , furthermore this problem is beyond my knowledge and experience .

I will not address the issue , but will watch to see developments. 

Thanks

---

### Post by wildmanne39 on 2012-07-21
Hi NikTh, you are correct and a search does not look promising without a lot of modifications, I appreciate the help and you are always welcome to post in my threads.
Thanks

---

### Post by Harkawy on 2012-07-22
Thank you all for your assistance.
Based upon the SUSB listing; Syntek Semiconductor Co., Ltd 802.11g + Bluetooth Wireless Adapter, the device is a chip that sits on the motherboard.  I went to the Syntek Semiconductor web site and did a search for all possible Wifi/Bluetooth adapters and found two that I thought would work, one for Ubuntu and one for Windows 7 so I downloaded them.  The one for Ubuntu was a script.  Since I have been a user of Microsoft's operating systems for more than 25 years and brand new to Ubuntu, I couldn't figure out how to activate the script as I clicked on it and it seemed to open in a text box.

Since I installed Ubuntu as a co-operating system, I booted back into Windows 7 and was able to install the drivers and the little toy was now seeing the LAN.  

So, how do I execute the script under Ubuntu?

---

### Post by wildmanne39 on 2012-07-22
Hi, please post a link to the script you are talking about.
Thanks

---

### Post by Harkawy on 2012-07-22
The file is located at:  [http://www.stk.com.tw/product-01.asp?Product_Type=58]("http://www.stk.com.tw/product-01.asp?Product_Type=58") under item 1.USB dongle/USB miniCard

[http://www.stk.com.tw/driver/Wireless/Release_ForUSBLinux/Ubuntu/BlueW-2310U_2.4.4_100823_Ubuntu10.04_withouthotkey.tar.gz]("http://www.stk.com.tw/driver/Wireless/Release_ForUSBLinux/Ubuntu/BlueW-2310U_2.4.4_100823_Ubuntu10.04_withouthotkey.tar.gz")

---

### Post by wildmanne39 on 2012-07-22
Hi, yes that is the one I looked at last night and it is for 10.04 we might can get it to work in 12.04 but it will not be easy.

Can you look in windows and tell me the name of the driver you are using in it?
Thanks

---

### Post by Harkawy on 2012-07-23
> **wildmanne39 said:**
> Hi, yes that is the one I looked at last night and it is for 10.04 we might can get it to work in 12.04 but it will not be easy.

Can you look in windows and tell me the name of the driver you are using in it?
Thanks

Device Manager
[INDENT]Network adapters
[indent]3DSP Wireless 802.11 B+G USB Adapter #2
Bluetooth PAN Network Adapter[/INDENT][/indent]
The drivers are:
[INDENT]
wlusb732.sys
btnetdrv.sys[/INDENT]

The link is [http://www.stk.com.tw/product-01.asp?Product_Type=58]("http://www.stk.com.tw/product-01.asp?Product_Type=58")
And the file is [2010-09-21] Wlan & IVT Bluetooth Driver for Win7 32Bit

---

### Post by wildmanne39 on 2012-07-23
Hi, I was checking with someone to see if he might rewrite the driver for 12.04 but he is not available.

So download the driver you need and the directions to install it is in the readme file that comes with the driver.

Here is a link to directions to get the driver to work hopefully, you  will need to read the complete thread because you will need to make some changes like put your kernel version where the old 10.04 kernel version is in the install script.
[http://ubuntuforums.org/showthread.php?t=1815093](http://ubuntuforums.org/showthread.php?t=1815093)
Thanks

---

### Post by Harkawy on 2012-07-24
Thank you for the information.  I'll do the reading and forge onward.

---

