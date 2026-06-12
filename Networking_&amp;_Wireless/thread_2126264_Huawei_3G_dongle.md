---
title: "Huawei 3G dongle"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by luigiD on 2013-03-16
I had no problem installing (through a live USB) the 64 bit Ubuntu 12.10 in an Asus laptop - model F55A-SX091D with >>

-- Pentium B980 (2,40 GHz, 2 MB Smart-Cache);
-- RAM: 4096MB DDR3-1333MHz;
-- Hard disk: 500GB S-ATA, 5.400 R/Min;
-- CD-ROM device: 8x DVD-Super Multi D/L Double Layer;
-- WLAN: 802.11 b/g/n;
-- Ethernet: 10/100/1000 MBit/s;
-- Card reader: 2-in-1 (MMC/ SD);
-- Graphical card: Intel HD;
-- VGA, HDMI;
-- Webcam: 0.3 Megapixel;
-- 1x USB 2.0, 1x USB 3.0;
-- battery: Li-Ion / 6 cells / 65 Watt;
-- SRS Premium Sound, Altec Lansing Lautsprecher, Multitouchpad.

Everything has been working fine from instant one, except for two issues I haven't been able to address.

ISSUE #1 - When I bouhgt the Asus laptop, it had free DOS software and, on installing Ubuntu, I opted for Ubuntu to wholly re-format the hard disk. In hindsight, that might have been a poor choice in that there was probably also proprietary Asus software for regulating screen brightness through the keyboard and other such controls. Now I have to do those operations with the facilities offered by the Ubuntu packages. No big issue.

ISSUE #2 - When I plug a memory stick into one of the USB ports, or an SD card into its reader, they are promptly recognized and I can transfer files from / to the laptop. But this does not happen when I plug a Huawei USB dongle for connecting to the 3G internet signal. Its plugging is squarely ignored by the system, as if nothing had been plugged. In addition to an autorun.exe for Microsoft Windows, this dongle also has a directory named "Linux", which houses the driver which supposedly makes it possible for me to use it with Ubuntu.

The Linux directory has these files:
-- data.bin
-- DataCard_Verify
-- install
-- MobilePartner.tar.gz
-- SysConfig.dat
Furthermore there is a readme.txt file which reads as follows:
QUOTE____*You need login as root*
1. Run "install" in TERMINAL to install MobilePartner
   eg: # bash /<path>/install
2. If you had installed this software in your system before, you will get a prompt: "The software is exist, do you want overwrites? ([Y]/[N])", enter "y" to overwrites or "n" to exit.
3. If you do not had installed this software in your system before, you will get a prompt: "Please input the install path[/usr/local/Mobile_Partner]:". Then you can input install path(fullpath), or you may using the default path(/usr/local/Mobile_Partner) by press ENTER direct
4. Finish installing
--How to run--------------------------
* From shortcut in desktop
* Run MobilePartner in your install path
   eg: # /<install path>/MobilePartner
* Plug in your device, it will run automatically(Not supported in Xandros)____UNQUOTE
I have copied the files into the Asus laptop, then I tried to double-click on "install" or, in terminal, to carry out the commands listed in the "readme" file --- to no avail. Nothing happened.
Any suggestions / clarifications? 

I did not log in as root (I understand Ubuntu advises against doing that), and have used SUDO instead. That is, in my attempts I worked with the $ prompt, not the #.
Also I was puzzled that the "readme" file mentions "Mobile_Partner" in the command it suggests and the tarred file has "MobilePartner" in its name. I typed the command with either spelling.
As you can see, I am a newbie with Linux and Unix in general; things like SUDO and the perils of being root I have just learned by canvassing the internet. Please bear with me.

---

### Post by praseodym on 2013-03-16
Hi,

you do not need the windows drivers. Install the package "usb-modeswitch" via software-center. Please plugin the stick and show the terminal outputs of
```

lsusb
usb-devices
lsmod
```

---

### Post by luigiD on 2013-03-17
> **praseodym said:**
> Hi,

you do not need the windows drivers. Install the package "usb-modeswitch" via software-center. Please plugin the stick and show the terminal outputs of
```

lsusb
usb-devices
lsmod
```

I did nor express myself clearly. 
The Huawei antenna for picking up the 3G signal and connecting to a USB port has inside two directories with the Windows drivers AND the Linux drivers. What I have been trying to do is installing the Linux driver which comes with the Huawei antenna.
Thank you anyway.

