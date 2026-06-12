---
title: "Wi-Fi Not working."
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by chaitanya2106 on 2013-03-11
Hello Everyone,
I have just installed Ubuntu 12.04 LTS & although I have a dual boot (with Windows 7), but I don't think I would be booting Windows 7 because Ubuntu 12.04 LTS is so much easy and much fast. 
However, I have encountered a problem while trying to make my laptop a Wi-Fi hotspot for my tablet/mobile devices. I have a wired internet connection & I don't have a router. In Windows, I used some commands to share my internet connection & make my laptop a hotspot. I have been trying to do the same with Ubuntu 12.04 LTS. But it seems that Ubuntu is not able to detect my inbuilt WiFi adapter. The WiFi LED at the bottom of my laptop is not ON. Bluetooth & WiFi operate from the same toggle switch & when I toggle ON, the Bluetooth LED is ON but the WiFi one is not. 
Here is a screenshot: 
[http://www.flickr.com/photos/93984650@N06/8548157015/in/photostream/](http://www.flickr.com/photos/93984650@N06/8548157015/in/photostream/)

I have gone through the steps mentioned in this ubuntu documentation: 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

I have almost done everything as said in that documentation. I stopped at Step 6 when my result was very different from what the documentation says. Here is a screenshot
of my result: 
[http://www.flickr.com/photos/93984650@N06/8548170763/in/photostream](http://www.flickr.com/photos/93984650@N06/8548170763/in/photostream)


If anyone has anything in mind, please let me know. That would be great!

Regards,
Chaitanya

---

### Post by chaitanya2106 on 2013-03-11
I did try the route System Settings -> Additional Drivers -> Broadcom STA wireless driver & download it & activate , but after rebooting the wireless settings didn't show up. Although now there's no Broadcom STA wireless driver in the Additional Drivers section.

---

### Post by kurt18947 on 2013-03-11
I know very little about NDISwrapper except that the version in 12.04 repositories is broken and I suspect you don't need it.  Are you sure you have a Broadcom adapter?  To use the additional drivers, you must have a wired internet connection,  that app downloads the required firmware/software from the internet

Please open a terminal and type:

"lspci" if your adapter is internal, "lsusb" if it's a USB dongle. You can copy & paste the output of those commands here.  You could also copy & paste the output of this command:  "lsmod".  I hope someone versed in Broadcom devices will check in here,  I am quite ignorant but knowing which chipset you have and what modules are loading should be a good start.  For instance, here is part of my "lsusb"

~$ lsusb
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

This would tell us that my wifi adapter is a Netgear WNA1100 using an Atheros AR9271 chip set.  This is usually a good first step.

---

### Post by chaitanya2106 on 2013-03-11
Thanks for your kind reply.

This is what is displayed on entering "lspci" in the Terminal,
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GS] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01) 
```

Results of "lsmod": 
```

Module                  Size  Used by
rfcomm                 38104  12 
parport_pc             32115  0 
ppdev                  12850  0 
bnep                   17791  2 
wl                   3032548  1 
coretemp               13362  0 
gpio_ich               13160  0 
snd_hda_codec_idt      60238  1 
dell_wmi               12602  0 
sparse_keymap          13659  1 dell_wmi
snd_hda_intel          33029  3 
snd_hda_codec         116477  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            17210  0 
dcdbas                 14099  1 dell_laptop
r592                   17809  0 
memstick               15886  1 r592
snd                    62675  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              181041  1 wl
lib80211               14041  1 wl
r852                   17906  0 
sm_common              16773  1 r852
nand                   49703  2 r852,sm_common
nand_ids                8548  1 nand
mtd                    38671  2 sm_common,nand
nand_bch               13004  1 nand
bch                    21768  1 nand_bch
nand_ecc               13106  1 nand
btusb                  17952  0 
psmouse                91022  0 
lpc_ich                16993  0 
microcode              18396  0 
bluetooth             189585  24 rfcomm,bnep,btusb
mac_hid                13078  0 
soundcore              14636  1 snd
serio_raw              13032  0 
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
firewire_ohci          36110  0 
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
nouveau               855013  3 
ttm                    76326  1 nouveau
drm_kms_helper         47459  1 nouveau
drm                   240232  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13317  1 nouveau
mxm_wmi                12894  1 nouveau
tg3                   141717  0 
video                  19117  1 nouveau
wmi                    18745  3 dell_wmi,nouveau,mxm_wmi
```

---

### Post by kurt18947 on 2013-03-11
Thank You.  Your wireless adapter is 0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01) .  I will be very surprised if you can't get this working without NDISwrapper.  I've never dealt with a Broadcom adapter so can only do what anyone else might do, search the networking and wireless forum.  I think before you do much else you'll want to remove any traces of what you've done so far.  I pretty sure NDISwrapper will interfere with any other drivers.  If you have access to a wired connection, I'd remove any traces I could find of your previous efforts then shut down, attach the ethernet cable and restart.  Then open software sources -> additional drivers and see how that works.  This is not a brand new or obscure chip set which is in your favor.  Here is a recent solved thread, there are others.  Chili555 is one of the wireless gurus on this forum.

[http://ubuntuforums.org/showthread.php?t=1997880&highlight=bcm4311](http://ubuntuforums.org/showthread.php?t=1997880&highlight=bcm4311)

I would recommend learning how to use search on this forum.  There is a LOT of excellent advice here.  I may sound like I hate NDISwrapper.  I don't.  For some adapters, it's the only game in town.  If there is a native solution e.g. not using Windows drivers, the native solution is likely to prove better over time.

---

### Post by Hadaka on 2013-03-11
Hi, this should get you going.

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo mpdprobe b43
```

