---
title: "No signal from graphic card after boot"
date: 2013-11-30
forum: Multimedia Software
---

### Post by salopette91 on 2013-11-30
Hello everyone!

I need some help here I've been trying for hours to get ubuntu up and running on my new computer.
These are the specs:
> **Motherboard:** Gigabyte GA-H87M-HD3
**Processor:** Intel Core i5 4440
**Ram: **Corsair Vengeance 2x4gb
**Graphics: **Sapphire Radeon HD7790
**HD: **Seagate Barracuda 7200
**CD/DVD: **Atapi iHAS624

At first I was trying to install the desktop version. Whatever I tried to do it always arrived at a point where it was trying to load the graphics card (screen starts blinking) and ends up with a black screen (if I booted with nomodeset) or no signal at all (without nomodeset).

So I tried to install ubuntu server and it worked but when I choose ubuntu in the GRUB it doesn't even load the terminal (or at least I can't see it) always black screen.

How can I fix this problem? Is it possible to make a customized .iso with the graphics driver in it and install ubuntu like that? Or is there any other way I can get ubuntu desktop up and working?

Please help me out here I'm going nuts. xD

---

### Post by salopette91 on 2013-12-01
Anyone?

---

### Post by salopette91 on 2013-12-01
Ok so my question changes to where can I find support for Ubuntu?
If nowhere, please suggest me a linux distribution that is actually working. Thank you.

---

### Post by QIII on 2013-12-01
Hello!

Did you confirm the md5sum of your downloaded .iso with the one from Canonical's website?  

Have you attempted to run Ubuntu in a Live session from your installation medium ("Try Ubuntu")?

This is a Haswell with Intel HD 46xx graphics?

Thanks.

---

### Post by salopette91 on 2013-12-02
> **QIII said:**
> Did you confirm the md5sum of your downloaded .iso with the one from Canonical's website?
Yes both for the desktop and server edition. Also burned the DVD using the official guide for Windows at: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