---

### Post by praseodym on 2013-03-17
You dont need the Linux driver either. The driver "option" is already part of the kernel.

Is you stick recognized as hard drive? If yes, unmount it.

---

### Post by luigiD on 2013-03-17
> **praseodym said:**
> You dont need the Linux driver either. The driver "option" is already part of the kernel.

Is you stick recognized as hard drive? If yes, unmount it.

Any other device (flash drive, memory stick, cables for recharging tablets / phones ...) is recognized as soon as I plug it, and an icon shows up on the left border of the screen. But not this bloody Huawey 3G antenna. 
When I plug it, nothing happens at all. 
I thought that installing the Linux software found inside it (and listed in my first message above) would make a difference.
Anything else works fine indeed, at an amazing speed. 
If you are wishing to also answer another, unrelated question? Is that right that no antivirus is needed when using Linux in a personal computer which is no part of a physical network?

---

### Post by luigiD on 2013-03-17
By ther way, when I searched "usb-modeswitch" in software-center, I was only shown the option to REMOVE it. So, it had already been installed. The first day, when the Ubuntu base installation completed, lots of stuff was updated and possibly added without me asking for that.

---

### Post by praseodym on 2013-03-17
Plz show the outputs from above

---

### Post by luigiD on 2013-03-18
This is the output of the above commands. The Huawei 3G stick was not plugged when I ran them. Please let me know if you need me to run the commands again after plugging it. The stick is labelled "Huawei Mobile Broadband HSPA+ USB Slider Model E1820".

   ~$ lsusb
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
 Bus 001 Device 003: ID 1bcf:2883 Sunplus Innovation Technology Inc.  
 

 ~$ usb-devices 
  
 T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
 P:  Vendor=1d6b ProdID=0002 Rev=03.05 
 S:  Manufacturer=Linux 3.5.0-25-generic ehci_hcd 
 S:  Product=EHCI Host Controller 
 S:  SerialNumber=0000:00:1a.0 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
 P:  Vendor=8087 ProdID=0024 Rev=00.00 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 0 
 D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1 
 P:  Vendor=1bcf ProdID=2883 Rev=04.29 
 S:  Manufacturer=04G626000611BQ2C5001JKD 
 S:  Product=ASUS USB2.0 Webcam 
 C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo 
 I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo 
  
 T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
 P:  Vendor=1d6b ProdID=0002 Rev=03.05 
 S:  Manufacturer=Linux 3.5.0-25-generic ehci_hcd 
 S:  Product=EHCI Host Controller 
 S:  SerialNumber=0000:00:1d.0 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
 P:  Vendor=8087 ProdID=0024 Rev=00.00 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
 P:  Vendor=1d6b ProdID=0002 Rev=03.05 
 S:  Manufacturer=Linux 3.5.0-25-generic xhci_hcd 
 S:  Product=xHCI Host Controller 
 S:  SerialNumber=0000:00:14.0 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0 
 D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1 
 P:  Vendor=15ca ProdID=00c3 Rev=05.12 
 S:  Product=USB Optical Mouse 
 C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid 
  
 T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4 
 D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1 
 P:  Vendor=1d6b ProdID=0003 Rev=03.05 
 S:  Manufacturer=Linux 3.5.0-25-generic xhci_hcd 
 S:  Product=xHCI Host Controller 
 S:  SerialNumber=0000:00:14.0 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
 

 ~$ lsmod 
 Module                  Size  Used by 
 parport_pc             32689  0  
 ppdev                  17074  0  
 rfcomm                 46620  0  
 bnep                   18141  2  
 bluetooth             209249  10 rfcomm,bnep 
 binfmt_misc            17501  1  
 nls_iso8859_1          12714  1  
 snd_hda_codec_hdmi     32049  1  
 snd_hda_codec_realtek    78147  1  
 ext2                   72881  1  
 joydev                 17458  0  
 coretemp               13401  0  
 ghash_clmulni_intel    13221  0  
 cryptd                 20404  1 ghash_clmulni_intel 
 asus_nb_wmi            12711  0  
 asus_wmi               24089  1 asus_nb_wmi 
 sparse_keymap          13891  1 asus_wmi 
 snd_hda_intel          33492  3  
 snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              17699  1 snd_hda_codec 
 uvcvideo               76750  0  
 videobuf2_core         32852  1 uvcvideo 
 snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 videodev              120310  2 uvcvideo,videobuf2_core 
 videobuf2_vmalloc      12861  1 uvcvideo 
 videobuf2_memops       13405  1 videobuf2_vmalloc 
 snd_seq_midi           13325  0  
 snd_rawmidi            30513  1 snd_seq_midi 
 snd_seq_midi_event     14900  1 snd_seq_midi 
 snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer              29426  2 snd_pcm,snd_seq 
 snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq 
 microcode              22804  0  
 arc4                   12530  2  
 rt2800pci              18529  0  
 rt2800lib              58731  1 rt2800pci 
 crc_ccitt              12708  1 rt2800lib 
 rt2x00pci              14476  1 rt2800pci 
 rt2x00lib              54939  3 rt2800pci,rt2800lib,rt2x00pci 
 wmi                    19071  1 asus_wmi 
 psmouse                95595  0  
 mac_hid                13206  0  
 mac80211              540032  3 rt2800lib,rt2x00pci,rt2x00lib 
 snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 serio_raw              13216  0  
 lpc_ich                17062  0  
 alx                    68240  0  
 mdio                   13808  1 alx 
 i915                  520615  3  
 cfg80211              206797  2 rt2x00lib,mac80211 
 eeprom_93cx6           13345  1 rt2800pci 
 drm_kms_helper         49113  1 i915 
 drm                   288721  4 i915,drm_kms_helper 
 i2c_algo_bit           13414  1 i915 
 soundcore              15048  1 snd 
 video                  19391  1 i915 
 mei                    40691  0  
 snd_page_alloc         18485  2 snd_hda_intel,snd_pcm 
 lp                     17760  0  
 parport                46346  3 parport_pc,ppdev,lp 
 hid_generic            12541  0  
 usbhid                 46987  0  
 hid                   100411  2 hid_generic,usbhid

