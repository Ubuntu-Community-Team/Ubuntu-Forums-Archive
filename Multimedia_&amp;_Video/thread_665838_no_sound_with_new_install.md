---
title: "no sound with new install"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by rebelgoose on 2008-01-12
I just installed Gutsy Gibbons on my toshiba satellite A105 S361 laptop. I have no sound, but the same version of ubuntu worked fine on my alien. 
here's results from lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
05:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

any help would be appreciated.

---

### Post by Metaljaz on 2008-01-12
Try right clicking on the volume control at the top right hand side. Select preferences
Make sure that you have the Intel ICH6 (Alsa Mixer) device selected. Then try selecting
PCM. 
May work for you.

---

### Post by eggdeng on 2008-01-12
Type in a terminal 
```
sudo gedit /etc/modprobe.d/alsa-base
```
and add the line
```
options snd-hda-intel model=toshiba
```
to the end of the file. Save and reboot. With luck, you will get sound at least from external speakers. There is a general thread about Intel HDA problems at
[http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")
These threads are more toshiba-specific, you will probably find your model on one of these.
[http://ubuntuforums.org/showthread.php?t=568463]("http://ubuntuforums.org/showthread.php?t=568463")
[http://ubuntuforums.org/showthread.php?t=473425]("http://ubuntuforums.org/showthread.php?t=473425")

---