> **QIII said:**
> [COLOR=#000000]Have you attempted to run Ubuntu in a Live session from your installation medium ("Try Ubuntu")?[/COLOR][COLOR=#000000]
Yes. It acts just as same as "Install Ubuntu". Black screen with "nomodeset" and No signal screen without it.
When I was attempting to install Desktop version I also had to press F6 during the loading too see the various boot methods otherwise it would've black-screen'ed earlier.

[/COLOR]> **QIII said:**
> [COLOR=#000000]This is a Haswell with Intel HD 46xx graphics?[/COLOR][COLOR=#000000]
Not sure of what that is or what you need to know, pardon. Here are the specs of my graphic card [/COLOR][COLOR=#000000]*Sapphire Radeon HD7790*[/COLOR][COLOR=#000000]:

[/COLOR]> [TABLE="width: 100%, align: center"]
[TR]
[TD="class: txtgry_12, bgcolor: #EEEEEE, align: center"]Display Support[/TD]
[TD="class: txtgry_12, bgcolor: #FFFFFF"]4 x Maximum Display Monitor(s) support with 1 DisplayPort connected
supports up to 3 display monitor(s) without DisplayPort
4 x Maximum Display Monitor(s) support[/TD]
[/TR]
[TR]
[TD="class: txtgry_12, bgcolor: #EEEEEE, align: center"]Output[/TD]
[TD="class: txtgry_12, bgcolor: #FFFFFF"]1 x HDMI (with 3D)
1 x DisplayPort 1.2
1 x Dual-Link DVI-D
1 x Dual-Link DVI-I[/TD]
[/TR]
[TR]
[TD="class: txtgry_12, bgcolor: #EEEEEE, align: center"]GPU[/TD]
[TD="class: txtgry_12, bgcolor: #FFFFFF"]1075 MHz Core Clock
28 nm Chip
896 x Stream Processors[/TD]
[/TR]
[TR]
[TD="class: txtgry_12, bgcolor: #EEEEEE, align: center"]Video Memory[/TD]
[TD="class: txtgry_12, bgcolor: #FFFFFF"]1024 MB Size
128 -bit GDDR5
6400 MHz Effective[/TD]
[/TR]
[TR]
[TD="class: txtgry_12, bgcolor: #EEEEEE, align: center"]Dimension[/TD]
[TD="class: txtgry_12, bgcolor: #FFFFFF"]215(L)x106(W)x35(H) mm Size.
2 x slot[/TD]
[/TR]
[TR]
[TD="class: txtgry_12, bgcolor: #EEEEEE, align: center"]Software[/TD]
[TD="class: txtgry_12, bgcolor: #FFFFFF"]Driver CD[/TD]
[/TR]
[TR]
[TD="class: txtgry_12, bgcolor: #EEEEEE, align: center"]Accessory[/TD]
[TD="class: txtgry_12, bgcolor: #FFFFFF"]DVI to VGA Adapter
6 PIN to 4 PIN Power Cable[/TD]
[/TR]
[/TABLE]
[COLOR=#000000]

Thank you for helping me out![/COLOR]

---

### Post by QIII on 2013-12-02
I believe your CPU is a unit with a GPU on the same die.  Does your motherboard have a graphics output among the I/O ports in the back (that is, other than the outputs on the dedicated card?)

Edit:  Also, which version of Ubuntu are you using?

---

### Post by salopette91 on 2013-12-02
Yes it has a VGA output. You think ubuntu is using that graphics card even if BIOS is set to the dedicated graphics card?

Edit: latest available. 13.10

---

### Post by QIII on 2013-12-02
No, I was just eliminating possibilities.  If you are sure you have the dedicated card selected in the BIOS/EFI (which leads to a question in a moment), you might try switching it to integrated and see if it will boot with a monitor attached to the integrated output just for troubleshooting purposes.

The other question is this:  I believe that is a UEFI board.  When you installed, did you do a UEFI installation or a legacy BIOS installation?  While Ubuntu supports UEFI, there are some special considerations that may not be obvious when installing.

I'm not up on UEFI enough to give you the details (I have all of mine set to legacy BIOS boot just because I've been too lazy to fiddle around with UEFI just yet.  I will with 14.04.  ;))

There are a number of members, including a few of the Staff, who seem to be well versed.  We'll see if I need to get in touch with one of them and point them to this thread.  If a moderator with the handle oldfred shows up in the meantime, I'll turn it over to him!

---

### Post by oldfred on 2013-12-02
The 4000 series Intel processors are the 4th generation or Haswell as a code name.
You should have both video systems available.

Are you booting in UEFI or BIOS mode. 
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)



Haswell systems seem to have some added settings in UEFI/BIOS that interfere. 
But if using nVidia you will need nomodeset, but possibly additional boot parameters and/or UEFI setting changes.

These were laptops, not sure if you motherboard has similar settings?
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)
[http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg](http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg)

These were older cards, Some issues may be similar?
 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www.rodsbooks.com/gb-hybrid-efi/](http://www.rodsbooks.com/gb-hybrid-efi/)
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.

---

### Post by QIII on 2013-12-02
... speak of the devil ...

:)

---

### Post by salopette91 on 2013-12-02
I read myself some stuff about UEFI while I was trying to solve this problem and I set first boot priority to "Legacy" and to make sure I also set boot options to "legacy only".
I will try and see if I can find these settings in the links above by oldfred in my BIOS and try out one by one the boot options and I'll report back.

Thank you for your help.

---

### Post by oldfred on 2013-12-02
Best not to install in Legacy mode, but if you do, Boot-Repair can convert install from BIOS to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI).

---

### Post by salopette91 on 2013-12-02
Problem solved. I am writing from Ubuntu right now.
There are 2 settings in the BIOS that act on the integrated graphics card. The first one is the one that let's you choose which graphics card use and it's the one I set to use my PCIe card, the second one is is a setting in "Peripherals" tab that in case of trouble with the ext device it activates the integrated using 64 megs of graphics, this setting has to be disabled in order to install correctly Ubuntu. Normally this setting doesn't create trouble (ex. when installing Windows) but my guess is that Ubuntu sees that as the default graphics card and therefore ignores the PCIe one. I can not double test this because I don't have a VGA plug but I'm quite sure if I would have connected the VGA from the motherboard it would've loaded correctly with the integrated graphics.

I installed in Legacy mode but I will follow oldfred's suggestion to convert to UEFI.

For now I guess I can mark this thread as Solved. I will also try to load the installed ubuntu (with already the working drivers) with the integrated graphic setting enabled to 64 megs since I would like to be able to see the BIOS in case my PCIe card goes nuts, and see if it's only a problem with the installation and I'll report back.

Thank you very much for your support!

---