---

### Post by praseodym on 2013-03-18
Please show the outputs, when the stick is plugged

P.S.: You may want to install antivirus software to protect others from "spamming" ;)

---

### Post by luigiD on 2013-03-19
> **praseodym said:**
> Please show the outputs, when the stick is plugged

P.S.: You may want to install antivirus software to protect others from "spamming" ;)
Additional information: 1) when connected to the Ubuntu machine, the Huawei stick flashes green or blue light (to signal the strength of the broadband it detects), the same way it does when plugged to a machine with MS Windows 7; 2) under Windows, it also displays an interface for monitoring the connection (current transfer speed, time elapsed, and more).
Here is the output of the commands with the Huawei stick plugged in.

                        ~$ lsusb 
 

 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 003 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800/E173 (HSPA modem) 
 Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
 Bus 001 Device 003: ID 1bcf:2883 Sunplus Innovation Technology Inc.  
 

 ~$ usb-devices 
 

 T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
 P:  Vendor=1d6b ProdID=0002 Rev=03.05 
 S:  Manufacturer=Linux 3.5.0-25-generic ehci_hcd 
 S:  Product=EHCI Host Controller 
 S:  SerialNumber=0000:00:1a.0 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
 P:  Vendor=8087 ProdID=0024 Rev=00.00 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 0 
 D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1 
 P:  Vendor=1bcf ProdID=2883 Rev=04.29 
 S:  Manufacturer=04G626000611BQ2C5001JKD 
 S:  Product=ASUS USB2.0 Webcam 
 C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo 
 I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo 
  
 T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
 P:  Vendor=1d6b ProdID=0002 Rev=03.05 
 S:  Manufacturer=Linux 3.5.0-25-generic ehci_hcd 
 S:  Product=EHCI Host Controller 
 S:  SerialNumber=0000:00:1d.0 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
 P:  Vendor=8087 ProdID=0024 Rev=00.00 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4 
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
 P:  Vendor=1d6b ProdID=0002 Rev=03.05 
 S:  Manufacturer=Linux 3.5.0-25-generic xhci_hcd 
 S:  Product=xHCI Host Controller 
 S:  SerialNumber=0000:00:14.0 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
  
 T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0 
 D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
 P:  Vendor=12d1 ProdID=1446 Rev=00.00 
 S:  Manufacturer=Huawei Technologies 
 S:  Product=HUAWEI Mobile 
 C:  #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA 
 I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none) 
 I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
  
 T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  2 Spd=1.5 MxCh= 0 
 D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1 
 P:  Vendor=15ca ProdID=00c3 Rev=05.12 
 S:  Product=USB Optical Mouse 
 C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid 
  
 T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4 
 D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1 
 P:  Vendor=1d6b ProdID=0003 Rev=03.05 
 S:  Manufacturer=Linux 3.5.0-25-generic xhci_hcd 
 S:  Product=xHCI Host Controller 
 S:  SerialNumber=0000:00:14.0 
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
 

 ~$ lsmod 
 

 Module                  Size  Used by 
 parport_pc             32689  0  
 ppdev                  17074  0  
 rfcomm                 46620  0  
 bnep                   18141  2  
 bluetooth             209249  10 rfcomm,bnep 
 binfmt_misc            17501  1  
 snd_hda_codec_hdmi     32049  1  
 nls_iso8859_1          12714  1  
 snd_hda_codec_realtek    78147  1  
 joydev                 17458  0  
 ext2                   72881  1  
 coretemp               13401  0  
 ghash_clmulni_intel    13221  0  
 cryptd                 20404  1 ghash_clmulni_intel 
 asus_nb_wmi            12711  0  
 asus_wmi               24089  1 asus_nb_wmi 
 sparse_keymap          13891  1 asus_wmi 
 microcode              22804  0  
 psmouse                95595  0  
 serio_raw              13216  0  
 uvcvideo               76750  0  
 videobuf2_core         32852  1 uvcvideo 
 videodev              120310  2 uvcvideo,videobuf2_core 
 videobuf2_vmalloc      12861  1 uvcvideo 
 videobuf2_memops       13405  1 videobuf2_vmalloc 
 wmi                    19071  1 asus_wmi 
 arc4                   12530  2  
 rt2800pci              18529  0  
 rt2800lib              58731  1 rt2800pci 
 crc_ccitt              12708  1 rt2800lib 
 rt2x00pci              14476  1 rt2800pci 
 rt2x00lib              54939  3 rt2800pci,rt2800lib,rt2x00pci 
 mac_hid                13206  0  
 mac80211              540032  3 rt2800lib,rt2x00pci,rt2x00lib 
 alx                    68240  0  
 cfg80211              206797  2 rt2x00lib,mac80211 
 eeprom_93cx6           13345  1 rt2800pci 
 mdio                   13808  1 alx 
 snd_hda_intel          33492  3  
 snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              17699  1 snd_hda_codec 
 snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 snd_seq_midi           13325  0  
 snd_rawmidi            30513  1 snd_seq_midi 
 snd_seq_midi_event     14900  1 snd_seq_midi 
 snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer              29426  2 snd_pcm,snd_seq 
 snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq 
 snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore              15048  1 snd 
 snd_page_alloc         18485  2 snd_hda_intel,snd_pcm 
 lpc_ich                17062  0  
 i915                  520615  3  
 mei                    40691  0  
 drm_kms_helper         49113  1 i915 
 drm                   288721  4 i915,drm_kms_helper 
 i2c_algo_bit           13414  1 i915 
 video                  19391  1 i915 
 lp                     17760  0  
 parport                46346  3 parport_pc,ppdev,lp 
 usb_storage            48839  0  
 hid_generic            12541  0  
 usbhid                 46987  0  
 hid                   100411  2 hid_generic,usbhid

