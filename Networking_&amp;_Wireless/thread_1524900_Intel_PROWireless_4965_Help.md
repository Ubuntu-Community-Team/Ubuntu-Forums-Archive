---
title: "Intel PRO/Wireless 4965 Help"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by fskgoalie on 2010-07-05
i downloaded 10.04 yesterday and setup connection with minimal issues. i used the internet for a little bit and then restarted computer to switch back to vista. when i booted ubuntu again i i didnt connect. when i right click connection bar the option "enable wireless" is grayed out and i cannot click it. it says it is disabled. my wireless card is on the list of cards that work with ubuntu.

---

### Post by roosh on 2010-07-06
Hi,

Please open a terminal and type the following seperately and post back the output of each:
 ```
lspci
``` ```
lsusb
``` ```
lsmod
```

---

### Post by fskgoalie on 2010-07-06
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) 
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1) 
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) 
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02) 
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

---

### Post by fskgoalie on 2010-07-06
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 002: ID 413c:8133 Dell Computer Corp. Wireless 5720 VZW Mobile Broadband (EVDO Rev-A) Minicard GPS Port 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by fskgoalie on 2010-07-06
Module                  Size  Used by
binfmt_misc             7960  1
rfcomm                 40393  4
ppdev                   6375  0
sco                     9617  2
bridge                 53184  0
stp                     2171  1 bridge
bnep                   11884  2
l2cap                  34806  16 rfcomm,bnep
fbcon                  39270  71
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0
vgastate                9857  1 vga16fb
joydev                 11072  0
snd_hda_codec_idt      61450  1
usbhid                 41084  0
snd_hda_intel          25677  2
snd_hda_codec          85759  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1473  2
snd_seq_dummy           1782  0
snd_seq_oss            31219  0
snd_seq_midi            5829  0
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                121641  0
dell_wmi                2177  0
psmouse                64576  0
uvcvideo               62467  0
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
iwlcore               124955  1 iwlagn
sdhci_pci               6700  0
hid                    83440  1 usbhid
option                 19050  0
usbserial              39131  1 option
snd                    71106  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ricoh_mmc               3416  0
dell_laptop             7941  0
dcdbas                  6886  1 dell_laptop
btusb                  12969  2
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
nouveau               515227  2
ttm                    60847  1 nouveau
drm_kms_helper         30742  1 nouveau
serio_raw               4918  0
sdhci                  17928  1 sdhci_pci
led_class               3764  2 iwlcore,sdhci
mac80211              238448  2 iwlagn,iwlcore
cfg80211              148546  3 iwlagn,iwlcore,mac80211
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0
output                  2503  1 video
drm                   199204  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
intel_agp              29095  0
lp                      9336  0
parport                37160  2 ppdev,lp
ohci1394               30260  0
ieee1394               94771  1 ohci1394
tg3                   122382  0
ahci                   37838  1

---

### Post by fskgoalie on 2010-07-06
i also tried uninstalling then reinstalling. i could connect to internet after installation but when i restarted my computer wireless was disabled like before.

---

### Post by roosh on 2010-07-06
It seems Ubuntu is loading a driver for you, but it's not working somehow. I can't tell what to do now. If all else fails, you can try to use ndsiwrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by fskgoalie on 2010-07-06
none of the packages support 10.04. should i look for older version of ubuntu to install?

---

### Post by roosh on 2010-07-07
No. Just go to system --> applications --> synaptic package manager
and install it from there. I am using ndiswrapper on 10.04

---

### Post by fskgoalie on 2010-07-08
I tried installing from CD but said i needed to download parts of it.

---

### Post by fskgoalie on 2010-07-08
ok, i uninstalled ubuntu then reinstalled it. i downloaded the ndiswrapper packages and restarted computer. my wireless connection was still disabled.

---

### Post by roosh on 2010-07-08
Now you need to get the windows XP drivers for your system. You need to get either the 32-bit or 64-bit drivers, depending on your system. Also, it looks like you have the Intel Corporation PRO/Wireless 4965 AG or AGN card. I already found the drivers on the intell site. So I can see what your system architecture is if you post back the output of:
```
uname -a
```

---

### Post by fskgoalie on 2010-07-08
i have windows vista home premium

---

### Post by roosh on 2010-07-08
You can still get the XP driver online. I actually was able to get it myself. Please post the output of ```
uname -a
```

---

### Post by fskgoalie on 2010-07-08
uname -a

Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

---

### Post by roosh on 2010-07-08
You should be able to download the driver here:
[http://downloadcenter.intel.com/T8Clearance.aspx?sType=&agr=Y&ProductID=&DwnldID=19147&url=/19147/eng/ICS_Dx64.zip&PrdMap=&strOSs=&OSFullName=&lang=eng](http://downloadcenter.intel.com/T8Clearance.aspx?sType=&agr=Y&ProductID=&DwnldID=19147&url=/19147/eng/ICS_Dx64.zip&PrdMap=&strOSs=&OSFullName=&lang=eng)

After this, extract the contents to a folder. Then point ndiswrapper to the .inf file in that folder. 
Then run the commands:
sudo rmmod iwlagn
sudo rmmod iwlcore
sudo modprobe ndiswrapper

if that works, then we need to make some permanant changes to make the card load at boot.

---

### Post by fskgoalie on 2010-07-08
should i uninstall ubuntu then reinstall so i have connection and then follow the steps?

---

### Post by roosh on 2010-07-08
are you telling me that you don't even have a wired internet connection?
Even if that's the case, then you don't need to uninstall ubuntu. Just, copy the folder with the XP driver (in the above link) to your computer with ubuntu.

---

### Post by fskgoalie on 2010-07-08
i only have laptop haha. i didnt see a .inf file and i clicked on the files and they all say they arent compatible and i need x86

---

### Post by roosh on 2010-07-09
What do you mean? There is a file called NETw5x64.INF in there. Extract the folder named "Disk" to your desktop. Then open a terminal and run:

sudo ndiswrapper -i ~/Desktop/Disk?Drivers/x64/NETw5x64.INF

See if that works.

---

### Post by fskgoalie on 2010-07-09
i found the .inf file but i can't figure out how to point ndiswrapper to the file.

---

### Post by roosh on 2010-07-09
Ok, put the folder named Disk on your desktop and run: ```
sudo ndiswrapper -i ~/Disk/Disk/Drivers/x64/NETw5x64.INF
```

then temporaily disable the original drivers and activate ndiswrapper (each line denotes a seperate command): 
```
sudo rmmod iwlagn
sudo rmmod iwlcore
sudo modprobe ndiswrapper

```

---

### Post by fskgoalie on 2010-07-10
for each command it says the file cannot be found

---

### Post by roosh on 2010-07-11
Sorry, instead of sudo ndiswrapper -i ~/Disk/Disk/Drivers/x64/NETw5x64.INF
try

sudo ndiswrapper -i ~/Desktop/Disk/Drivers/x64/NETw5x64.INF

---

### Post by fskgoalie on 2010-07-11
this is what appeared when i entered sudo ndiswrapper -i~/Desktop/Disk/Drivers/x64/NETw5x64.INF


usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

---

### Post by roosh on 2010-07-14
you didn't have a space between "-i" and "~/Desktop/Disk/Drivers/x64/NETw5x64.INF"
just copy and paste this:

sudo ndiswrapper -i ~/Desktop/Disk/Drivers/x64/NETw5x64.INF

---

