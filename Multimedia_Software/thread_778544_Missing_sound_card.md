---
title: "Missing sound card ?"
date: 2008-05-02
forum: Multimedia Software
---

### Post by lightfoot on 2008-05-02
Hi All,

I have a problem with the sound on my Toshiba Tecra T9100. I've just installed Ubuntu 8.04 and apparently it can't find the sound card, but the sound worked fine when running Windows ?  My volume icon has a red warning sign over it, clicking the icon gives me an error window that says "No volume control Gstreamer plugins and/or devices found".

I followed the instructions on the Comprehensive Sound Problem Solutions Guide thread....

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Step 1....

rachel@rachel-laptop:~$ aplay -l
aplay: device_list:205: no soundcards found...


Step 2....

rachel@rachel-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)


Am I right in saying that no sound card is listed and should there be something like this be listed....

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)

I checked to see if it was disabled in the systems BIOS, but found no mention of a sound card?...So where has it gone and what do I do next, can I reinstall it from somewhere....HELP ?

I also have another identical laptop on which the sound works OK (it has problems of it's own...but that's another story !)

This is all still very new to me (I think the technical term is 'Thick' when it comes to computers) and I've been struggling to sort this out for a couple of days, but I can't seem to find a answer, so any help is much appreciated.

Cheer's

LF

---