---

### Post by praseodym on 2013-03-19
```
12d1:1446
``` is the storage mode```

T: Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 3 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=12d1 ProdID=1446 Rev=00.00
S: Manufacturer=Huawei Technologies
S: Product=HUAWEI Mobile
C: #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
I: If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=[COLOR="#FF0000"]usb-storage[/COLOR] 
```
Switch it via:
```

sudo usb_modeswitch -v 12d1 -p 1446 -M '55534243123456780000000000000011062000000100000000000000000000' 
```
You better copy/paste this line ;)

Did you install this:
```

sudo apt-get install usb-modeswitch
```

---

### Post by alexfish on 2013-03-19
H all

the device has switch
```

I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none) [COLOR=#008000]<< this is part of the modem[/COLOR] 
I: If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=[COLOR=#FF0000]usb-storage[/COLOR]

```

But not sure if all the bits are there , normal to see #EPs=3 to enable a connection,
can have a look at this thread
[http://ubuntuforums.org/showthread.php?t=1969322&page=2](http://ubuntuforums.org/showthread.php?t=1969322&page=2)
Do Know there used to be Two Swiching codes for Huawie , but also Know for Recent devices this code has changed ,
if Can get the Option Driver to bond with the device , and Modem Manager can not connect , the try ppp direct of wvdial , most of this info is in the thread

As mentioned , possible all parts of the device may not be revealed, Best option will be to Visit USB_MODESWITCH Forum , they are very helpful .
ADDED: Link to resent + possible Kernel Implications
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=2&t=1336](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=2&t=1336)