---

### Post by chaitanya2106 on 2013-03-11
> **Hadaka said:**
> Hi, this should get you going.

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo mpdprobe b43
```

Hey thanks for your reply. Here are the results of those commands: 

```
chaitanya@CHAITANYA-PC:~$ sudo apt-get remove --purge bcnwl-kernel-source
[sudo] password for chaitanya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcnwl-kernel-source
```

```
chaitanya@CHAITANYA-PC:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn linux-headers-3.5.0-23
  language-pack-zh-hans-base firefox-locale-zh-hans
  linux-headers-3.5.0-23-generic language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,947 kB of archives.
After this operation, 8,962 kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu1 [3,947 kB]
Fetched 3,947 kB in 42s (93.9 kB/s)                                            
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 211185 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu1_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu1) ...
```

```
chaitanya@CHAITANYA-PC:~$ sudo mpdprobe b43
sudo: mpdprobe: command not found
```

---

### Post by Hadaka on 2013-03-11
hi , sorry i made a typo
its...
```
sudo modprobe b43
```

---

### Post by chaitanya2106 on 2013-03-11
> **Hadaka said:**
> hi , sorry i made a typo
its...
```
sudo modprobe b43
```

hey, its showing this result:

chaitanya@CHAITANYA-PC:~$ sudo modprobe b43
[sudo] password for chaitanya: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.




& then I closed the terminal despite the warning that there is a process going on & I would kill it. Though that process was going on for more than 15 mins.

---

### Post by Hadaka on 2013-03-11
Hi, after you loaded ubuntu did you do..

```
sudo apt-get update
sudo apt-get upgrade
```
if not, from a wired connection please do those commands
then do..
```
sudo apt-get autoremove
```
then do..
```
sudo modprobe b43
```
report back any errors.
thanks.

---

### Post by chaitanya2106 on 2013-03-11
> **Hadaka said:**
> Hi, after you loaded ubuntu did you do..

```
sudo apt-get update
sudo apt-get upgrade
```
if not, from a wired connection please do those commands
then do..
```
sudo apt-get autoremove
```
then do..
```
sudo modprobe b43
```
report back any errors.
thanks.

Did all that , but its still stuck: 

```
chaitanya@CHAITANYA-PC:~$ sudo apt-get update
[sudo] password for chaitanya: 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise InRelease                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports InRelease
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg       
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release                               
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Sources           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main i386 Packages           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex    
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [370 kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [64.0 kB]     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B] 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [22.2 kB]   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,388 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [239 kB] 
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Sources [5,120 B]
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Sources [80.3 kB] 
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Sources [4,729 B]
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main i386 Packages [595 kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [69.9 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,362 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted i386 Packages [9,505 B]
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe i386 Packages [187 kB]
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse i386 Packages [10.4 kB]
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources          
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [43.2 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Translation-en               
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [261 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Translation-en [109 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 2,191 kB in 43s (50.2 kB/s)                                            
Reading package lists... Done
```
```
chaitanya@CHAITANYA-PC:~$ sudo apt-get upgrade
[sudo] password for chaitanya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libnm-gtk-common libnm-gtk0 network-manager-gnome
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 478 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main libnm-gtk-common all 0.9.4.1-0ubuntu2.1 [6,292 B]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main libnm-gtk0 i386 0.9.4.1-0ubuntu2.1 [67.4 kB]
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main network-manager-gnome i386 0.9.4.1-0ubuntu2.1 [404 kB]
Fetched 478 kB in 12s (38.5 kB/s)                                              
(Reading database ... 211348 files and directories currently installed.)
Preparing to replace libnm-gtk-common 0.9.4.1-0ubuntu2 (using .../libnm-gtk-common_0.9.4.1-0ubuntu2.1_all.deb) ...
Unpacking replacement libnm-gtk-common ...
Preparing to replace libnm-gtk0 0.9.4.1-0ubuntu2 (using .../libnm-gtk0_0.9.4.1-0ubuntu2.1_i386.deb) ...
Unpacking replacement libnm-gtk0 ...
Preparing to replace network-manager-gnome 0.9.4.1-0ubuntu2 (using .../network-manager-gnome_0.9.4.1-0ubuntu2.1_i386.deb) ...
Unpacking replacement network-manager-gnome ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Setting up libnm-gtk-common (0.9.4.1-0ubuntu2.1) ...
Setting up libnm-gtk0 (0.9.4.1-0ubuntu2.1) ...
Setting up network-manager-gnome (0.9.4.1-0ubuntu2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```
```
chaitanya@CHAITANYA-PC:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox-locale-zh-hans kde-l10n-engb kde-l10n-zhcn language-pack-kde-en
  language-pack-kde-en-base language-pack-kde-zh-hans
  language-pack-kde-zh-hans-base language-pack-zh-hans
  language-pack-zh-hans-base linux-headers-3.5.0-23
  linux-headers-3.5.0-23-generic
0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
After this operation, 95.5 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 211347 files and directories currently installed.)
Removing firefox-locale-zh-hans ...
Removing kde-l10n-engb ...
Removing kde-l10n-zhcn ...
Removing linux-headers-3.5.0-23-generic ...
Removing linux-headers-3.5.0-23 ...
Removing language-pack-zh-hans-base ...
Removing language-pack-kde-en-base ...
Removing language-pack-kde-zh-hans-base ...
Removing language-pack-kde-en ...
Removing language-pack-kde-zh-hans ...
Removing language-pack-zh-hans ...
Processing triggers for software-center ...
INFO:softwarecenter.db.update:no translation information in database needed
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
```
```
chaitanya@CHAITANYA-PC:~$ sudo modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```

---

### Post by Hadaka on 2013-03-12
Hi, all this started when you attempted to 
create a hotspot without wireless working?
please do..
```
lsmod
```

---

### Post by Hadaka on 2013-03-12
hi, please also do.

```
cd /etc/modprobe.d
ls
```
and post the output

thanks.

---

### Post by Hadaka on 2013-03-12
re reading your post i see you attempted the wrapper thing....
please do the following commands..one at a time...even if there
is an error..continue to the next command till all commands are 
entered...
```
 sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
```

i believe this is what is causing the problem.

---

### Post by chaitanya2106 on 2013-03-12
> **Hadaka said:**
> Hi, all this started when you attempted to 
create a hotspot without wireless working?
please do..
```
lsmod
```

Yes i did started with the thought that i will create a hotspot but later i noticed WiFi is not even active in my laptop nevermind to create a hotspot out of it. I mean i have a wired ethernet conn and i want to make it a Wifi with my laptop as the router.

---

### Post by Hadaka on 2013-03-12
Hi, ok lets see if we can get your wireless working then
address creating a hotspot. Did you do the last set of 
commands i sent? Especially the commands in post #14
thanks

---

### Post by chaitanya2106 on 2013-03-13
> **Hadaka said:**
> re reading your post i see you attempted the wrapper thing....
please do the following commands..one at a time...even if there
is an error..continue to the next command till all commands are 
entered...
```
 sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
```

i believe this is what is causing the problem.



Here are the results:

```
chaitanya@CHAITANYA-PC:~$ sudo modprobe -rfv ndiswrapper
[sudo] password for chaitanya: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
chaitanya@CHAITANYA-PC:~$ sudo apt-get remove --purge ndisgtk ndiswrapper*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ndiswrapper-1.58
E: Couldn't find any package by regex 'ndiswrapper-1.58'
E: Unable to locate package ndiswrapper-1.58.tar.gz
E: Couldn't find any package by regex 'ndiswrapper-1.58.tar.gz'
chaitanya@CHAITANYA-PC:~$ sudo rm /etc/modprobe.d/ndis*
rm: cannot remove `/etc/modprobe.d/ndis*': No such file or directory
chaitanya@CHAITANYA-PC:~$ sudo rm -r /etc/ndiswrapper/*
chaitanya@CHAITANYA-PC:~$ 
```

---

### Post by varunendra on 2013-03-13
I don't think the sta driver was removed properly -
> **chaitanya2106 said:**
> 
```
chaitanya@CHAITANYA-PC:~$ sudo apt-get remove --purge **[COLOR="#FF0000"]bcnwl[/COLOR]-kernel-source**
[sudo] password for chaitanya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: **Unable to locate package [COLOR="#FF0000"]bcnwl[/COLOR]-kernel-source**
```

Hence subscribed :)


**PS:**

Chaitanya,

Please use default font in posts unless necessary. Making all the text bold makes it difficult to read.
Also, use 'Code' tags when posting command outputs. It preserves the formatting. Follow the "Code Tags example" link in my signature to see how to do that.

Thanks!

---

### Post by Hadaka on 2013-03-13
@varunendea..thanks..i missed that.

Hi, as was noted, the sta driver was not cleared out.
please copy and paste the following commands.

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist

```
then lets reset the b43 driver
```
sudo modprobe -rfv b43
sudo modprobe -v b43
```
and a final check on modules
```
lsmod
```
thanks.

---

### Post by chaitanya2106 on 2013-03-13
> **Hadaka said:**
> 
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist

```



```

chaitanya@CHAITANYA-PC:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for chaitanya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,656 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 185189 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic


```

its stuck since 15 minutes.

---

### Post by Hadaka on 2013-03-13
Hi, go ahead and boot or powercycle
then please do..

```
lsmod
```

thanks.

---

### Post by chaitanya2106 on 2013-03-13
> **Hadaka said:**
> Hi, go ahead and boot or powercycle
then please do..

```
lsmod
```

thanks.



```
chaitanya@CHAITANYA-PC:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12664  0 
xt_state               12515  0 
ipt_REJECT             12513  0 
xt_tcpudp              12532  0 
iptable_filter         12707  0 
nf_nat_h323            12810  0 
nf_conntrack_h323      52413  1 nf_nat_h323
nf_nat_pptp            12537  0 
nf_conntrack_pptp      13554  1 nf_nat_pptp
nf_conntrack_proto_gre    13581  1 nf_conntrack_pptp
nf_nat_proto_gre       12672  1 nf_nat_pptp
nf_nat_tftp            12421  0 
nf_conntrack_tftp      12818  1 nf_nat_tftp
nf_nat_sip             16946  0 
nf_conntrack_sip       24793  1 nf_nat_sip
nf_nat_irc             12543  0 
nf_conntrack_irc       13139  1 nf_nat_irc
nf_nat_ftp             12596  0 
nf_conntrack_ftp       13184  1 nf_nat_ftp
iptable_nat            13017  0 
nf_nat                 24741  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      14123  3 iptable_nat,nf_nat
nf_conntrack           66862  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12650  1 nf_conntrack_ipv4
ip_tables              18107  2 iptable_filter,iptable_nat
x_tables               22012  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
rfcomm                 38104  12 
parport_pc             32115  0 
bnep                   17791  2 
ppdev                  12850  0 
arc4                   12474  2 
joydev                 17394  0 
b43                   351542  0 
mac80211              475546  1 b43
cfg80211              181041  2 b43,mac80211
dell_wmi               12602  0 
ssb_hcd                12782  0 
sparse_keymap          13659  1 dell_wmi
bcma                   34573  1 b43
gpio_ich               13160  0 
coretemp               13362  0 
dell_laptop            17210  0 
snd_hda_codec_idt      60238  1 
dcdbas                 14099  1 dell_laptop
microcode              18396  0 
snd_hda_intel          33029  3 
snd_hda_codec         116477  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
ssb                    50757  2 b43,ssb_hcd
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62675  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r592                   17809  0 
r852                   17906  0 
sm_common              16773  1 r852
nand                   49703  2 r852,sm_common
memstick               15886  1 r592
nand_ids                8548  1 nand
mac_hid                13078  0 
mtd                    38671  2 sm_common,nand
nand_bch               13004  1 nand
bch                    21768  1 nand_bch
nand_ecc               13106  1 nand
psmouse                91022  0 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
serio_raw              13032  0 
btusb                  17952  0 
bluetooth             189585  24 rfcomm,bnep,btusb
lpc_ich                16993  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
firewire_ohci          36110  0 
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
tg3                   141717  0 
nouveau               855013  3 
ttm                    76326  1 nouveau
drm_kms_helper         47459  1 nouveau
drm                   240232  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13317  1 nouveau
mxm_wmi                12894  1 nouveau
video                  19117  1 nouveau
wmi                    18745  3 dell_wmi,nouveau,mxm_wmi
chaitanya@CHAITANYA-PC:~$ 



```

Hey many many thanks, Now my wireless adapter is enabled. Again, thanks for guiding me all the way.
Now i get to the part where I have to create a hotspot. I created a hotspot in Windows 7 with the SSID "CPWiFi" , I see that whenever I toggle ON the WiFi button , ubuntu would try to connect to the CPWiFi network. I don't know how it knows that I have created that connection in Windows? I thought CPWiFi would only work in Windows 7. Anyways, Ubuntu only tries to connect to CPWiFi but fails. I went to System Settings--> Network--> Wireless--> Use as Hotspot option & created one SSID "CHAITANYA-PC". Now it would try to connect to these network(s) & it keeps trying but never successfully connects.

---

### Post by chaitanya2106 on 2013-03-13
And now System Settings has crashed a couple of times.

---

### Post by Hadaka on 2013-03-13
Hi, glad you got the wireless working, I dont think
i have anything to offer on your hotspot issue. I would
mark this thread solved. Use thread tools or edit the title
and mark it solved. Then post a new thread on the hotspot
problem. I would also suggest you stick with your original
new thread for a solution, bouncing from thread to thread
for advise and entering commands makes it confusing for
the person trying to help you in one of the other threads as
they are unaware you have been getting multiple commands.
thanks.

---

### Post by varunendra on 2013-03-13
> **Hadaka said:**
> I would mark this thread solved.
+1

@ Chaitanya,
Please mark the thread as [Solved] now that its Title problem is solved.
Follow the 'how to' link in my signature to see how to mark it as such.
Thanks!

> Then post a new thread on the hotspot
+1 again.

Make its title relevant to your question so that correct people, who can help with that can notice it.

The advice about not using multiple solutions from multiple people on multiple threads is also a crucial one. It only makes a problem worse in most cases.

If you are tempted to do so, at least post a link to your original thread as reference so that others know what other things you have already been trying.

Good luck! :)

---

### Post by varunendra on 2013-03-14
> **chaitanya2106 said:**
> ```

Processing triggers for initramfs-tools ...
update-initramfs: **Generating /boot/initrd.img-3.5.0-25-generic**

```
**[COLOR="#FF0000"]its stuck since 15 minutes[/COLOR]**.

I don't like this ^^

If you interrupted that process by force-restarting or killing the terminal, it may have resulted in a corrupt initrd.img file. From **man update-initramfs** :
> The initramfs is a gzipped cpio archive.   At  boot  time,  the  kernel
       unpacks  that archive into RAM disk, mounts and uses it as initial root
       file system. All finding of the  root  device  happens  in  this  early
       userspace.

If your system is crashing frequently after last operation, this may be an explanation why. I strongly recommend you do -
```
sudo update-initramfs
```
Wait for it to finish, it shouldn't take too long.

If it really gets stuck again, check available space in your /boot partition (if you have a separate one). Try removing an older, unused kernel.
If there is enough space (the image merely needs about 22 MB + some more may be needed) and still it fails, try-
```
sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
```
copy-paste above to avoid typo (the (**`**) is a back-quote or 'grave accent' mark on the same key as **~**)

**PS:**
Glad to notice you marked the thread solved :)

---

### Post by chaitanya2106 on 2013-03-14
> **Hadaka said:**
> I would also suggest you stick with your original
new thread for a solution, bouncing from thread to thread
for advise and entering commands makes it confusing for
the person trying to help you in one of the other threads as
they are unaware you have been getting multiple commands.
thanks.

Yes, I knew that following people at the same time will eventually lead to confusion but I went on deliberately. I want to thank you & chilli555 very much. \\:D/

---

