---
title: "alsa/pavucontrol is not detecting my sound card but lspci"
date: 2014-06-29
forum: Multimedia Software
---

### Post by test-parshwa on 2014-06-29
[SIZE=3][B]LAPTOP- toshibha satellite A105
OS-LUBUNTU 14.04 (which is LTS)[/B][/SIZE]
installed alsa/pulseaudio, but still i couldnt resolve my problem
check this info and let me know what i can do to get my audio back (i was having audio perfectly in ubuntu 12.XX)
XXX@XXX-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
05:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
XXX@XXX-PC:~$ sudo apt-get install alsa
[sudo] password for XXX:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'alsa-base' instead of 'alsa'
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
XXX@XXX-PC:~$ sudo apt-get install alsa utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'alsa-base' instead of 'alsa'
E: Unable to locate package utils
XXX@XXX-PC:~$ sudo apt-get install alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
XXX@XXX-PC:~$ sudo apt-get install alsa-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
XXX@XXX-PC:~$ alsamixer
cannot open mixer: No such file or directory
XXX@XXX-PC:~$ aplay -l
aplay: device_list:268: no soundcards found..
.[ATTACH=CONFIG]254345[/ATTACH]
[ATTACH=CONFIG]254347[/ATTACH]
[ATTACH=CONFIG]254346[/ATTACH]


pls guys help me out, i cant go back to windows,i dont want to. even i tried kali linux fisrt same prob occured so i thought prob is with kali so i tried this lubuntu.

u can have remote access to my system (ll provide teamviewer info) if anybody has solution.

thanks in advance

---

### Post by lidex on 2014-07-01
Alsa is not detecting your sound card. Is this an upgrade?
Try this:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