BR

Alex

---

### Post by luigiD on 2013-03-20
As I wrote at the outset, I know nothing about Linux and its command line. I am obviously worried about damaging a system which is performing extremely well.  

 

 I could not figure out the sense of “12d1:1446 ”, and terminal confirmed it is not something I had to type.  

 

 Right now I am connecting the Ubuntu laptop with another Huawei device which beams a wi-fi  hotspot all around. So if I cannot make the 3G stick work, I can still surf the internet with the Ubuntu machine (but the connection is not as strong).

 

 I see we can attach files to our forum messages. Would you be interested in looking into the *MobilePartner.tar.gz* pack which is inside the 3G Huawei stick (in its Linux directory)?

 

 Nor did I quite understand if Alexfish was giving me advice or was debating with praseodym.
 

 Anyway, here is the record of what I´ve done:

 

 ~$ 12d1:1446 
 

 12d1:1446: command not found
 

 ~$ sudo usb_modeswitch -v 12d1 -p 1446 -M '55534243123456780000000000000011062000000100000000000000000000' 
 

 Looking for default devices ... 
  No devices in default mode found. Nothing to do. Bye. 
 

 

 ~$ sudo apt-get install usb-modeswitch 
 

  Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 usb-modeswitch is already the newest version. 
 The following package was automatically installed and is no longer required: 
   linux-headers-3.5.0-17 
 Use 'apt-get autoremove' to remove it. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by luigiD on 2013-03-20
[RIGHT]Post Scriptum 
[/RIGHT]

Could you please confirm that, for removing linux-headers-3.5.0-17 (as requested in the output of "sudo apt-get install usb-modeswitch"), I should type the following line?
       sudo apt-get autoremove linux-headers-3.5.0-17

Thank you

---

### Post by praseodym on 2013-03-20
Did you copy/paste this line when the stick was plugged in?
```
sudo usb_modeswitch -v 12d1 -p 1446 -M '55534243123456780000000000000011062000000100000000000000000000'
```
For removing:
```
sudo apt-get autoremove
```
should do the trick

---

### Post by luigiD on 2013-03-20
Yes, I executed the command

sudo usb_modeswitch -v 12d1 -p 1446 -M '55534243123456780000000000000011062000000100000000000000000000'

when the Huawei 3G was plugged in.

---

### Post by praseodym on 2013-03-20
Please open two terminals. One:

First one:
```
tail -f /var/log/messages
```

Plugin the stick and start in the 2nd one
```
usb_modeswitch -H -v 12d1 -p 1446
```
Please show the output of the 1st one.

---

### Post by bmork on 2013-03-21
> **luigiD said:**
> Bus 003 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800/E173 (HSPA modem) 
 

I'd normally say that you need to install the usb-modeswitch package.

> 
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0 
 D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
 P:  Vendor=12d1 ProdID=1446 Rev=00.00 
 S:  Manufacturer=Huawei Technologies 
 S:  Product=HUAWEI Mobile 
 C:  #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA 
 I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none) 
 I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
  

But the "Driver=(none)" here makes me wonder if you already did that and it failed for some reason? If so, could you turn on logging in /etc/usb_modeswitch.conf  (edit it adding a line with 
```

EnableLogging=1

```
)
and post any resulting /var/log/usb_modeswitch_* file?

And please ignore the Huawei drivers on the stick.  You don't need those, and trying to make them work is more likely to create a mess than anything else.

---

### Post by luigiD on 2013-03-21
-------------------- I opened 2 terminals
 

 -------------------- In terminal 1, I typed >>
 

 ~$ tail -f /var/log/messages 
 

 tail: cannot open `/var/log/messages' for reading: No such file or directory 
 

 

 -------------------- I plugged the 3G stick into USB 3.0 (the other USB is 2.0); as usual, the 3G starts flashing
 

 

 -------------------- In terminal 2, I typed >>
 

 ~$ usb_modeswitch -H -v 12d1 -p 1446 


  
 Looking for default devices ... 
  No devices in default mode found. Nothing to do. Bye.

---

### Post by luigiD on 2013-03-21
This is a reply to bmork which I haven´t been able to send for some time because [http://ubuntuforums.org/](http://ubuntuforums.org/) crashed or went out of service just after I had reported to praseodym.

By now, I quite understand that the Linux software inside the stick is not to be used.

As to usb-modeswitch, that´s right: when I asked for its installation, the REMOVE request was made by Software Center.

Given my lack of knowledge / experience, it is hard for me to figure out how to log into usb-modeswitch. If you could present me with the typing to be done - the way praseodym has done above in his messages - I would be able to add that line.

Thank you to the three of you. Hopefully, we´ll get to the end of this.

---

### Post by alexfish on 2013-03-21
Hi  luigiD

You will not damage the system , if leave all packages as they are , removing them , will do no good at present , other than having to reinstall

if you are using usb_modeswith from the command line , use root :: 
Example:

```
sudo  usb_modeswitch -H -v 12d1 -p 1446
```

enter your password if prompted,

reason to post with reference to the kernel + link to usb_modswitch forum , noted that your system is based on " V3.5" .

for now try sudo , see what happens

Forgot to mention , do not install Huawei , drivers at present , They generall work well but will prevent modem manager from identifing the device, + the system logging us can be overwelming on Unity plaforms.

BR

Alex

---

### Post by luigiD on 2013-03-22
> **alexfish said:**
> Hi  luigiD

You will not damage the system , if leave all packages as they are , removing them , will do no good at present , other than having to reinstall

if you are using usb_modeswith from the command line , use root :: 
Example:

```
sudo  usb_modeswitch -H -v 12d1 -p 1446
```

enter your password if prompted,

reason to post with reference to the kernel + link to usb_modswitch forum , noted that your system is based on " V3.5" .

for now try sudo , see what happens

Forgot to mention , do not install Huawei , drivers at present , They generall work well but will prevent modem manager from identifing the device, + the system logging us can be overwelming on Unity plaforms.

BR

Alex

Thank you. I won't have access to my Ubuntu laptop until Monday, as I'm away for the week-end. By Monday or Tuesday I'll let you know if I've been successful in following your lead.

---

### Post by luigiD on 2013-03-27
0ver the last days the following warning kept appearing when I worked with my Ubuntu laptop:

 

 SYSTEM PROBLEM DETECTED
  Do you want to report now?
 

 Further info follows below, but the long and short of it is that after installing Ubuntu &#8211; about 2 weeks ago &#8211; functioning has been flawless until now. As I am not knowledgeable with Linux I haven´t tampered with the command line, except for executing the line commands suggested to me in the messages above.

 

 The warnings pop up so frequently that I am thinking of re-installing Ubuntu from scratch.

 

 Please, have a look at what I have copied below from those warnings. If you understand what went wrong, and can indicate the typing for restoring the previous system status, I shall be grateful.

 

 I won´t be able to add more messages for quite some time, because I am travelling soon. But, on my return, I will try out whatever you may have suggested to me.

 

 The lines below reproduce the content of the warnings, but no copy-and-paste was feasible. Instead, I had to jot down on paper what I saw. As a result, what you see below is likely not to be a faithful reproduction of what appears on my screen.  

 

 >>>>>>>>>>>>>>>>
 

 Sorry, Ubuntu 12.10 has experienced an internal error. If you noticew further error try restartting the computer.
 

 Apport has detected a possible CPU hang. Did your system recently lock up or require a hard reboot?
 

 ***I answered "No" to this. When I clicked on a button labelled "Show Details", a flood of text rushed in. Here you only find the beginning of it. ***

 

 Executable path
 /usr/share/apport/apport-gpu-error-intel-py
 Package
 xserver-xorg-video-intel:2.20.9.0ubuntu2
 Problem type
 Crash
 Title
 [sandybridge-m-gt1] False CPU lockup IPEHR 0xffffffff IPEHR : 0x0b140001
 .tmp.unity.support.test.0
 Apport version
 2.6.1-0ubuntu10
 Architecture
 amd64
 etc.

---

### Post by luigiD on 2013-04-07
It's only fair that I apologize for having perhaps given the impression the some typing proposed by forum members might have been faulty. 

After reinstalling Ubuntu 12.10, and without ever using terminal commands, warnings of the kind mentioned in my last post kept showing up.

Based on my experience, there is no reason to doubt the competence of volunteers who provide their help to beginners.

---

