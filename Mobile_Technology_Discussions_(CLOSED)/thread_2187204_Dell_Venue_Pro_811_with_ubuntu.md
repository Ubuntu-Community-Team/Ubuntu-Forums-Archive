---
title: "Dell Venue Pro 8/11 with ubuntu?"
date: 2013-11-11
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Alienman24 on 2013-11-11
I know these just came out but I was wondering if anyone had tried to install ubuntu on the Dell Venue pro 8 or 11.  You can see the specs at dells website here:
[URL="http://www.dell.com/us/p/dell-venue-8-pro/pd?oc=fncwv8p01h&model_id=dell-venue-8-pro"]http://www.dell.com/us/p/dell-venue-8-pro/pd?oc=fncwv8p01h&model_id=dell-venue-8-pro
[/URL]Most other tablets seem to run "arm" which from everything I've read is a pain however these come with full blown windows 8.1 and an unlocked boot loader.  They have an SD card slot and a micro USB (which I could boot a usb from with an adapter).  The only thing I'm worried about is if I come up against some kind of weird driver or hardware issue.  I''ve googled "linux on dell venue 8 pro" but have just found a bunch of reviews.  I don't want to buy it unless I can get rid of windows and run ubuntu.  Thoughts?

---

### Post by prepodam on 2013-11-13
Unfortunately, new baytrail tablets isn't good for ubuntu now, as I understand.
The tablet must support disabling of secure boot and enabling of legacy boot to setup 32bit ubuntu.

And, as we can see, in asus t100 linux support isn't good.
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)

May be, lenovo miix or dell venue or Toshiba Encore will have the better linux support.

---

### Post by Alienman24 on 2013-11-14
I know you can disable secure boot but I'm not sure about legacy boot.  Walmart has a good return policy so I may give it a shot and just return it if it does not work.  Thanks!

---

### Post by Bucky Ball on 2013-11-14
*Thread moved to **Mobile Technology Discussions**.*

---

### Post by evvsoft on 2013-11-14
In comments at amazon.com one of buyers says that Win8 message "Secure boot not configured" disappeared only after update BIOS. That seems stock BIOS without secure boot

---

### Post by awilliamson on 2013-11-24
I just bought one of these and tried booting Fedora on it. Written up [here]("https://www.happyassassin.net/2013/11/24/the-fedlet-revived-or-fedora-linux-on-a-dell-venue-8-pro-bay-trail/").

Secure Boot is enabled out of the box but is easy to disable in the firmware. You access the firmware by holding the volume down button for a couple of seconds right after powering on. The tricky thing about Bay Trail systems is that they have 32-bit UEFI firmwares, whereas up until now, just about every other UEFI system has been 64-bit UEFI, and that's what distros have focused on supporting. You need an image with a working 32-bit UEFI boot chain to get anywhere on one of these things. I was able to build such a Fedora image and get the system booted, but wasn't able to get to a functioning X or console due to what look like various kernel issues, with 3.12 and 3.13 kernels. Haven't tried any Ubuntu images yet, but I imagine Ubuntu would behave fairly similarly.

edit: there's no 'legacy boot' (CSM). You can _only_ boot the things from the internal storage or a USB stick, via native 32-bit UEFI. Can't boot in 'legacy mode', 'BIOS mode', whatever you want to call it, and can't boot from a micro SD card either (seems like). If you're going to buy one of these to fiddle with you're going to want a USB OTG adapter and a USB hub.

---

### Post by NoBugs! on 2013-12-03
Just to clarify, are you talking the Android-based Dell Venue 7/8? I don't see why it would have Windows-8 style secure-boot, and when I chatted with Dell chat they mentioned it does support root.

Just curious why Dell Venues aren't getting much attention/work porting as Nexus7, it seems to be very similar specs, about half the price. Is this secure-boot the Achilles' heel keeping this thing on AndroidOS (and outdated version, at that)?

---

### Post by slooksterpsv on 2013-12-03
> **NoBugs! said:**
> Just to clarify, are you talking the Android-based Dell Venue 7/8? I don't see why it would have Windows-8 style secure-boot, and when I chatted with Dell chat they mentioned it does support root.

Just curious why Dell Venues aren't getting much attention/work porting as Nexus7, it seems to be very similar specs, about half the price. Is this secure-boot the Achilles' heel keeping this thing on AndroidOS (and outdated version, at that)?

Please read the original post he did say Pro and even gave a link showing Windows 8.1 and Bay-Trail quad-core Intel Atom CPU.

I'd be interested if you could get Ubuntu to work on this. Hmm...

---

### Post by cman-1 on 2013-12-04
32bit UEFI boot is easy

Clover EFI is the best solution for that.

---

### Post by charlie17 on 2013-12-04
Does anyone know if any of these new Windows 8 Pro tablets are being targeted for Ubuntu Touch development or if the focus is only on ARM based tablets ?

---

### Post by cman-1 on 2013-12-05
Touch is only for ARM IIRC.

Desktop 13.04 works well on Intel tablets, especially with the Unity interface

---

### Post by souraka on 2013-12-06
hi
this tablet (venue pro 11) is a intel I3 based so it might be good to install the last version of ubuntu right  ??
if not...question you maybe can't answer now but is there any chance to get ubuntu or ubuntu touch working on delle venue pro really soon
clearly i a am going to buy it but i really don't want to use windows, so i acn wait a little bit but...

---

### Post by cman-1 on 2013-12-06
Windows 8.1 is not that bad for tablets.

---

### Post by KegHead on 2013-12-09
hi!

i have two dell venue 8's planned for gifts(one for myself)....anyone having any success?

any chance of using 64 bit 13.10?

thanks!

KegHead

---

### Post by Alienman24 on 2013-12-11
I found a you tube link where someone boots ubuntu.
[http://www.youtube.com/watch?v=1WrRngZ4giE](http://www.youtube.com/watch?v=1WrRngZ4giE)
The description says:

[FONT=arial][COLOR=#333333]"This is the new Dell Venue 8 Pro booting Ubuntu (13.10) from USB. As of now this is only working with frame buffer, no built in wlan, no sound, no camera. However the touchscreen is working."
[/COLOR][/FONT]
[SIZE=2][FONT=arial]My ubuntu skills are limited, anyone have any idea what "frame buffer" is or any ideas about the wifi?  I get my OTG cable today and will spend the next few days trying to boot different linux flavors but any comments suggestions would be appreciated.  I don't really care about sound or camera use.  Just the wifi and touch and it sounds like the touch works.[/FONT][/SIZE]

---

### Post by KegHead on 2013-12-12
looks like we're making progress!

---

### Post by KegHead on 2013-12-12
hi!

i watched the video...wish there was more info.

KegHead

---

### Post by Alienman24 on 2013-12-12
Ok Update.  I have my dell venue 8 pro (got it from Walmart for $230).  I also got my OTG cable to connect a USB drive.  I figured this would not be easy but here are the problems I've seen so far.

1)  UEFI, seems there are many threads on this but they are beyond my depth.  From what I can gather 99% of UEFI things are 64 bit but I my understanding is that the Dell Venue 8 pro has Windows 8 32bit.  This seems to cause a problem since apparently no flavor of linux has 32bit UEFI support.

2)  Boot to USB, there seem to be a couple different ways.  Since I can't seem to make a 32 bit UEFI bootible USB drive, any of the ways I try still result in me just going to windows.  

I know you can hold volume down while it is turing on and it will take you to a bios/settings screen (with touch support, which is odd).   There you can change the boot order and it will see the USB (not the SD card).  But it never boots any of my linux images for reason # 1 above.

You can also hold shift (which I achieved with a virtual keyboard) and restart the system.  This takes you to another menu which has the following options:
*  Exit and continue to windows 8.1
*  Use a device, use a USB drive, netowrk connection or windows recovery DVD
*  Trouble shoot, refresh or reset your PC, or use advanced tools
*  Turn off your PC

When I select "Use a device", it sees the USB drive and another device called "UEFI OS" which I assume is just the normal windows boot sequence.  When I select my USB drive, it still just reboots into windows.  Again I think this is due to problem # 1

Any help or suggestions you be appreciated.

---

### Post by JasonMRaub on 2013-12-13
I have a dell venue 8 pro. I have found out you can only boot a 32-Bit Uefi installer, pretty much all versions of Linux that are 32-Bit are not Uefi. Fedora 17 32-Bit would boot on my device, but, it would not go to the GUI. Fedora 19 has no 32-Bit Uefi support on there 32-Bit installer, they dropped support. Ubuntu has no 32-Bit Uefi installer, ask them to add support, they may listen.

---

### Post by cman-1 on 2013-12-19
If you need EFI help there is only one community that can help you.

We hackintoshers have been dealing with EFI since 2008 and we have a good command on it.

There is no community on the 'net that can do what we can do.

---

### Post by Alienman24 on 2013-12-20
Now I seem to be reading that the Intel Atom Z3740D in the Dell venue may support 64 bit.  Maybe we should try more 64 bit images?

---

### Post by evvsoft on 2013-12-26
Processor support, but UEFI not, so you need 32bit bootloader, that support to boot 64bit kernel. All distribs by default doesn't support this scheme

---

### Post by slooksterpsv on 2013-12-31
So I got one for Xmas - the Dell Venue Pro 8 and it's not that bad especially when I only paid $249 + you get office 2013 key for free. I'd still be curious to know how well Ubuntu works cause when I got the machine I had only 12GB out of 23GB left (the other are recovery partitions for the 8GB). I went and got a bluetooth keyboard for $25.00 and it works pretty good. =) Hope everyone's having a happy holidays

---

### Post by maxxsire on 2013-12-31
I'm looking to get the new Dell Venue 11 Pro Core i5-4300y 1.6GHz 8GB RAM 256GB SSD that's here [http://www.pcconnection.com/IPA/Shop/Product/Detail.htm?sku=16519771](http://www.pcconnection.com/IPA/Shop/Product/Detail.htm?sku=16519771) it's 62-Bit which "could" be very promising. To me it would be one of the ultimate tablets to run Ubuntu on but can't find hardware compatibility list for the processor, graphics card, and such. With the i5-4300y Haswell processor, 8GB of RAM, a stunning 1920x1080 touch screen, switchable battery, a swift 256 Solid State Drive, and only weighing in at 1.6 pounds I would grant it as the ultimate Linux-Tablet-Box that could function as an everywhere and any time computer. I just want to make sure it will run Ubuntu before buying. I currently run Ubuntu Studio, Ubuntu, and Windows 7 on my laptop but figure that I might have to settle for only regular Ubuntu on the new Dell Venue 11 Pro Core i5-4300y 1.6GHz 8GB RAM 256GB SSD. I would be grateful for any opinions or advice. Much props in advance. I bow in honor!

---

### Post by oldfred on 2013-12-31
32-bit UEFI Support Proposed For Ubuntu Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE)

New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)
Packard Bell ENME69BMP InsydeH2O  or Gateway LT41P04u

---

### Post by Alienman24 on 2014-01-02
I am still trying to hack away at this thing!  I am very glad ubuntu is looking to support 32bit uefi!  In the meantime I stumbled upon a destro that claims to have 32bit uefi support:  kanotix.  
I could not get it to work but my skills are limited.
Here is a link if anyone else wants to try.  Please post successes or failures.
[http://www.kanotix.com/module-Downloads.html](http://www.kanotix.com/module-Downloads.html)

---

### Post by souraka on 2014-01-06
hi there i have my new dell venu pro 11 and i try to install ubuntu on it from windows need help.....

---

### Post by Alienman24 on 2014-01-07
Souraka,  Most of us are cheap and have the Dell Venue _8_ pro which has 32 bit windows with UEFI.  We can't get linux on those right now because there is no destro with 32bit UEFI.

Your Dell Venue _11_ pro, should be running 64 bit windows.  You should be able to follow the directions here:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and create a 64 bit UEFI Thumb drive which you can then connect to your tablet with a OTG cable.

I would strongly suggest that you choose "Try without installing" so you can check to see if the wifi and touch work.  You may even need to get an multi USB adapter so you can attach a keyboard/mouse.

I don't mean to make it sound like a pain.  You should have a much easier time with yours then us with the Venue 8 pro.  Please post any results or questions.

---

### Post by migntom on 2014-01-08
Hello everyone,

I just received my Dell Venue 11 Pro Core i3. I tried to install Ubuntu 13.10 in my tablet, and I will give you my feedback here.

To install Ubuntu, I created a bootable Live-Usb key with UnetBootin. In order to boot from Usb, you have to go to the boot selection menu : press the power button, then maintain the Fn key (only if you use the Dell's keyboard) and press F12 repeatedly key until the menu appears. You can also boot from Windows advanced boot.

I recommand you to use an Usb multiplier to allow use of a mouse, and a keyboard if you did not purchased the mobile keyboard, and to have an additional Hdmi screen (see below).

In the list, select "Try Ubuntu without installing". The first thing you see after that, is a black screen. Nohting else. However, Ubuntu does work, and it is possible to display the image in an another screen, if you use the Hdmi port. That is why you should have another screen to try Ubuntu, the touchscreen always stays black. Resolution in the other screen is correctly detected, so I think the Hd Graphics 4200 is detected by Ubuntu, but his driver does not work very well. Or maybe should I configure something ?

The touchscreen seems to be recognized, it is possible to move the cursor with this. It is totally functional, if you disable the Built-in Display in System Settings > Displays (or clone the displays). But if you have the mobile keyboard, the touchpad does not work at all.

Wifi (Dell Wireless 1537) is unfortunately not recognized, you only see a 'No network device available'. If you have an Android smartphone, you can bypass this problem by sharing the smartphone connection, or you can use an Usb Wi-Fi, but it is not very practical for an ordinary use.

To continue testing, I decided to install Ubuntu in the Ssd. This step does not cause any problem, and is like any other installation (I did a dual-boot Windows-Ubuntu). Once finished, I can select with Grub which operating system to start. I tried to install the Wireless Driver (Dell Wireless 1537 downloaded from Dell) with NdisWrapper (ar6knwfx81.inf), but it did not work.

Sound is working fine.

Installing some updates (117 MB) did not fix anything.

In conclusion, Ubuntu works in Dell Venue 11 Pro, but there are some annoying issues that prevent a comfortable use for everyday, like lack of Wifi, or the permanent black screen in the touchscreen. I hope that Linux will provide a better support of this tablet soon!

I hope my description helps you (sent from my Dell Venue 11 Pro under Ubuntu). Feel free to ask me if you wish more information.

Edit: I also tried to install Debian 7.2. In order to boot Live-Usb, you have to disable Secure Boot and enable Legacy Boot. It works as bad as Ubuntu, but not worse. To have sound, you have to install PulseAudio. I noticed an interesting thing: if you use Linux 3.2.0, the built-on screen works, but not the touchscreen. And you cannot plug another screen. If you use Linux 3.11.6 (= Ubuntu 13.10's kernel) or 3.12.6 or 3.13 Rc7, you have the same screen issue, but touch works... Newer kernels do not resolve anything.

Edit 2: under Ubuntu, setting nomodeset crashes the graphic interface. But under Debian, it fixes the black screen issue, but you cannot use the Hdmi port...

---

### Post by axFelix on 2014-02-14
Thanks for the testimony, Migntom! I've been eyeing a Venue Pro 11 with the mobile keyboard myself but most of the feedback I could find about running Linux concerns the Venue Pro 8 rather than the 11, so it's great to see someone else who's tried it out.

Just to confirm: the Venue Pro 11 actually has 64-bit UEFI, so you were able to boot every distro you tried without having to mess around with 32-bit bootloaders? That's great, if so.

As for the video/modesetting issues, this guy (and the linked bug trackers) has been hard at work trying to fix them, and the Intel devs have chimed in, though I'm not sure if this only concerns the Baytrail (Atom) versions rather than the i3: [http://www.happyassassin.net/2013/11/24/the-fedlet-revived-or-fedora-linux-on-a-dell-venue-8-pro-bay-trail/](http://www.happyassassin.net/2013/11/24/the-fedlet-revived-or-fedora-linux-on-a-dell-venue-8-pro-bay-trail/). With luck it'll work better in 3.14.

The wifi is a bit of a dealbreaker, so I hope that gets sorted out soon. Can you confirm a couple more things for me?

You mentioned you had the mobile keyboard -- is that the one that has the touchpad, the hinge and the built-in battery? If so, do all of those things work when they're connected (and are they able to be hotplugged)? If so, great -- you mentioned that "the touchpad doesn't work" but I wasn't sure if you meant that the touchscreen stops responding when the mobile keyboard is connected, or if the mobile keyboard's touchpad doesn't work at all.

Also, is there any auto-rotation when the orientation is changed?

Thanks!

---

### Post by migntom on 2014-02-15
Hello axFelix,

Here are my personal answers to your questions. Note that I upgraded to 3.14-rc2 kernel: an interesting thing is that the MicroSd card reader now works! It was not with 3.13 and older. But I did not see any other improvement. All other issues still are present, including the graphic problem (booting with nomodeset is obligatory, or else you will have a black screen). I am now under Debian 7.2.

Yes, I did not have to use any 32-bit loader. Just booted from Usb or Usb Cd-Rom as you would do with any laptop or desktop. I cannot confirm if it will be the case for the Atom declination, as I only own the i3 version.

I confirm that Wi-Fi does not work at all, even in Linux 3.14-rc2. Iwconfig says "no wireless extensions." for usb0 and lo, so it is not even detected by Debian. Ndiswrapper does not work. I hope too that it will soon be supported, as a laptop/tablet without Wi-Fi is almost unusable nowadays. And for the graphics too, using an additionnal screen is impossible, and loading Hd movies costs a lot of Cpu cycles, because of nomodesetting.

Yes, the keyboard I have chosen is the one with the built-in battery. I meant that the touchpad does not work at all, you cannot move the cursor or click. Oddly, when I execute "egrep -i 'synap|alps|etps' /proc/bus/input/devices" ([https://wiki.debian.org/SynapticsTouchpad](https://wiki.debian.org/SynapticsTouchpad)) in a terminal, it says "N: Name="Synaptics T Pad V 01.30"", so it is found by the system. But after searching like mad, I did not found any way to get this working, so I have to use the touchscreen (which works very fine) or a mouse.
In conclusion, the touchscreen works (with and without the mobile keyboard) but not the touchpad.

Hot puggling is possible and does not cause any problem. Batteries are correctly working (I can remove the main battery and the sector and it stays operating if the keyboard was plugged).

And unfortunately, there is not auto-rotation when I change the orientation. I do not know how to check if the accelerometer is detected, but I think it is the same case of the Wifi.

I hope this answers your questions, and feel free to ask me anything if you want, or if something is unclear. ;)

---

### Post by axFelix on 2014-02-16
Thanks! So it sounds like the display, the mobile keyboard touchpad, and the wifi are the three things that really need to be fixed at a low level before this can be called "working." The display is definitely being worked on, and the wifi should happen eventually (particularly if it's a similar module in all of the new Dells, as it appears to be Atheros based), but I wonder what it'll take to bring attention to the touchpad since it's an optional accessory to uncommon hardware ...

Glad to hear that the hotplugging works as well as it does!

---

### Post by spotter2 on 2014-02-18
One thing people should consider to make this really usable (at least IMHO).

partition the emmc to have a boot partition.  store a file system on the sd card, boot of the kernel stored on the boot partition but have it be able to mount the root file system from the sd card.  unfortunately sdcard itself isn't bootable  a little destructive relative to bootable usb by itself, but is then something self contaiend and dont have to carry around a bulky usb key / usb otg cable.

---

### Post by renewable2 on 2014-02-21
I installed Ubuntu 12.04 amd64 using 'wubi' from a USB key to the microSDCard, after reboot the bootloader gave me a choice of the original windows 8.1 the tablet was shipped with or Ubuntu.

Choosing Ubuntu brought up the windows bios boot manager which informed me that there was a problem with Ubuntu's 'Master Boot Record' file 'wubildr.mbr', error 0xc0000225 the file is missing or corrupt.

When disabling the bootloader I'm asked for the 'bitlocker key', seems as though I might be asked to repair an installation.

---

### Post by Jhongy on 2014-03-03
Hi,

I've been working on the Asus T100, which is a similar baytrail convertible. Much of the hardware is working. Booting is fine too. You need to prepare a bootable GPT+EFI usb image, but use a 32-bit grub EFI bootloader, with the name hard-coded at "bootia32.efi". The distro itself can be 64-bit or 32-bit, but there is a caveat: 
- with 64-bit, EFI runtime services are inaccessible, which means that suspend/resume and poweroff don't work for now, until the linux kernel is patched with the ability to translate 64-bit efi requests down to 32-bit.

Current status is here: [http://ubuntuforums.org/showthread.php?t=2191557](http://ubuntuforums.org/showthread.php?t=2191557)

The full thread with all the developments is over at XDA-developers: [http://forum.xda-developers.com/showthread.php?t=2500078](http://forum.xda-developers.com/showthread.php?t=2500078) . 

The asus has good working graphics, semi-working wifi, and a few other things working. I don't think the dv8p has wifi yet, but it's worth digging.

---

### Post by migntom on 2014-03-05
I just received the active stylus for my Venue 11 Pro. Debian detects it and it works (for example in Xournal, Gimp), although not perfectly (it's hard to write a fine handwritten sentence), and there is no pressure sensitivity. Maybe should I configure something, I don't know. There is also palm detection.

Edit: after flashing Bios to the latest version (A10, [http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=4D8K3](http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=4D8K3)), it is much better (virtually perfect) and there is pressure detection. Just one thing, I would like to know how to active the "right click" with the stylus. Using any of stylus' buttons or maintain it on the screen like under Windows 8.1 does not give me the contextual menu.

---

### Post by axFelix on 2014-03-08
Good to hear! Thanks for keeping the thread updated :)

Haven't seen much progress on the Baytrail-T video bugs lately or any mention of Atheros or Synaptics updates ... but hopefully soon.

---

### Post by Jhongy on 2014-03-20
There is some back-and-forth on an IRQ assignment bug at boot, but for now it can be worked around. I haven't seen any movement on a driver for the MIPI-DSI panels yet.

You're waiting for Synaptics updates? Isn't your touchpad working on the dv8p?

---

### Post by axFelix on 2014-03-21
Touchscreen itself works fine, touchpad on the removable keyboard + hinge + touchpad + battery attachment on the dv11p doesn't work (keyboard and battery do, though, so I'm hoping that everything is more or less pin-friendly and it's just a new synaptics product that doesn't have drivers yet). Basically the same thing on the new Dell wireless module which is apparently a newish atheros product. Still waiting for them to ship a Baytrail (or Cherry Trail) configuration with 4gb of memory though, so no hurry :)

---

### Post by baumber on 2014-03-23
Hello Migntom and everyone,

I'm interested in buying a Dell Venue 11 Pro 7130 (with Haswell CPU) and running it with Ubuntu.

Can you please post/attach the outputs of "as root: lsusb and lspci, lspci -vv and lsusb -vv,  and cat /var/log/syslog, cat /var/log/Xorg.0.log, cat /proc/cpuinfo" from your Dell Venue 11 Pro 7130 (with Haswell CPU) to get an overview of the built-in hardware?

I have search around and found reports of some technical defects/shortcomings/issues, described with the following keywords;

- Dell Venue Freezing; [http://www.youtube.com/watch?v=_fOvpSFp-YE](http://www.youtube.com/watch?v=_fOvpSFp-YE)

- Dell Venue Stylus Issues; [http://www.youtube.com/watch?v=hh9QNEkpSbw](http://www.youtube.com/watch?v=hh9QNEkpSbw)

- Dell Venue Ghosting; Dell Venue 11 Pro screen going crazy:
[http://www.youtube.com/watch?v=kPjm1bWDIfY](http://www.youtube.com/watch?v=kPjm1bWDIfY) and [http://www.youtube.com/watch?v=RBrRhFdUfL8](http://www.youtube.com/watch?v=RBrRhFdUfL8)
and [http://www.youtube.com/watch?v=OOcwUk7LpmQ](http://www.youtube.com/watch?v=OOcwUk7LpmQ)

- Chassis has a worse manufacturing quality(fabrication defects) than Dell Venue 11 Pro 5130 (with Atom CPU) or Dell Venue 8

- Problems/Changing of the screen, if you press with the finger besides the screen on the frame ...

- It is possible to press down the chassis deeply at the backside ...

- 3G module disconnects or doesn't accept sim-cards anymore

Can you confirm such problems?

German reviews:
[http://www.tabtech.de/tablet-tests/review-dell-venue-11-pro-im-tests](http://www.tabtech.de/tablet-tests/review-dell-venue-11-pro-im-tests)

[http://youtu.be/ZhWRmGEk8Lc](http://youtu.be/ZhWRmGEk8Lc)

[http://www.youtube.com/watch?v=DlijUyskce4](http://www.youtube.com/watch?v=DlijUyskce4)

Best regards

---

### Post by joe94 on 2014-03-26
> **NoBugs! said:**
> 
Just curious why Dell Venues aren't getting much attention/work porting as Nexus7, it seems to be very similar specs, about half the price.


The NSA is putting up 1/2 the cost

---

### Post by migntom on 2014-03-30
Hello baumber,

First of all, sorry for the delay in responding, I did not have time to play with my computer...

> **baumber said:**
> Hello Migntom and everyone,

I'm interested in buying a Dell Venue 11 Pro 7130 (with Haswell CPU) and running it with Ubuntu.

Can you please post/attach the outputs of "as root: lsusb and lspci, lspci -vv and lsusb -vv,  and cat /var/log/syslog, cat /var/log/Xorg.0.log, cat /proc/cpuinfo" from your Dell Venue 11 Pro 7130 (with Haswell CPU) to get an overview of the built-in hardware?

I executed all of these commands, and pasted them here: [http://pastebin.com/xXLByjNQ](http://pastebin.com/xXLByjNQ)

> **baumber said:**
> I have search around and found reports of some technical defects/shortcomings/issues, described with the following keywords;

- Dell Venue Freezing; [http://www.youtube.com/watch?v=_fOvpSFp-YE](http://www.youtube.com/watch?v=_fOvpSFp-YE)

- Dell Venue Stylus Issues; [http://www.youtube.com/watch?v=hh9QNEkpSbw](http://www.youtube.com/watch?v=hh9QNEkpSbw)

- Dell Venue Ghosting; Dell Venue 11 Pro screen going crazy:
[http://www.youtube.com/watch?v=kPjm1bWDIfY](http://www.youtube.com/watch?v=kPjm1bWDIfY) and [http://www.youtube.com/watch?v=RBrRhFdUfL8](http://www.youtube.com/watch?v=RBrRhFdUfL8)
and [http://www.youtube.com/watch?v=OOcwUk7LpmQ](http://www.youtube.com/watch?v=OOcwUk7LpmQ)

Under Linux, I never experienced any of these issues. I never encontered the freezing problem, also under Windows. However, the ghosting issue happened one time to me under Windows, but only during few seconds, and it never did it again. Maybe some updates fixed this problem. The stylus issues have been corrected, and using it is fine for me. The only problems I found is the tablet's start button: if you touch it, your tablet vibrates and it can be annoying. Under Windows, it activates the start menu, so it is more annoying. And for me, the buttons on the tablet are too easy to click, but with practice, you easily avoid undesired clickings.

> **baumber said:**
>  - Chassis has a worse manufacturing quality(fabrication defects) than Dell Venue 11 Pro 5130 (with Atom CPU) or Dell Venue 8

I don't know. I only have the 7130 version, so I cannot answer this question. But I do not see why the 7130 would have a worse manufacturing quality than the other options. All I can say is that my Dell Venue 11 Pro i3 seems to be a high-quality product.

> **baumber said:**
> - Problems/Changing of the screen, if you press with the finger besides the screen on the frame ...

- It is possible to press down the chassis deeply at the backside ...

- 3G module disconnects or doesn't accept sim-cards anymore

Can you confirm such problems?

German reviews:
[http://www.tabtech.de/tablet-tests/review-dell-venue-11-pro-im-tests](http://www.tabtech.de/tablet-tests/review-dell-venue-11-pro-im-tests)

[http://youtu.be/ZhWRmGEk8Lc](http://youtu.be/ZhWRmGEk8Lc)

[http://www.youtube.com/watch?v=DlijUyskce4](http://www.youtube.com/watch?v=DlijUyskce4)

Best regards

My tablet do not present any of these issues. Maybe some people received defect Venues Pro, but I do not experience any of these problems. I cannot answer for the 3G disconnection because I did not choose this option.

I hope this answers your questions.

---

### Post by baumber on 2014-04-01
Hello migntom,

thank you for your answers and sharing your outputs! I have more questions, but it is not urgent ...

Are there any news regarding Wifi (Dell Wireless 1537)? 

Have you reported the non-detection of the Wifi-device to the kernel developers?

Neither in lsusb, nor in lspci the Wifi (vendor? Atheros based?) is listed, maybe there is a software rfkill switch to enable the device? 
 
Check for rfkill switch with : "rfkill list", when it is blocked: "sudo rfkill unblock all"
Check for disabled hardware with: sudo lshw -C network => something like "*-network DISABLED" is shown ...

Is there a vendor_id/name in Windows 8.1 for the Wifi?

It's not urgent, when you have time, can you please post the outputs of "dmesg and acpitool -e" ?

Thanks, baumber

---

### Post by axFelix on 2014-04-01
There's a kernel bug report open (at least for the Baytrail version) that suggests that the relevant bus isn't being probed correctly -- looks like the wifi is as nonstandard as the display. Hopefully we'll see better kernel support from Intel soon as I think it's mostly on their end rather than Dell's and they've been pretty proactive about these things lately (this might also account for the touchpad issue): [https://bugzilla.kernel.org/show_bug.cgi?id=67921](https://bugzilla.kernel.org/show_bug.cgi?id=67921)

---

### Post by Stanislav_Spasov on 2014-04-05
> **baumber said:**
> ...
Are there any news regarding Wifi (Dell Wireless 1537)


A (very) quick memo to let others know:
Have Dell Venue 11 Pro 7130
I just tried Ubuntu Development Release - 14.04 Beta 2.
WiFi adapter was recognised and worked flawlessly out of the box.
Had to add 'nomodeset' boot option to get display output...
UBUNTU just eats the battery!:(
Sorry but no time for more testing and reporting now ...

---

### Post by samueljroys on 2014-04-09
I also have the Dell Venue 11 Pro 7130.  I used YUMI to put Ubuntu 14.04 Beta 2 on a 4gb SD card with some persistence.  I was able to boot to the SD card with legacy boot.  I had to add the nomodeset option during boot up but was able to get all the way into the operating system with the display, touchscreen, wifi, bluetooth, etc working.  The only thing that did not appear to work correctly was the touchpad for the mobile keyboard. (The one with the battery built in) As mentioned above the battery really didn't seem to last long at first and the machine was running incredibly warm with the cooling fan running constantly until I set it down to install updates.  I left it on running on battery all night, about 5.5 hours, with the screen off, not connected to the keyboard.  So it might be that the screen on is what is causing the high heat and the battery drain.  Not sure if that helps anyone but figured I'd let people know.  I got this since it seemed the best choice for a windows tablet that could work with the 'legacy' windows programs but was really hoping to be able to run some version of linux on it too.  I couldn't find any way to run a version on it until i saw the above post.

---

### Post by migntom on 2014-04-10
> **baumber said:**
> Hello migntom,

thank you for your answers and sharing your outputs! I have more questions, but it is not urgent ...

Are there any news regarding Wifi (Dell Wireless 1537)? 

Have you reported the non-detection of the Wifi-device to the kernel developers?

Neither in lsusb, nor in lspci the Wifi (vendor? Atheros based?) is listed, maybe there is a software rfkill switch to enable the device? 
 
Check for rfkill switch with : "rfkill list", when it is blocked: "sudo rfkill unblock all"
Check for disabled hardware with: sudo lshw -C network => something like "*-network DISABLED" is shown ...

Is there a vendor_id/name in Windows 8.1 for the Wifi?

It's not urgent, when you have time, can you please post the outputs of "dmesg and acpitool -e" ?

Thanks, baumber

I just installed the stable 3.14 kernel, but unfortunately no news regarding Wifi. I did not reported this problem because I do not have much time to find where I can do this.

And no, Wifi is not listed neither in lsusb nor in lspci. And nothing is listed if I use "rfkill list", or "lshw -C network".

In Windows 8.1, the Wifi card is listed as "Dell Wireless 1537 802.11 a/g/n Adapter" in the device manager. Manufactured by Qualcomm Atheros.

You will find the outputs of dmesg and acpitool -e here: [http://pastebin.com/ubsQzfYa](http://pastebin.com/ubsQzfYa)

> **Stanislav_Spasov said:**
> A (very) quick memo to let others know:
Have Dell Venue 11 Pro 7130
I just tried Ubuntu Development Release - 14.04 Beta 2.
WiFi adapter was recognised and worked flawlessly out of the box.
Had to add 'nomodeset' boot option to get display output...
UBUNTU just eats the battery!:sad:
Sorry but no time for more testing and reporting now ...

> **samueljroys said:**
> I also have the Dell Venue 11 Pro 7130.  I  used YUMI to put Ubuntu 14.04 Beta 2 on a 4gb SD card with some  persistence.  I was able to boot to the SD card with legacy boot.  I had  to add the nomodeset option during boot up but was able to get all the  way into the operating system with the display, touchscreen, wifi,  bluetooth, etc working.  The only thing that did not appear to work  correctly was the touchpad for the mobile keyboard. (The one with the  battery built in) As mentioned above the battery really didn't seem to  last long at first and the machine was running incredibly warm with the  cooling fan running constantly until I set it down to install updates.  I  left it on running on battery all night, about 5.5 hours, with the  screen off, not connected to the keyboard.  So it might be that the  screen on is what is causing the high heat and the battery drain.  Not  sure if that helps anyone but figured I'd let people know.  I got this  since it seemed the best choice for a windows tablet that could work  with the 'legacy' windows programs but was really hoping to be able to  run some version of linux on it too.  I couldn't find any way to run a  version on it until i saw the above post.

So Wifi does really work under Ubuntu 14.04? It is a great news! Which kernel is running? Even with the lastest 3.14 kernel, I was not able to make Wifi working under Debian. Or, does it use a proprietary driver?

That is unfortunate, that the HD Graphics 4200 and the touchpad do still not work very well, though... Hope it will be fixed soon!

Edit: I tried Ubuntu 14.04 Beta 2 from Usb (built with Unetbootin) without installing. But Wifi and Bluetooth were not working in the live session, they were not detected at all. Did you tweak something to get them working?

Edit 2: not better with the final version.

---

### Post by migntom on 2014-04-18
In summary (in Debian with 3.14.0 kernel and Ubuntu 14.04 with 3.13 kernel), here are what are working for me (i3 version):

[LIST]
[*]Batteries (including the one in the mobile keyboard) 
[*]Hotplugging the tablet 
[*]Usb 3 port 
[*]Touchscreen 
[*]With nomodeset, screen is at full definition (1920 x 1080) 
[*]Camera and Webcam 
[*]Audio (speakers and jack) 
[*]Stylus (perfect with pressure sensitivity and palm detection) 
[*]µSd reader 
[*]Sleeping when closing lid 
[*]Volume control with buttons 
[*]Ubuntu can boot with Uefi and dualboot with Windows 8.1, but not Debian, which requires Legacy Boot 
[/LIST]
 
And what are not working:

[LIST]
[*]Wifi and Bluetooth (not detected at all, neither with lsusb, lspci, nor rfkill; Ndiswrapper is not working and says: "Hardware present: no") 
[*]TouchPad (detected with egrep -i 'synap|alps|etps' /proc/bus/input/devices as "Synaptics T Pad V 01.30", but cannot get it working...) 
[*]Screen orientation (accelerometer not detected?) 
[*]Change backlight intensity (cannot change it in System Settings...  > Backlight & Lock; xbacklight does not affect the brightness) 
[*]Have to add nomodeset option to get someting on the screen (otherwise you will get a black screen ; without nomodeset, you have to connect your tablet to an additionnal screen, and you will get a picture on the connected screen). Cannot use the Hdmi port under nomodeset 
[*]Power button does not send any extinction signal 
[/LIST]
 
Other issues:

[LIST]
[*]Cpu overheating and overusing under Ubuntu, even when doing basic tasks (not present under Debian) 
[*]The interface animations (open/close the Dash, move to another workspace, window appearing or disappearing) are very/extremely slow and cost a lot of Cpu cycles 
[*]Play a movie with Vlc at fullscreen is using 100% Cpu and can freeze the screen (you have to do an Alt + F4) 
[*]Under Debian, with nomodeset, the default font size is really big (I do not know why). You have to set them to size 4, 5 or 6 to have a normal size 
[/LIST]
 
Don't know:

[LIST]
[*]3G module (I did not choose this option) 
[/LIST]
 
I have a question... Anybody does know how to make the F key as default when pressing them, instead of the other function (mute, volume up/down, play/pause, search,...). For example, to do Alt + F4, I have to push Alt + Fn + F4. It annoys me a bit to have to press Fn when I want to use a Function key...

---

### Post by Thyme676 on 2014-04-21
> **migntom said:**
> In summary (in Debian with 3.14.0 kernel and Ubuntu 14.04 with 3.13 kernel), here are what are working for me (i3 version):

[LIST]
[*]Batteries (including the one in the mobile keyboard)
[*]Hotplugging the tablet
[*]Usb 3 port
[*]Touchscreen
[*]With nomodeset, screen is at full definition (1920 x 1080)
[*]Camera and Webcam
[*]Audio (speakers and jack)
[*]Stylus (perfect with pressure sensitivity and palm detection)
[*]µSd reader
[*]Sleeping when closing lid
[*]Volume control with buttons
[*]Ubuntu can boot with Uefi and dualboot with Windows 8.1, but not Debian, which requires Legacy Boot
[/LIST]
 
And what are not working:

[LIST]
[*]Wifi and Bluetooth (not detected at all, neither with lsusb, lspci, nor rfkill; Ndiswrapper is not working and says: "Hardware present: no")
[*]TouchPad (detected with egrep -i 'synap|alps|etps' /proc/bus/input/devices as "Synaptics T Pad V 01.30", but cannot get it working...)
[*]Screen orientation (accelerometer not detected?)
[*]Change backlight intensity (cannot change it in System Settings... > Backlight & Lock; xbacklight does not affect the brightness)
[*]Have to add nomodeset option to get someting on the screen (otherwise you will get a black screen ; without nomodeset, you have to connect your tablet to an additionnal screen, and you will get a picture on the connected screen). Cannot use the Hdmi port under nomodeset
[*]Power button does not send any extinction signal
[/LIST]
 
Other issues:

[LIST]
[*]Cpu overheating and overusing under Ubuntu, even when doing basic tasks (not present under Debian)
[*]The interface animations (open/close the Dash, move to another workspace, window appearing or disappearing) are very/extremely slow and cost a lot of Cpu cycles
[*]Play a movie with Vlc at fullscreen is using 100% Cpu and can freeze the screen (you have to do an Alt + F4)
[*]Under Debian, with nomodeset, the default font size is really big (I do not know why). You have to set them to size 4, 5 or 6 to have a normal size
[/LIST]
 
Don't know:

[LIST]
[*]3G module (I did not choose this option)
[/LIST]
 
I have a question... Anybody does know how to make the F key as default when pressing them, instead of the other function (mute, volume up/down, play/pause, search,...). For example, to do Alt + F4, I have to push Alt + Fn + F4. It annoys me a bit to have to press Fn when I want to use a Function key...


Ok I have the core i5 version, and can confirm most of these with ubuntu 14.04, with some notes. I was able to install ubuntu in eufi, and the external display is working. To install I had to check the nomodeset option at boot. Now it boots to a black screen. However, if I plug in an external monitor, it renders on the monitor just fine. Much faster than the built in display with nomodeset on. I was also able to get the backlight to dim on the built in monitor, I added acpi_backlight=vendor to my boot parameters before quiet boot. 

Using powertop I was getting from 4 to 8 watts power drain while running cpufreq-indicator. So when using the external monitor, power usage was a lot better than with nomodeset and the built in display. I need to charge the tablet and mobility keyboard, but it looks like ~11 hours estimated time, possibly more.

TLDR: still working on getting internal display working w/o nomodeset. Works with external display. Wifi, trackpad, bluetooth, not working. Same working as in quotes.

---

### Post by migntom on 2014-04-22
> **Thyme676 said:**
> Ok I have the core i5 version, and can confirm most of these with ubuntu 14.04, with some notes. I was able to install ubuntu in eufi, and the external display is working. To install I had to check the nomodeset option at boot. Now it boots to a black screen. However, if I plug in an external monitor, it renders on the monitor just fine. Much faster than the built in display with nomodeset on. I was also able to get the backlight to dim on the built in monitor, I added acpi_backlight=vendor to my boot parameters before quiet boot. 

Using powertop I was getting from 4 to 8 watts power drain while running cpufreq-indicator. So when using the external monitor, power usage was a lot better than with nomodeset and the built in display. I need to charge the tablet and mobility keyboard, but it looks like ~11 hours estimated time, possibly more.

TLDR: still working on getting internal display working w/o nomodeset. Works with external display. Wifi, trackpad, bluetooth, not working. Same working as in quotes.

So, I just tested Ubuntu without nomodeset in an external monitor, and I confirm that graphics performance is way, way better than on the built-in screen with nomodeset. I could measure quantitatively the performances with glxgears:

[LIST]
[*]About 1000 frames/200 FPS with nomodeset, on the built-in screen 
[*]About 23000 frames/4600 FPS without nomodeset, on the connected monitor. You have to type "vblank_mode=0 glxgears" instead of only "glxgears" in the terminal, or else it will run at the same monitor refresh rate (60 FPS). 
[/LIST]
 Animations are very smooth, and in addition, it seems to fix the overheating issue (much less Cpu usage at idle) and confirm what you are saying. If only there were not this displaying issue... Playing a movie at full screen now uses only about 5-15% Cpu, and only slightly more if you set the Cpu frequency at 600 MHz instead of 1.5 GHz with cpufreq.

So, in conclusion, the graphic chip is working very well, but cannot display anything on the built-in screen without nomodeset.

---

### Post by baumber on 2014-04-24
@axFelix;
Thank you for the hint of the bugreport => but baytrail version; there is a lot of activity now with patches ...

@migntom;
Thanks for your outputs and summary!

@Stanislav_Spasov and samueljroys and [**[COLOR=#000000]Thyme676[/COLOR]**]("http://ubuntuforums.org/member.php?u=1221100")
Which model/CPU do you have ? With Intel Core i5-4300Y or i3-4020Y? Is it a Intel Wifi?
Maybe there are different WLAN chips integrated with the CPU models ? => i5-4300Y (Intel Wifi) vs i3-4020Y (WLAN Atheros)?

---

### Post by Thyme676 on 2014-04-25
I have the 7130 core i5 model.

[UPDATE]
The trackpad works properly with kernel 3.15-rc2. I have been doing some digging and the screen issue *may* be related to improper initialization of the display port lanes. Right now I'm trying to get intel-gpu-tools working on 14.04 so I can check. Side note, the touch screen now may or may not be working. I can't really tell with only the external display.

Here is part of the dmesg:

[  351.614784] ACPI: \_SB_.PCI0.LPCB.LPTE: ACPI_NOTIFY_DEVICE_CHECK event
[  351.614794] ACPI: \_SB_.PCI0.LPCB.UAR1: ACPI_NOTIFY_DEVICE_CHECK event
[  351.620178] dell_wmi: Received unknown WMI event (0x11)
[  368.104495] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  368.113295] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  368.122124] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  368.130917] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  368.139743] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  368.148563] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  368.157358] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  368.157538] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting
[  382.783106] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  382.791903] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  382.800688] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  382.809470] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  382.818249] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  382.827035] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  382.835847] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  382.836027] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting
[  460.383265] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  460.392091] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  460.400904] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  460.409698] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  460.418514] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  460.427328] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  460.436110] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  460.436289] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting
[  468.680269] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  468.689072] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  468.697885] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  468.706675] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  468.715489] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  468.724291] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  468.733083] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[  468.733263] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting

---

### Post by Thyme676 on 2014-04-26
More interesting developments. I tried running a crunchbang livedisk in legacy mode, and it's rendering on the built in screen. It's running a 64 bit version of debian with the 3.2.41-2 kernel. No trackpad or touchscreen with this version though.

---

### Post by migntom on 2014-04-26
> **Thyme676 said:**
> The trackpad works properly with kernel 3.15-rc2. I have been doing some digging and the screen issue *may* be related to improper initialization of the display port lanes. Right now I'm trying to get intel-gpu-tools working on 14.04 so I can check. Side note, the touch screen now may or may not be working. I can't really tell with only the external display.

Just installed this kernel. TouchPad does effectively works, although you have to tap with two fingers to do a right click ; clicking on the right bottom simulates a left clicking. Oddly, I cannot set anymore the Cpu frequency with Cpufreq (now, it only gives me "Performance" and "Powersave" options). Other issues still remain, no change. For me, the touchscreen is still working fine, as well as my active stylus (even with an external monitor when booting without nomodeset). I have no idea about the Gpu issue. Fps displayed with Glxgears are the same as before (about 200 with nomodeset and 4600 without).

Also, Ubuntu does work even if Secure Boot is enabled. So there is no need to tweak the Bios to boot from an Ubuntu live Usb and install it ; the boot device can be selected by pressing Fn + F12 at the start of the tablet.

> **Thyme676 said:**
> More interesting developments. I tried running a crunchbang livedisk in legacy mode, and it's rendering on the built in screen. It's running a 64 bit version of debian with the 3.2.41-2 kernel. No trackpad or touchscreen with this version though.

Yeah I also tested and installed Debian before, and I confirm this. There is a rendering on the built-in screen with the 3.2 kernel, but not with newer kernels, like in Ubuntu. The rendering with 3.2 kernel without nomodeset is the same as the one with newer kernels and nomodeset. The issues I encountered in both operating systems are the same, except that Debian consumes much less Cpu in idle. Getting sound working in Debian is also a bit tricky, I got it by installing PulseAudio, but I had to tweak some things with AlsaMixer to get it working and a tray icon.

---

### Post by José Serra on 2014-04-28
Hi. I'm using a Venue 8... With the 3.15rc3 kernel: no wifi, no blue-tooth, no webcam. And using nomodeset kernel option.

I installed Ubuntu 14.04 following these instructions: [http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/) (posted earlier in this thread)

May be we should open a new tread for the Venue 8 tablet.

---

### Post by José Serra on 2014-04-28
Instead of nomodeset. With video=VGA-1:800x1280@75e the video works a lot better.
[https://bugs.freedesktop.org/show_bug.cgi?id=71977#c40](https://bugs.freedesktop.org/show_bug.cgi?id=71977#c40)

---

### Post by migntom on 2014-04-30
Unfortunately, replacing nomodeset with video=VGA-1:1920x1080@75e (also tried with @75, @60e and @60) changes nothing on my Dell Venue 11 Pro i3. I still have a black screen. Maybe it only works with the Atom graphics.

---

### Post by Thyme676 on 2014-04-30
Not working for me on the i5, either. I tried using 60 instead of 75 and eDP instead of VGA-1 as well. We are so close!

---

### Post by Matthias_Ziehm on 2014-05-01
Have you tried video=VGA-1:1080x1920@ and one of the mode (75e, 75, 60e or 60)?
Maybe is it this way round like for the dell 8 which is given to be video=VGA-1:800x1280@75e not video=VGA-1:1280x800@75e.

---

### Post by Thyme676 on 2014-05-01
Ok I'll try those when I get the chance today and update accordingly. For reference, windows reports 60 or 48hz options.

Unfortunately none of the combinations worked. I tried that format with @60,@60e,@48,@48e

---

### Post by migntom on 2014-05-13
> **Matthias_Ziehm said:**
> Have you tried video=VGA-1:1080x1920@ and one of the mode (75e, 75, 60e or 60)?
Maybe is it this way round like for the dell 8 which is given to be video=VGA-1:800x1280@75e not video=VGA-1:1280x800@75e.

> **Thyme676 said:**
> Ok I'll try those when I get the chance today  and update accordingly. For reference, windows reports 60 or 48hz  options.

Unfortunately none of the combinations worked. I tried that format with @60,@60e,@48,@48e

Not working for me too. I installed the 3.15 Rc5 kernel, but no change. Cannot boot without nomodeset (black screen), and there is no Wifi at all.

It's been a while since the last reply. Does anybody have any news regarding these drivers support? If the displaying issue and the Wifi were fully working, we would have fixed the most annoying issues.

---

### Post by yonnie on 2014-05-23
Here's a howto on installing ubuntu 64-bit onto an Asus Transformer:  [http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)

Perhaps this method could be applied towards the Dell Venue 11 pro?  I don't like the 'dual-boot' idea as I'd rather ditch the windows altogether and make the tablet entirely Linux.

---

### Post by Thyme676 on 2014-05-23
Good news everyone! So I just installed the latest kernel (3.15-rc6) and the graphics are working without nomodeset! I'm still experimenting but it seems like the graphics are running a lot smoother, and the tablet is cooler when playing HD video. xrandr reports 1080P at 60hz connected to eDP1. Touch screen isn't working, and trackpad needs configuring for tap to click. Also wifi still isn't working, but that's a minor problem really. Personally I think I'll just order a good mini pcie wireless card from intel now that the graphics are working.

---

### Post by migntom on 2014-05-24
> **Thyme676 said:**
> Good news everyone! So I just installed the latest kernel (3.15-rc6) and the graphics are working without nomodeset! I'm still experimenting but it seems like the graphics are running a lot smoother, and the tablet is cooler when playing HD video. xrandr reports 1080P at 60hz connected to eDP1. Touch screen isn't working, and trackpad needs configuring for tap to click. Also wifi still isn't working, but that's a minor problem really. Personally I think I'll just order a good mini pcie wireless card from intel now that the graphics are working.

Excellent news, thanks! Since I already was with the 3.15-Rc5 kernel, I thought that an upgrade to 3.15-Rc6 kernel would change nothing, but it was otherwise and the graphics issue is effectively and finally fixed! :D It is as fast as before, when we had to plug an external screen to boot without nomodeset (~4600 Fps with "vblank_mode=0 glxgears"). I don't know why the touchscreen is not working for you, it's fully operating for me, and I did not have to configure anything to have tap to click. Concerning the Wifi, I am tethering with an Android smartphone, and it works fine, although I wish that it will be fixed soon.

The brightness can also be changed now, in All Settings > Brightness & Lock!

---

### Post by Thyme676 on 2014-05-24
Great! After all this work I'm happy to see it working. Right now I have crunchbang installed, and the touch pad is configured a bit differently, so the touchscreen could just be a config issue.

---

### Post by migntom on 2014-05-24
Hmm bad news... I just rebooted my tablet, and the touchscreen stopped working (stylus not working too). :-| I rebooted several times but could not get it working anymore, additionnal monitor plugged or not, nomodeset activated or not. Even more oddly, I cannot get it working in older 3.15-Rc5 kernel (it worked like a charm before). I don't know what happened, since I did not tweak anything... TouchPad continues to work fine, though.

---

### Post by walte_rande on 2014-05-27
I have created a USB drive from PCUnlocker_UEFI_x64.zip and get Dell Venue Pro 8 to boot from it. The USB drive must be formatted with GPT partition table and FAT32, otherwise it won't work. I'll give a try with Ubuntu later.

---

### Post by Jace_Miller on 2014-06-01
I recently picked up a refurbished core i5 version for pretty cheap ($425 on eBay).  Popping off the back cover it looks like there's a mini pcie slot there.

If the biggest issue is WiFi/bluetooth it might be possible to swap out the Dell card with something a bit nicer (should run between $15-40 depending on what bands you want)

Now, the issue is that I don't really feel like doing this with mine until someone else gives it a shot, but no one else seems interested.

Due to the low price I'm using it as just a laptop replacement with great battery life (the keyboard dock) but I'd like to be able to run Debian (or derivative) on it with full WiFi support (and if I can get a dual band AC card added that'd be super)

---

### Post by migntom on 2014-06-26
I just updated my kernel from 3.15-Rc6 to stable 3.15.1, and there is no apparent improvement. But do not install the 3.16-Rc, because the keyboard and touchpad from the mobile keyboard with battery are not working with these kernels!

---

### Post by sanicki on 2014-07-08
This seems to be the best thread for asking about the status of Ubuntu support for the Dell Venue Pro 8. A quick read seems to indicate not everything is yet working, but I was wondering if anyone had posted a how-to to get started and if a current list of non-working elements could be posted.

---

### Post by axFelix on 2014-07-09
effectively, we're now at a point where virtually everything works to spec except for the wifi, if you use one of a handful of point releases of recent kernels -- which (going by experience) means that this should all stabilize nicely around 3.16 or 3.17. not sure, however, when the wifi will work.

---

### Post by sanicki on 2014-07-10
So is it as straightforward as a standard usb install or are there additional steps to follow? And would a wireless dongle bridge the gap until wireless radio is solved?

---

### Post by rektide2 on 2014-07-13
Is there a special kernel-module ya'll need to use the Mobile Tablet Keyboard peripheral with an i5 Venue 11 Pro? What kind of a connection does it have with the Venue? I can use it in the bios to F12 and get myself into grub, but the keyboard isn't working in either grub or Linux.

How does the keyboard connect? Do you guys see it connected under lsusb or is there some controller in lspci? What driver/module runs it? Any information on how the Tablet Keyboard/mouse Mobile connect up would be great.

I'm still trying to get a debootstrapped live USB stick booting. I can get it booted (and have my own modern kernel installed in the bootstrap), but the keyboard doesn't work. If I put a USB hub in to attach a keyboard (as there is only one usb port! CURSES!), the bios won't let me boot from USB. If I unplug / replug the keyboard, a dell_wmi extension gripes that it doesn't recognize the event, but nothing changes: I'm still at the console, with the keyboard not working. Edit: I changed USB hubs and can now plug in both usb storage as well as a usb keyboard! Yay. But how do I get the keyboard working?

---

### Post by axFelix on 2014-07-13
Right now, the two obstacles to doing a standard USB install are:

1) most linux distros, with the exception of bleeding-edge stuff like Arch and derivatives like Manjaro/Antergos, don't currently have a new enough kernel packed in to bring the display etc. up correctly, so you might need an external monitor to use it with until you can actually install a newer kernel. pain in the ass, but obviously a one-time fix.

2) if you have a baytrail variant and not an i3/i5, the UEFI bootloader is 32bit rather than 64bit (despite the fact that the platform is otherwise fully 64bit; this is apparently just a weird bit of jankiness with the first generation of baytrail stuff) and again, not all distros can deal with this (though I think there have been some patches upstreamed across the board lately to fix this issue), so you may have to do a little bit of research to prepare the iso if it doesn't work on the first go.

and yeah, a wireless dongle would bridge the gap just fine for now, with those two things out of the way.

---

### Post by rektide2 on 2014-07-19
Does the Mobile Tablet Keyboard work for anyone? Does it work for anyone on a i3/i5 model? HELP. PLEASE RESPOND. How does it show up for you in /sys and in /dev?

---

### Post by axFelix on 2014-07-20
if you look at the last page, it was broken in one of the 3.16 RCs, but working before that...

---

### Post by birdman3131 on 2014-07-27
Well a friend just picked up one of the venue pro 8's and i am debating having one myself. I am more of a Windows guy but like to have a copy of Linux laying around because it does come in handy. I was thinking about dualbooting one with Ubuntu and windows but have a couple questions.

1. Would it be possible to have a small partition on the ssd that handles the booting from the SD card? If so how big would it need to be?

2. How much works on the 8? It seemed to me that the last 3/4s of the thread has been mostly aimed at the 11.

---

### Post by andir2 on 2014-07-28
Just for the stats:

Today, I successfully booted Ubuntu Desktop 14.04 LTS "Trusty Tahr" on my Dell Venue 11 Pro (Bay Trail).

I used the x64 ISO Image and Rufus to create a bootable USB drive (GPT, FAT32, 64kB Blocks).
First attempt resultet in a BIOS message telling me there is nothing to boot from.
To fix this I copied the /EFI directory from a Clonezilla live (version: 20140630-trusty) USB drive and adapted the config.
The next attempt resultet in a frozen Ubuntu boot screen.
I copied the files from a Ubuntu i386 USB drive to the USB drive (so effectively I ended up with the i386 version).
Finally I was able to successfully boot Ubuntu.

Experience:
+ Booting from USB via USB Hub worked without issues
+ External keyboard worked
+ Touchscreen worked without issues
- WiFi didn't work (no adapter recognized, didn't really try to find a solution)
- Didn't see any virtual keyboard (didn't really search for it though)

Hope this information might be useful to someone..

---

### Post by migntom on 2014-08-07
I retested my tablet with these two kernels under Debian (Lxde) and Ubuntu: 3.15.7 and the 3.16.0. The former worked not so bad, only the Wifi, the touchscreen, and some other less significant things were not working. But, the latter still causes issues which already were in the Rc versions: the mobile keyboard and the touchscreen stopped working! I hoped that the stable 3.16 kernel would fix them and bring back the touchscreen and stylus, which worked on the 3.14 kernel, but instead we lose more and more functions... What is happening? Hope we will not lose the graphics in 3.17... Here is a summary of working things (at least for my i3 version) according the kernel :

    
[LIST]
[*]Batteries (including the one in the mobile keyboard): [COLOR=#008000]works with 3.14, 3.15 and 3.16[/COLOR][COLOR=#006400].[/COLOR] 
[*]Mobile Keyboard: worked with the [COLOR=#008000]3.14 and 3.15[/COLOR], but not on the [COLOR=#ff0000]3.16[/COLOR]. 
[*]TouchPad: [COLOR=#ff0000]only worked with the[/COLOR] [COLOR=#008000]3.15[/COLOR]. 
[*]Hotplugging the tablet: [COLOR=#008000]works with 3.14, 3.15 and 3.16.[/COLOR] 
[*]Touchscreen and stylus: worked with the [COLOR=#008000]3.14[/COLOR] but not on the [COLOR=#ff0000]3.15 nor 3.16[/COLOR]. 
[*]Usb 3 port: [COLOR=#008000]works with 3.14, 3.15 and 3.16.[/COLOR] 
[*]Graphics: [COLOR=#008000]fully working since 3.15-Rc6, including the Hdmi port[/COLOR], but [COLOR=#ff8c00]cannot use two extended screens in Debian[/COLOR], since it forces clone displaying (extended displaying is working with Ubuntu). Under Debian, Xrandr says "Failed to get size of gamma for output default"... 
[*]Camera and Webcam: [COLOR=#ff0000]the webcam seems to be undetected with any kernel[/COLOR], but [COLOR=#008000]the 8 Mp camera is working with 3.14, 3.15 and 3.16[/COLOR] (tested with Cheese). 
[*]Audio (speakers and jack): [COLOR=#008000]works with 3.14, 3.15 and 3.16.[/COLOR] 
[*]µSd reader: [COLOR=#008000]works with 3.14 and 3.15 with Ubuntu [/COLOR](unfortunately, I don't remember if it also worked with the 3.16 kernel). [COLOR=#ff0000]However, it never worked with Debian...[/COLOR] 
[*]Sleeping when closing lid: [COLOR=#008000]works with 3.14, 3.15 and 3.16.[/COLOR] 
[*]Volume control with buttons:[COLOR=#008000] works with 3.14 and 3.15[/COLOR] (I don't remember if it works in 3.16 Ubuntu). [COLOR=#ff0000]However, it never worked with Debian...[/COLOR] 
[*][COLOR=#008000]Ubuntu can boot with Uefi and dualboot with Windows 8.1[/COLOR], [COLOR=#ff8c00]but not Debian, which requires Legacy Boot[/COLOR]. 
[*]Wifi and Bluetooth: [COLOR=#ff0000]not working at all in any kernel[/COLOR]. 
[*]Screen orientation: [COLOR=#ff0000]not working at all in any kernel[/COLOR]. 
[*]Power button does [COLOR=#ff0000]not send any extinction signal in any kernel.[/COLOR] 
[*]Change backlight intensity: works with [COLOR=#008000]3.15 and 3.16[/COLOR] 
[*]Don't know about the 3G module (I did not choose this option) 
[/LIST]

Other things:

[LIST]
[*]When booting Debian, it always hang just after the Dell logo, displaying this text in a black screen: "Invalid partition table!". If you press any key, the boot continues and shows you the normal Grub kernel selection menu. This does not happens with Ubuntu. 
[*]The boot and shutdown time are fast, but very slow with the 3.16 kernel (and even impossible: shutdown stucks forever when it says "Will now halt"). When booting, if you move with the touchpad or a mouse, tons of lines "[ 1234.567890] evbug: Event. Dev: input(8 or 10), Type: (0, 1, 2 or 3), Code: (random integer), Value: (random integer)" will appear... Ditto during the shutdown, but touchpad generates nothing. Additionnally, after a few seconds, the boot stucks at "[drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off" during some time. 
[/LIST]

In conclusion, do not use the 3.16 kernel. Use the 3.15 instead. Note that since I am currently with Debian and 3.15.7, some informations may be incorrect (I don't have an eidetic memory...), but most of them should be what actually happens. I hope this will help some people to decide if it is worth to buy now a Dell Venue 11 Pro and install Linux, or other people who are testing the tablet. And I hope that all or most of the issues will be fixed on next kernels.

---

### Post by baumber on 2014-08-13
@migntom
Thank you for keeping us uptodate!

I've found a bugreport from Archlinux, where user Evgeny reports a problem with kernel 3.16 and the dock station (keyboard).

The user owns a Dell Venue 11 Pro with an Intel i5-4300Y + an Intel WiFi 7260 and has posted the full dmesg log!!

It seems there are different WiFi chipsets, built-in the tablets, or the 256GB model has this unique?

DMI: Dell Inc. Venue 11 Pro 7139/0RFDKW, BIOS A12 06/20/2014, SMBIOS 2.7 present., 256 GB SSD
Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
smpboot: CPU0: Intel(R) Core(TM) i5-4300Y CPU @ 1.60GHz (fam: 06, model: 45, stepping: 01) 

[https://bugs.archlinux.org/task/41541](https://bugs.archlinux.org/task/41541)

dmesg log;
[https://bugs.archlinux.org/task/41541?getfile=12096](https://bugs.archlinux.org/task/41541?getfile=12096)

Furthermore the user opened a bugreport at kernel.org:

[https://bugzilla.kernel.org/show_bug.cgi?id=82331](https://bugzilla.kernel.org/show_bug.cgi?id=82331)

---

### Post by Tom_Deblauwe on 2014-08-20
Hello,

Just to share some info about the 5130 dell venue 11:

- boot: just write an "amd64" variant of your distro's ISO to an USB stick with a windows-only program called "Rufus" and select "GPT partitioning scheme". Then copy a file called "bootia32.efi" to the "EFI/BOOT" directory. That file is a 32bit efi grub2 bootloader file. When starting, select the usb stick in the bios and it boots.
- WIFI: I got it working using the "ath6kl_sdio" wifi driver. However, I needed to use one with firmware 3.0 support, and that is in the "wireless-testing" repo, and not in 3.16. The 3.0 firmware itself you can download from [http://github.com/qca/ath6kl-firmware](http://github.com/qca/ath6kl-firmware) and extract it into /lib/firmware. Also needed is to tell the ath6kl driver that it can support the chip with SDIO id 0271:0418. It is a line like:

{SDIO_DEVICE(MANUFACTURER_CODE, (MANUFACTURER_ID_AR6004_BASE | 0x18))},

you have to add to the struct "static const struct  sdio_device_id ath6kl_sdio_devices[]" in the file sdio.c of the ath6kl driver so it will handle the  device.

Then the wifi works here.

For me the mobile keyboard is not working okay: at startup, the mouse works, but then the mousepointer stops moving as soon as I type one letter... really :) any solutions to that?

Best regards,
Tom,

---

### Post by Dragonbite on 2014-08-20
Is the Dell Venue the only Windows 8 tablet that runs 32-bit UEFI, or is that standard for Windows (ARM) tablets?  Or is this issue only occurring with the Dell?

Also, is this an issue with the Android-based version?

---

### Post by axFelix on 2014-08-21
Thrilled that you got the wifi working so (relatively) easily! I think all I'm waiting for at this point is for a kernel that actually consistently works with the touchpad and touchscreen, then ...

afaik, the 32-bit UEFI issue is common to the entire first generation of Bay Trail hardware (that is, all of the 64-bit quad-core x86 Atom chips shipping in the past year). It's supposed to be gone in Cherry Trail (which is the mostly-similar revision due out later this year).

---

### Post by Tom_Deblauwe on 2014-08-25
Little update: The dell mobile keyboard issue I described above is solved with the patch for 3.16 mentioned here:

[https://bugzilla.kernel.org/show_bug.cgi?id=80091](https://bugzilla.kernel.org/show_bug.cgi?id=80091)

Best regards,
Tom,

---

### Post by keaton2 on 2014-08-27
I've been scanning this thread, but I cannot find a definite answer. I have a Venue 11 Pro 7139 that I have yet to successfully boot to a desktop GUI. It gets stuck at error: cannot initialize the agpgart module. Does anyone have any suggestions?

---

### Post by keaton2 on 2014-08-27
Back again, I got the Fedlet installation USB to install and I am currently working on installing Win8 to get the newest BIOs

---

### Post by José Serra on 2014-08-28
I'm having problems to boot {venue 8} with kernel versions 3.15.1 onwards. It hangs just after Loading initial ramdisk... I tried modifying kernel options {video or nomodeset} and nothing... It only boots if I press volume before grub loads, and manually select the uefi option.

With Kernel 3.16.1 still no BT or Wifi, but the screen can be rotated in "displays" window

---

### Post by ravindran.k on 2014-10-06
Just got this one :) Using Intel AMT/vPro I can remotely see the Ubuntu GUI loading fine. It is mostly the HD4200 Driver.. will look more and let you all know..
if you want to play arund remotely .. install Intel SCS [https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=20921](https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=20921)  and connect thru the AMT tools :) 
Ofcourse, all this if your Dell venue 11 pro is a Vpro version

---

### Post by David_Go on 2014-10-10
I've attempted to compile a 3.17 kernel on my i5 version of the Venue 11 Pro to see what the progress is (using the default settings from Ubuntu on top of a base install of the latest 14.10 besta, and default new settings for the kernel).  My initial results for the things I could try are:

Batteries - including mobile keyboard - [COLOR=#006400]Works[/COLOR]
Mobile Keyboard - [COLOR=#006400]works[/COLOR]
Mobile Touchpad - [COLOR=#ff8c00]partial[/COLOR] - it works, but stopped suddenly.  I think closing screen and then turning system on again brought it back to life.
USB3 port - [COLOR=#006400]works[/COLOR]
Touchscreen - [COLOR=#ff0000]Broken[/COLOR]
Graphics - [COLOR=#006400]Works[/COLOR]
Audio - [COLOR=#006400]Works[/COLOR]
Sleeping when closing lid - [COLOR=#006400]Works[/COLOR]
Volume control using Audio Buttons - [COLOR=#006400]Works[/COLOR]
Wifi [COLOR=#ff0000]Broken   (Even after additionally following tom_**deb**[/COLOR][[COLOR=#ff0000]**lauwe**[/COLOR]]("http://ubuntuforums.org/member.php?u=1940875")[COLOR=#ff0000] post above )
[/COLOR][COLOR=#000000]Sc[/COLOR]reen Orientation [COLOR=#ff0000]Broken[/COLOR]
Power button does [COLOR=#ff0000]not send any extinction signal[/COLOR]
Change backlight intensity: [COLOR=#006400]works[/COLOR]

---

### Post by antux2 on 2014-10-11
Hi guys,
someone has also tested docking station with Ubuntu?Ethernet, usb ports, hdmi and display ports work?

Thanks,

Antonio

---

### Post by antux2 on 2014-10-20
David_go in this git link ([http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=7880377012ef48bf75498648c3bcbcb60460ff28](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=7880377012ef48bf75498648c3bcbcb60460ff28)) there is the commit to add support for ar6004 hw3.0, it's the tree of 3.17 kernel version....are you sure it doesn't works?

Antonio

---

### Post by David_Go on 2014-10-24
> **antux2 said:**
> David_go in this git link ([http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=7880377012ef48bf75498648c3bcbcb60460ff28](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=7880377012ef48bf75498648c3bcbcb60460ff28)) there is the commit to add support for ar6004 hw3.0, it's the tree of 3.17 kernel version....are you sure it doesn't works?

Antonio

Sorry for the delayed response - I did not get notification of your post.   I've checked, and this patch does appear to be in 3.17, and it does not appear to do anything for me.  (When I manually load the driver it calls cfg80211 and other prerequisite modules, but it does not create a wireless or networking device, nor does it give any indication that it detected anything and failed).    If there is anything I can do to be of assistance to anyone in debugging or pursuing this, please let me know - I'll check here periodically but otherwise email   ubuntuforum at my.host.net.nz

While it would be nice to get the Wifi device working, I'm really wanting to get the touchscreen working - on the assumption I can get another WIFI device but not another touchscreen - and this device is currently no good to me as a tablet.  If you have any thoughts how I can get this working please let me know !!!   (I have not yet tried reverting to an i386 kernel, a part of me believes I shouldn't need to therefore i shouldn't, but I'm getting to the point where I may give it a go, VM functionality is less important then basic functionality).

---

### Post by axFelix on 2014-10-27
Anyone tried out one of the 3.18 rc's yet?

---

### Post by migntom on 2014-10-28
> **axFelix said:**
> Anyone tried out one of the 3.18 rc's yet?

I tested all of these kernels (with Debian 7 Lxde). Note that since the stable 3.17.1 (I didn't test the 3.17.0) kernel, the mobile keyboard problem has been fixed (the keyboard and the touchPad are working). Others issues like Wifi or touchscreen not working are still here.

I didn't notice any change between the 3.17.1 and the 3.18-Rc1, but don't install the 3.18-Rc2 (neither 3.18-Rc2-utopic nor 3.18-Rc2-vivid): the tablet doesn't boot with this kernel. After being stuck during some time at "Loading, please wait...", it says "Gave up waiting for root device" with some other lines of text, and starts an unusable "(initrams)" shell (the keyboard is not working, and all you can do is a hard reset). I don't know if it works with Ubuntu.

---

### Post by David_Go on 2014-10-31
Today I blew away my install and tried the latest **i386 **Ubuntu 14.10 - with weird, but not altogether bad results.

* The Touchscreen works.
* The Keyboard and touchpad don't.
* Wifi is not recognised.
* /dev/bus/sdio/devices enumerates 1 dvice - mmc_host/mmc0/mmc0:0001
* Installing took an incredibly long time - I thought it locked up for sure - twice.  This may be related to the filesystem on the previous install - not sure.
* The kernel installed was 3.16.0-23-generic

I noted some anomilies and possibly useful stuff in the boot messages while installing -

HID related lines:
[   24.762540] Linux video capture interface: v2.00
[   24.775037] input: Synaptics T Pad V 01.30 UNKNOWN as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:06CB:2819.0001/input/input12
[   24.777586] hid-multitouch 0003:06CB:2819.0001: input,hiddev0,hidraw3: USB HID v1.11 Mouse [Synaptics T Pad V 01.30] on usb-0000:00:14.0-4/input0
[   24.811613] input: SYNA7500:00 06CB:3AF0 Pen as /devices/pci0000:00/INT33C3:00/i2c-9/i2c-SYNA7500:00/0018:06CB:3AF0.0008/input/input14
[   24.812300] input: SYNA7500:00 06CB:3AF0 as /devices/pci0000:00/INT33C3:00/i2c-9/i2c-SYNA7500:00/0018:06CB:3AF0.0008/input/input15
[   24.812625] hid-multitouch 0018:06CB:3AF0.0008: input,hidraw4: <UNKNOWN> HID v1.00 Device [SYNA7500:00 06CB:3AF0] on 

Also this:

[   24.729252] IP: [<f9124377>] rmi_probe+0x87/0x1a0 [hid_rmi]
[   24.729319] *pdpt = 0000000036d98001 *pde = 0000000000000000 
[   24.729386] Oops: 0000 [#1] SMP 
[   24.729423] Modules linked in: hid_rmi(+) media snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_soc_rt5640 snd_soc_rl6231 snd_soc_core snd_hda_intel snd_hda_controller soc_button_array mac_hid snd_hda_codec snd_compress snd_hwdep snd_pcm_dmaengine snd_pcm dw_dmac dw_dmac_core snd_seq_midi snd_seq_midi_event snd_soc_sst_acpi snd_rawmidi bnep snd_seq spi_pxa2xx_platform snd_seq_device mei_me lpc_ich i2c_hid rfcomm snd_timer shpchp mei bluetooth snd 8250_dw serio_raw soundcore i2c_designware_platform 6lowpan_iphc i2c_designware_core parport_pc ppdev lp parport squashfs overlayfs nls_utf8 isofs nls_iso8859_1 hid_generic uas usb_storage dm_mirror dm_region_hash dm_log usbhid hid mmc_block i915 i2c_algo_bit drm_kms_helper ahci drm libahci sdhci_pci wmi sdhci_acpi video sdhci
[   24.730289] CPU: 2 PID: 1286 Comm: systemd-udevd Not tainted 3.16.0-23-generic #31-Ubuntu
[   24.730382] Hardware name: Dell Inc. Venue 11 Pro 7130 MS/      , BIOS A12 06/20/2014
[   24.730469] task: f3294410 ti: f2b0e000 task.ti: f2b0e000
[   24.730530] EIP: 0060:[<f9124377>] EFLAGS: 00010246 CPU: 2
[   24.730593] EIP is at rmi_probe+0x87/0x1a0 [hid_rmi]
[   24.730647] EAX: 00000000 EBX: f6af148c ECX: 000080d0 EDX: 00000000
[   24.730715] ESI: f6978000 EDI: 00000000 EBP: f2b0fd08 ESP: f2b0fcec
[   24.730783]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   24.730842] CR0: 80050033 CR2: 00000414 CR3: 36a9f000 CR4: 001407f0
[   24.730905] Stack:
[   24.730928]  f8605636 f9126000 f9126010 f6978c8c f6978c6c f6978c8c f91242f0 f2b0fd28
[   24.731025]  f86056eb f6978c7c f9126050 f6978000 f6978c8c f9126050 00000000 f2b0fd60
[   24.731117]  c1452183 f6978c8c f9126008 f2b0fd58 f8605636 f9126000 f9126010 f6978000
[   24.731213] Call Trace:
[   24.731253]  [<f8605636>] ? hid_match_device+0x76/0x80 [hid]
[   24.731319]  [<f91242f0>] ? rmi_post_reset+0x10/0x10 [hid_rmi]
[   24.731391]  [<f86056eb>] hid_device_probe+0xab/0x120 [hid]
[   24.731458]  [<c1452183>] driver_probe_device+0x93/0x3c0
[   24.731525]  [<f8605636>] ? hid_match_device+0x76/0x80 [hid]
[   24.731589]  [<c1452569>] __driver_attach+0x79/0x80
[   24.731646]  [<c14524f0>] ? __device_attach+0x40/0x40
[   24.731704]  [<c14504df>] bus_for_each_dev+0x4f/0x80
[   24.731763]  [<c1451c7e>] driver_attach+0x1e/0x20
[   24.731819]  [<c14524f0>] ? __device_attach+0x40/0x40

Makes me wonder if there is an issue with hid_rmi which is falling back to allow hid_multitouch to work, but disabling the touchscreen.


Also - 
root@folio:~/venue/14-04-i386-desktopimg# grep "hid" modules.log 
hid_sensor_accel_3d 13096 0 - Live 0xf9418000
hid_sensor_als 13001 0 - Live 0xf9413000
hid_sensor_rotation 13179 0 - Live 0xf9406000
hid_sensor_magn_3d 13083 0 - Live 0xf93e3000
hid_sensor_incl_3d 13083 0 - Live 0xf93de000
hid_sensor_gyro_3d 13083 0 - Live 0xf9430000
hid_sensor_trigger 13006 12 hid_sensor_accel_3d,hid_sensor_als,hid_sensor_rotation,hid_sensor_magn_3d,hid_sensor_incl_3d,hid_sensor_gyro_3d, Live 0xf93a2000
industrialio_triggered_buffer 12794 6 hid_sensor_accel_3d,hid_sensor_als,hid_sensor_rotation,hid_sensor_magn_3d,hid_sensor_incl_3d,hid_sensor_gyro_3d, Live 0xf93a7000
industrialio 52002 9 hid_sensor_accel_3d,hid_sensor_als,hid_sensor_rotation,hid_sensor_magn_3d,hid_sensor_incl_3d,hid_sensor_gyro_3d,hid_sensor_trigger,industrialio_triggered_buffer,kfifo_buf, Live 0xf9494000
hid_sensor_iio_common 14029 6 hid_sensor_accel_3d,hid_sensor_als,hid_sensor_rotation,hid_sensor_magn_3d,hid_sensor_incl_3d,hid_sensor_gyro_3d, Live 0xf93b0000
hid_sensor_hub 19325 8 hid_sensor_accel_3d,hid_sensor_als,hid_sensor_rotation,hid_sensor_magn_3d,hid_sensor_incl_3d,hid_sensor_gyro_3d,hid_sensor_trigger,hid_sensor_iio_common, Live 0xf93bb000
hid_multitouch 17203 0 - Live 0xf91d8000
hid_rmi 23940 1 - Loading 0xf9123000
mac_hid 13059 0 - Live 0xf88c9000
i2c_hid 18263 0 - Live 0xf88c3000
hid_generic 12503 0 - Live 0xf83eb000
usbhid 47001 0 - Live 0xf8649000
hid 91893 6 hid_sensor_hub,hid_multitouch,hid_rmi,i2c_hid,hid_generic,usbhid, Live 0xf8601000

---

### Post by David_Go on 2014-11-01
I've compiled a 3.17.2 kernel and used it alongside the latest Ubuntu 14.10 **i386** which allows [COLOR=#008000]touchscreen, touchpad and keyboard to work[/COLOR] for my Venue 11 i5 model (But I can't get the WIFI device to enumerate, let alone work).  If anyone wants the packages, let me know and I'll make them available.

---

### Post by antux2 on 2014-11-01
David_go i don't have yet dell venue 11, i'm trying to understand the incombatiblities and decide to buy it or not :P
One of my doubts is if it's suitable to work with it (shell/browser/libreoffice) without external monitor.
Thanks

---

### Post by David_Go on 2014-11-01
(Assuming you are planning on putting Linux on it, and I can only speak for the i5 version which I have) It will work fine with a shell and libreoffice without an external monitor - As it stands you will have difficulties browsing as WIFI does not work with it, and it has no Ethernet port.   In order to get networking working at the moment I am using a USB -> ethernet converter.   I've also ordered another brand of WIFI card (but because I'm cheap and I live on an Island it will take a month before I get it and will know if it works - assuming I can't solve the WIFI connectivity issue).  To be honest, if knew when I bought it what I know now, I would not have bought it - although it was cheap, and I'll eventually bend it to my will.

---

### Post by antux2 on 2014-11-02
Yes about wifi i'm thinking about hub usb -> ethernet converter + usb ports, anyway i think it's a temporary problem....we trust in Linux :)

---

### Post by José Serra on 2014-11-14
For the Venue 8: I updated to 14.10 and 3.18rc4 Still no WiFi or BT, and the strange problem of getting stuck in loading ramdisk if I didn't choose manually the uefi boot option.

---

### Post by the-nj on 2014-11-18
Hey, would it be possible to make your packages available? and to have a small set of instructions for beginners. I'm trying to get ubuntu installed for days now but can't get it to work! Thanks in advance!

---

### Post by David_Go on 2014-11-23
I can confirm that if you replace the built in WIFI adaptor with an Intel 7260NGW 802.11AC NGFF adaptor the default i386 install has no problem with a wireless connection.  At this price its probably not worth pulling hair out getting the imbedded card to work and getting nowhere.

**[ Edit - 2014/12/03 - recompiled and everything works for me ] **I've recompiled and managed to get the keyboard and mouse working alongside the screen I've uploaded [http://my.host.net.nz/venue11/](http://my.host.net.nz/venue11/) - There are 6 files totalling about 292 megs .  Grab them all save then (from the command line, as root), type "dpkg -i filename.deb"  for each package, then reboot.  (Note these packages come with no warranty - DON'T USE THESE PACKAGES IF YOU ARE NOT WILLING TO RISK HOSING YOUR INSTALL.)

You can check its worked by seeing if the docking station and touchscreen work work.  You can check its installed by (as root) doing uname -a - If the kernel version includes "3.17.2"  then its worked - if its 3.16 grub needs to be updated - good luck with that !!!  I do note that I've reverted to "Legacy" booting bypassing the whole UEFI thing.     

 Depending on your configuration you might also have issues with the amount of available space on the boot drive.  For my installs I simply made a single disk, ie no separate /boot partition.   (If you go this route you probably want 2 partitions - 1 for swap.   I have specific reasons for not wanting a swap partition)  As a quid-pro for anyone who downloads the files, Please provide feedback of your experiences with them in this forum.  

Good luck with them,
 David

---

### Post by isnogood2 on 2014-11-23
Hi folks,

I just made this account to reply to this thread. First of all I want to thank you guys for your effort, it's been a huge help for me.
I bought a Dell Venue 11 pro 7130 last week and since last Wednesday I am experimenting with getting Linux to work on it.

Here are my system specs:
Intel Core i5-4300Y
8Gb of RAM
256Gb SSD
WiFi: Intel from the Start - I haven't done more research, it just works :-) so I can confirm what David_Go said about WiFi
Mobile Keyboard and digitizer

My Experiences so far:
I disabled UEFI and went with Legacy Boot from the start since I still consider good ol' bootin' the more stable solution.
I have tried the live distros of Fedora 20, Ubuntu Gnome 14.04, openSuSe Gnome 13.2 and Mint KDE 17, all of them in x64-Version.
I only managed to get Mint KDE 17 to boot properly in live mode ( I had to add "nomodeset" to the Kernel boot line). Kernelversion of Mint 17 is 3.13.
With Kernel 3.13, the touchscreen and digitizer work but the touchpad doesn't. Additionally, because of nomodeset, graphic performance is poor and the the battery is drained quickly.
I will stick to Mint since I already use it on my gaming rig. I just tried the other distros, because I think, the gnome-shell is better suited for touch devices than KDE. 
I tried plasma-active, but am not happy with it and gnome-shell is messes around with my packet-dependencies in Mint, I had to fully reinstall the system to get rid of it.

Kernels I have tried so far, that I can remember:
3.13 - touchpad doesn't work and nomodeset is required to boot
3.16.2 - no touchpad, no touchscreen, no digitizer, no keyboard, uninstalled it right away
3.17.4 - everything works like a charm, except touchscreen and digitizer
3.18-rc5 - seems to be a bit smoother and quicker than 3.17.4, but still no touchscreen

I didn't compile anything myself, just took the *.deb-packages from Ubuntu.
Screen orientation isn't working at all, but I haven't done any research, because I want get the touchscreen to work first.
Surprisingly, the windows button below the touchscreen is working with kernel 3.17.4 and 3.18-rc5, seems like it isn't part of the touchscreen as I have thought before.

So Kernel 3.13 has to do something different than the newer ones to recognize the touchscreen. I compared the outputs of dmesg, lsusb, lshw, lspci and xinput. If I haven't overseen anything, the outputs of lsusb, lspci and lshw are the same,
The only differences in dmesg and xinput are these two devices:

SYNA7500:00 06CB:3AF0
SYNA7500:00 06CB:3AF0 Pen

Both are running with hid-multitouch driver. So I guess these are touchscreen and digitizer.
With Kernel 3.13, these devices are there. With 3.17 and above, they are not. Sadly, I lack deeper knowledge of the Kernel and modules and drivers to have a clue, what I can do with this information.
So right now I can choose between an overprized tablet with poor performance and poor battery life or an overprized netbook X-D
That's all for now, I hope it helps. Just ignore the bad grammar, for English is not my first language ;-)

Regards Isnogood

---

### Post by isnogood2 on 2014-11-24
Huzzaaaa!
Just installed Kernel 3.18-rc6 and touchscreen works \o/

edit1:
well, i celebrated too early :-(
After a reboot, the screen isn't working anymore. I'll do some more testing.

edit2:
Did some reboots. On one, the system hang while booting. It seems to take longer to poweroff now. No other problems so far.
Touchscreen is working again, even after some reboots.

Regards Isnogood

---

### Post by saou on 2014-11-24
I'm a non-venue-pro-11 owner thinking of getting one.  While googling around I came across   [http://forum.tabletpcreview.com/threads/dell-venue-11-pro-and-linux.60622](http://forum.tabletpcreview.com/threads/dell-venue-11-pro-and-linux.60622) It seems that fedora rawhide with the right kernel makes it almost usable.   Has anyone tried running a 15.04 daily say as a live session?

---

### Post by axFelix on 2014-11-30
> **isnogood2 said:**
> Huzzaaaa!
Just installed Kernel 3.18-rc6 and touchscreen works \o/

edit1:
well, i celebrated too early :-(
After a reboot, the screen isn't working anymore. I'll do some more testing.

edit2:
Did some reboots. On one, the system hang while booting. It seems to take longer to poweroff now. No other problems so far.
Touchscreen is working again, even after some reboots.

Regards Isnogood

High hopes for 3.19! :)

---

### Post by David_Go on 2014-12-02
Is this a 32 or 64 bit install ?

---

### Post by David_Go on 2014-12-02
I think that 15.04 is way to early in the development cycle for anything meaningful, ie not very different to 14.10 year.   (According to this[ official link]("https://wiki.ubuntu.com/DraftReleaseSchedule") Alpha 1 has not yet been released)I can advise that the standard Ubuntu (14.10) install - even with everything working is not particularly impressive on this tablet - the screen resolution is way to high and the ICONS to small for things to just flow, with lots of software niggles, like no quick way to rotate screen, power off button does nothing etc.   I think its useable as a tablet at the moment, but barely.  I am looking forward to Ubuntu Touch - which I'm hoping will come out as a spin of 15.04 for Intel devices and may be more usable.   For the moment I wouldn't buy a Venue 11 for Linux - its simply not ready.

---

### Post by mreichardt on 2014-12-04
Hi,

First of all, thanks for sharing all that helpful info.

One question: Is it possible to attach USB devices to the *Venue 11 Pro*'s micro USB port with an OTG adapter? Has anyone tried this?

There is an item "kwmobile® 3in1 Micro USB Adapter Card Reader OTG for Dell Venue 11 Pro 7000" available on amazon - which says it's working with "Venue 11 Pro 7000" models (the ones with Core i3/i5 CPUs). However, other sources say that the micro USB port is for charging (only?).

Background: I'm looking for a Tablet running Ubuntu with two USB ports - and the Dell Venue looks like it could be the perfect solution (one USB port does not have enough bandwidth for the devices I'd like to attach). I do not need touch screen support - so that's not an issue. For WLAN, I would buy the Intel adapter.

---

### Post by David_Go on 2014-12-04
> **mreichardt said:**
> Hi,

First of all, thanks for sharing all that helpful info.

One question: Is it possible to attach USB devices to the *Venue 11 Pro*'s micro USB port with an OTG adapter? Has anyone tried this?

There is an item "kwmobile® 3in1 Micro USB Adapter Card Reader OTG for Dell Venue 11 Pro 7000" available on amazon - which says it's working with "Venue 11 Pro 7000" models (the ones with Core i3/i5 CPUs). However, other sources say that the micro USB port is for charging (only?).

Background: I'm looking for a Tablet running Ubuntu with two USB ports - and the Dell Venue looks like it could be the perfect solution (one USB port does not have enough bandwidth for the devices I'd like to attach). I do not need touch screen support - so that's not an issue. For WLAN, I would buy the Intel adapter.

I don't have an OTG converter for my Dell, and obviously you have not advised your use case, but I thought I would chime in with something which might not be immediately apparent -
The Micro USB slot is actually where you plug the device charger - it takes (according to the PSU brick) 19.5 volts in through this slot - thus even if OTG does work (and I suspect it will), you won't be able to charge your device while using that port.   

I did plug my Venue11 (i5) into my cellphone cable with the other end attached to another computer.  Unsurprisingly I did not see any communication between the devices, but when I rebooted the Dell it complained of a "3 watt PSU" being plugged in, which was interesting.

I have generally been extremely disappointed with this device under Linux - Even after overcoming the hardware problems (not for the faint of heart), I have not found a desktop which works nicely with the high res (and thus very small pixels by default) screen.  This can somewhat be tuned with bigger pixels and tweeks, but it is a very, very sucky tablet experience (onscreen keyboard does not pop up as needed, does not auto-rotate, bad UI etc).   I'm hoping things will improve with the Touch UI version of Ubuntu which is due out with 15.04, but right now I would not consider this device as a Linux tablet - and this from a Linux zealot who uses Linux on the desktop to the total exclusion of Windows !!!  Care to tell me a bit more about your usage case so I can give you more precise insights ?

---

### Post by isnogood2 on 2014-12-05
@ David_Go
It's a 64bit install.

The Powerbutton works. I can even configure its behaviour in KDE. The Volumekeys are working too but one klick on them changes the volume by about 50% which is way too much.
But the other problems, you talk about still remain: no auto-rotation of the screen, too small icons etc. The onscreen keyboard in KDE is quiet usable, but it doesn't pop up automatically. And it's not usable in the lock-on screen, you have to use xvkbd for that, which is just ugly.
I installed touchegg for dealing with gestures (two, three and four fingers) and almost all of them work, except pinching.
For now, I just use the system as flawed as it is. I will continue experimenting over the holidays.

---

### Post by mreichardt on 2014-12-07
@David_Go
Thanks for your quick response
(somehow I expected to get an email on new posts).

Use cases for this tablet include controlling a robot - as a kind of embedded PC.
Attaching the robot's webcam and Kinect device (*ASUS Xtion* to be precise) to a single USB bus does not work unless you turn the camera's resolution down to like 320x240 (otherwise *dmesg* displays complaints that the bandwidth is insufficient).

So why a tablet - and not some small embedded ARM board?
It's convenient (separate battery; screen whenever you need one).
Apart from that, existing robots are equipped with some old Acer tablets (Iconia W500; those work perfectly btw.) and all robots should have a similar hardware configuration (e.g. run the same 64-bit Ubuntu OS).
Maximum size for the tablet is 11 inch.

---

### Post by jerry.zhengyu.shen on 2014-12-17
i5 4300Y/256GB SSD version here.
I just tried 15.04/Unity daily x86_64 yesterday on my tablet. It booted, the keyboard worked, but then it kernel panics and freezes after a few seconds when booting live so I can't even install it. I'm hopeful that it may be just a flash drive problem, or a liveUSB problem, but that's probably not the case. Anyhow, I'll test it again later if I can get a different flash drive, as my current one is pretty old.

Antergos works almost 100%, as in the touchscreen and keyboard both work, but wireless disappears after suspending and resuming. Evidently, Antergos/Arch is doing something right here. It's been working since a month or so ago; on the 3.16 kernel the touchscreen worked but the mobile keyboard/battery did not. Now that it's at 3.17, the keyboard (even the brightness/volume/wireless hotkeys) and trackpad work too, although the wi-fi bug still isn't fixed. I'm not sure if that's a kernel bug or just something up with my install or NetworkManager. Perhaps it's some kernel config. Whatever. I'm too busy timesinking and ricing to figure it out. I'd really love Ubuntu/Unity on a tablet, because of the maximization of vertical screen space with the unified menubar, but it seems that it's not quite viable yet in this case. 

I currently have GNOME 3 installed in Antergos, and it still runs surprisingly cool. I upped the scaling to 1.5 and it works great, no pixelation as far as I can see. GNOME devs still haven't fixed their accessibility settings yet though, and long press to right click doesn't work without some screwing around with gesture apps. Firefox looks sort of ugly with the 1.5x font, but I expect I'll be able to fix that with CSS. An interesting thing is that the touch keyboard pops up whenever a textbox is tapped, which is actually better than what Windows does with desktop apps. Except for chromium, but I don't use that anyway. MS needs to get its **** together. As for other things that work, the volume keys increment properly, and the power button suspends. There are occasionaly glitches in GNOME, but that's to be expected. 

The vivid kernel is still at 3.16 ([http://packages.ubuntu.com/vivid/kernel/linux-signed-generic](http://packages.ubuntu.com/vivid/kernel/linux-signed-generic)), and news points to 3.18 being shipped with vivid when it comes out of alpha/beta. It's likely that 3.18 will fix some of the regressions that have happened. My Gentoo unstable install (on my laptop) is already on 3.18, so I'm thinking that Ubuntu will follow suit a bit after Arch updates. It would be a nice christmas present to finally get a fully working GNU/Linux distro on this thing. I hate having to use the Windows flag on 8chan when I'm posting with this tablet. Not fun. I have no use for Windows anymore now that I've discovered Touhou works perfectly in wine.

---

### Post by axFelix on 2014-12-29
Thanks for the feedback, Jerry -- I was actually planning to run Antergos and Gnome 3 myself, and I would've done it last week, but I was shipped a defective mobile keyboard, so it's currently in the mail while I wait for a replacement. Glad to know I had the right idea and it's working so well!

You can probably try the SUSPEND_MODULES solution to fix the wifi (I had to do that with my Ubuntu desktop over a year ago, and it might no longer be necessary with a newer kernel, but I haven't bothered to undo it, since all it means is a few extra seconds to reconnect when resuming from suspend) -- [http://superuser.com/questions/620201/how-to-force-ubuntu-debian-mint-to-unload-modules-at-suspend-to-disk](http://superuser.com/questions/620201/how-to-force-ubuntu-debian-mint-to-unload-modules-at-suspend-to-disk). Would be curious to hear if it works.

Any word on the front camera or auto-rotation? I know those weren't working in Ubuntu yet but I'm curious about Arch/Antergos. Also wouldn't mind some more information about how to get the longpress right click working; I had thought about that but hadn't researched it yet.

---

### Post by jerry.zhengyu.shen on 2015-01-09
axFelix, I had a defective mobile keyboard too, but I just popped it open and smushed the connectors a bit. Worked just fine after that. Apparently there's an issue with loose connections on the mobile keyboards, but luckily they're not too hard to open and fix. 

I haven't been able to get the front camera to work. I just tested out Ubuntu-GNOME 15.04 with the latest 3.18 kernel. Good news, no more kernel panics on boot! The wireless works, but the touchscreen still doesn't. It doesn't even appear when running xinput list. In Antergos it shows up as SYNA7500:00 XXXX:XXXX Pen. I don't know which driver I'd need to enable to get that on Ubuntu. 

To get long press right click, I installed a program called easystroke gestures. I had to mess around a little but I eventually got it to somewhat work with long press right click. Even with 3.14, the GNOME accessibility settings are still utterly broken. 

Also good news on the accelerometer. You can access the raw data in /sys/bus/hid/devices/[PCI thing]/HID-SENSOR-200073.1.auto/iio:device2/in_accel_y_raw. I'm not quite sure if every device is the same, but once you have that, it'd be pretty trivial to write an infinite shell script which just loops and constantly checks the range of the integer in that file and executes xrandr accordingly. I know for sure that GNOME does not do auto rotate, but since the sensor output is there and supported, I can see other DEs being possibly different.

I'm testing the SUSPEND_MODULES thing with iwlwifi in there. I'll update once I'm done.

I suspect I did the SUSPEND_MODULES thing wrong. Anyways, here's how I fixed the wifi dropping on suspend. Before suspending you must rmmod both iwlwifi and iwlmvm. After suspending you need to modprobe them, and it works. The same thing must be done with hid-multitouch to make both the touchscreen work after suspend/resume, but you can rmmod/modprobe after resuming as well. With the wireless modules, if you don't rmmod them before suspending, your wifi will disappear forever (or at least until the next reboot).

---

### Post by axFelix on 2015-01-22
Got my machine back and everything's working nice! Was able to get good suspend settings working with this package:

[https://aur.archlinux.org/packages/systemd-suspend-modules/](https://aur.archlinux.org/packages/systemd-suspend-modules/)

Add the following to /etc/suspend-modules.conf:

iwlmvm
iwlwifi

(needs to be in that order).

Thanks for your help! Enjoying this machine. Not sure I'm getting the keyboard battery to charge properly though...

---

### Post by isnogood2 on 2015-01-26
I changed to Antergos with Gnome-Shell and usability is definitly better than with KDE. However, the touch screen doesn't seem to support multitouch and gestures. Touchegg isn't recognizing any gestures. That worked with Linux Mint and KDE.

> **axFelix said:**
> Got my machine back and everything's working nice! Was able to get good suspend settings working with this package:

[https://aur.archlinux.org/packages/systemd-suspend-modules/](https://aur.archlinux.org/packages/systemd-suspend-modules/)

Add the following to /etc/suspend-modules.conf:

iwlmvm
iwlwifi

(needs to be in that order).

Thanks for your help! Enjoying this machine. Not sure I'm getting the keyboard battery to charge properly though...

Thanks for your input. I will test that suspend thing. My Venue also didn't recognize the keyboard battery. A BIOS update did the trick.

Regards,
Isnogood

---

### Post by axFelix on 2015-01-26
yup, I've got the keyboard battery working now too!

multitouch does work, but only in a handful of gnome apps (try pinch to zoom in the image/pdf viewer). I also haven't been able to get it to resume reliably when adding multitouch-hid to the suspend-modules.conf the same way I did for the wifi modules (which work great now), so I'm just ignoring the touch support for the time being as it's pretty spotty anyway. the touchpad on the mobile keyboard also supports three-finger taps for middle click, which I just discovered. very nice.

I needed to switch from lightdm which antergos uses by default to gdm because the lockscreen wasn't kicking in right and some games were stuttering. I don't think gnome 3 properly supports lightdm anymore but antergos hasn't made the change.

my list of outstanding issues at this point is pretty short: touch is spotty, front webcam/mic still don't work, legacy tray icons (dropbox/steam/everpad) are really not that functional in upstream gnome 3 (I think this is just about the only thing they still haven't really reconciled from the 2.x days), and powertop is a little broken currently so I haven't been able to save the results of a calibration run which would probably get me another hour or two of battery: [https://github.com/NixOS/nixpkgs/issues/5424](https://github.com/NixOS/nixpkgs/issues/5424)

and that's a really short list! this machine works great.

---

### Post by axFelix on 2015-02-04
Lots of stuff seemingly fixed in 3.15 -- powertop no longer broken, touch support seems to resume properly on suspend, and this seems like the best solution for Gnome 3 tray icons so far: [https://extensions.gnome.org/extension/615/appindicator-support/](https://extensions.gnome.org/extension/615/appindicator-support/)

that leaves only the front webcam and mic as an issue.

---

### Post by raspacek on 2015-02-12
0

---

### Post by tim93 on 2015-02-20
> **Tom_Deblauwe said:**
> Hello,

Just to share some info about the 5130 dell venue 11:

- boot: just write an "amd64" variant of your distro's ISO to an USB stick with a windows-only program called "Rufus" and select "GPT partitioning scheme". Then copy a file called "bootia32.efi" to the "EFI/BOOT" directory. That file is a 32bit efi grub2 bootloader file. When starting, select the usb stick in the bios and it boots.
- WIFI: I got it working using the "ath6kl_sdio" wifi driver. However, I needed to use one with firmware 3.0 support, and that is in the "wireless-testing" repo, and not in 3.16. The 3.0 firmware itself you can download from [http://github.com/qca/ath6kl-firmware](http://github.com/qca/ath6kl-firmware) and extract it into /lib/firmware. Also needed is to tell the ath6kl driver that it can support the chip with SDIO id 0271:0418. It is a line like:

{SDIO_DEVICE(MANUFACTURER_CODE, (MANUFACTURER_ID_AR6004_BASE | 0x18))},

you have to add to the struct "static const struct  sdio_device_id ath6kl_sdio_devices[]" in the file sdio.c of the ath6kl driver so it will handle the  device.

Then the wifi works here.

For me the mobile keyboard is not working okay: at startup, the mouse works, but then the mousepointer stops moving as soon as I type one letter... really :) any solutions to that?

Best regards,
Tom,
Hello, all. I picked this thread up yesterday and attempted the procedure above on a Venue 11 Pro 5130 Atom processor. I used the AMD64 version, and I'm able to run the live version with touchscreen, active pen, external mouse and keyboard with the dock, and I have ethernet internet access (haven't messed with wifi yet). The problem I'm having is when I try to install, it crashes when trying to installing GRUB2. I've already blown away the abomination known as Windows 8.1 and have deleted all the partitions. It looks like Ubuntu itself installed properly on the drive, but it's not able to boot. How do I get around this? Thank you.

Edit - the version of Linux is [h=1]Ubuntu 14.04.1 LTS (Trusty Tahr)[/h]

---

### Post by john379 on 2015-03-11
Wondering if anyone can help me out.

I followed the above instructions, downloaded the latest AMD build from here [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) used RUFUS to put onto a USB drive with GPT Partitioning Scheme.  Added the 32bit EFI to the EFI/Boot dir and tried to boot. 

I get the bootloader but no matter what option I choose the screen just goes black and the system hangs immediately after attempting to load into the OS. 

The USB drive light also shuts off.  I have to hold the power button for 10 seconds to shut down and try again but same thing each time.

This is a Venue Pro 11 5130. 

Thanks for any suggestions!

---

### Post by axFelix on 2015-03-30
FYI, the touchscreen is broken again in 3.19, so I'm sticking with 3.18-6 (in Arch) for now. Guess we're not past regressions just yet :)

But still working perfectly apart from the front webcam.

---

### Post by ben-mueller1998 on 2015-03-30
I've seen people mention Arch is working pretty well across different sites, but nobody's mentioned how they got Arch installed. Could you point me in the right direction? Also, what do consider "perfectly"?

---

### Post by Meikrekel on 2015-04-06
I´ve been trying to install Antergos on the system. I can´t get it to install since I can´t connect to wifi. It doesn´t show me a dropdown list of available wifi networks or something like that. Everything else seems to work great but I can´t get it installed without WiFi.

I have the i3 4020y version.

Can someone explain me how they connected to their wifi network on Antergos?

---

### Post by souraka on 2015-04-14
i am connected now with my cell phone. so you can connect on wifi by your cell this is the only solution i found for the moment

---

### Post by eincry on 2015-04-22
Hello, I'm considering to get the core M version of Dell Venue 11 pro, and I need to dual boot with linux. How is the current status of linux support on this machine?

I will mainly use linux, so does the basic functionality of dispaly, wifi, keyboard, touchpad and the touchscreen work? Also, can it sleep when lip closed and wake up with all these functionality work? How about the other stuffs like stylus, camera and the external ports?

A quick look of this post seems positive, but I am not sure. Are there any one that can confirm it? I also want to know which kernel or distro work best. Thanks.

---

### Post by stef-baly on 2015-04-24
Dell pro 11 (i3) works quit fine with 15.04. In fact, the display bug has been solved with the new kernel 3.19.3 (It's ok with antergos too).
Problem : when waking from sleep the wifi interface disappears.

---

### Post by isnogood2 on 2015-04-24
> **stef-baly said:**
> Dell pro 11 (i3) works quit fine with 15.04. In fact, the display bug has been solved with the new kernel 3.19.3 (It's ok with antergos too).
Problem : when waking from sleep the wifi interface disappears.

Thanks for the info. I will try 15.04 this weekend (not a fan of arch/antergos). I found a little tool, to wake up the WiFi module. I think it's called something like "systemd-suspend-modules", maybe I found it in this thread some pages ago, I'm not sure.

---

### Post by luca-zerb on 2015-04-24
Today I've tested some different flavours of 15.04 and, besides the wifi disappearing after resume problem, the touchscreen was never working on all the different distrubutions that I've tried. Am I the ony one facing this problem?

---

### Post by isnogood2 on 2015-04-25
So far, I've testet Ubuntu 15.04 with Kernels 3.19.0, 3.19.3, 3.19.5, and 4.0.0. I couldn't get the touchscreen working with neither of them.

---

### Post by eincry on 2015-04-25
So it seems that it can be used as a laptop as the wifi, keyboard and tuochpad work. Is the touchscreen really doesn't work, even when unplug from the keyboard? The reply #96 says it works.

---

### Post by isnogood2 on 2015-04-26
It worked with kernels 3.17 and 3.18 but not with newer versions.

---

### Post by todd14 on 2015-04-30
Yes, ubuntu on my Dell Venue Pro 11 with a I5 and 256gig.....I am in......I would even pay to dump Windows on my dell tablet! Ubuntu need to help out here.....Desktop performance tablet running Ubuntu should be a hot item for the 100000 of dell venue's with I3 and I5's now....Where can we get nightly builds????? Where can we support the cause????

---

### Post by isnogood2 on 2015-05-14
Just installed kernel 4.0.3 and still no luck with getting the touch screen to work. I scrolled through "journalctl -b" and didn't even found an error in hardware recognition or something similar. I installed Ubuntu in EFI-mode, is it possible that that's the problem? Or maybe I have to configure systemd to recognize the touch screen? I'm clueless at this point.

---

### Post by isnogood2 on 2015-05-27
For now, I switched back to Linux Mint 17.1 with KDE and kernel 3.18.6. Everything is working in this configuration, except the front camera. I experimented with getting plasma-active to run on my machine, but somehow, it doesn't work. I guess, I have to wait für plasma 5 to appear in the repositories, so I can give it another try.
For now, I'm satisfied with how the system works. It's just that KDE isn't really optimized for touch input. I'll see what I can do about it.

---

### Post by luqmaninbmore on 2015-06-14
I 've got Ubuntu 15.04 installed and everything seems to be working except the touchscreen and the WiFi after suspend.  The latter doesn't matter to me much because boot times are so quick but I would very much like to correct the former.  I've tried kernel 3.18.6 to no avail.  I have an antergos live USB that features a working touch screen/wifi/etc., that is running on 3.17.6-1-Arch.  Unfortunately, being a rolling release, when I installed Antergos, it updated the kernel and I lost touchscreen input.  I've tried installing the 3.17.6 kernel in Ubuntu but it did not make the touchscreen usable.  What is so different between the Ubuntu and Antergos/Arch versions of the kernel that it would cause this difference in behavior?  

Isnogood2- How did you get Linux Mint 17.1 installed?  When I've tried it, it either didn't boot or, when it did, I didn't have a touch screen.  I tried the Debian 8.1 live cd- the touchscreen worked, but the keyboard dock and wifi did not and battery life was extremely attenuated.  Does anyone have any ideas where to proceed from here?  I can use it satisfactorily as a Linux laptop but I really need the touchscreen to work for me to be truly satisfied (I want to be able to detach the tablet from the dock).

---

### Post by isnogood2 on 2015-06-15
@[**[COLOR=#000000]luqmaninbmore[/COLOR]**]("http://ubuntuforums.org/member.php?u=1987985"): Mint 17 and 17.1 make use of kernel 3.13. You have to add "nomodeset" to the boot parameters, so the system can boot. The touchscreen doesn't work with this kernel, but you can now install kernel 3.18.6.  I should add, that the touchscreen doesn't work after every boot. A reboot usually helps.

---

### Post by togop2 on 2015-07-02
I've been trying to get the wi-fi driver working, but failing so far. What exactly do I need to do for that? Thanks

---

### Post by isnogood2 on 2015-07-06
@togop2: What WiFi-Chipset do you have? An Intel chipset should work out of the box. I don't know about other chipsets. The last thing, I read about that topic in this thread is, that it's better to switch to an Intel WiFi card.

---

### Post by togop2 on 2015-07-10
I have Intel Atom processor and Atheros wi-fi. Changing that would end the warranty, no?
Does anyone have a .deb of a properly patched kernel that works well and simply needs me to download the 3.0 firmware?

---

### Post by isnogood2 on 2015-07-14
I usually just copy-paste from here:
[http://www.yourownlinux.com/2015/02/how-to-install-linux-kernel-3-18-6-in-linux.html](http://www.yourownlinux.com/2015/02/how-to-install-linux-kernel-3-18-6-in-linux.html)

---

### Post by isnogood2 on 2015-10-29
I resurrect this thread today to ask, how you guys get along with your Dell Venues. I wasn't able to get the touchscreen to work on any kernel newer than 3.18. Yesterday, I installed Ubuntu 15.10 and the touchscreen still won't work. Can someone tell me, if it's a good idea to downgrade kernel 4.2 of Ubuntu 15.10 to kernel 3.18? So far, I failed at finding a good desktop environment, that's suitable for touch input.

---

### Post by isnogood2 on 2015-11-05
A patch to get the touch screen working is provided here: [https://bugzilla.kernel.org/show_bug.cgi?id=94281](https://bugzilla.kernel.org/show_bug.cgi?id=94281). I haven't tried it yet.

---

### Post by alistair12 on 2016-01-15
Maxxsire, I'm running Ubuntu Gnome 15.10 on a Dell Venue 11 Pro Core i5-4220v, 64-bit, and I just can't get the touchscreen or the wifi to work. I chose Gnome for this device specifically because it is supposed to be so great on tablets. Do a search and you will find other Venue users have had the same touchscreen/wifi problems. Fortunately, I bought the dock and am using my Venue wired with a Wacom tablet. I am seriously considering dumping Gnome for Lubuntu or Xubuntu, since I am using it as a "desktop".

---

### Post by isnogood2 on 2016-01-17
I'm now running Fedora 23 with Gnome. The touch screen is working, since I installed kernel 4.4. Unfortunately the automatic screen orientation doesn't work (worked with kernel 4.2). I guess, it has to do with the new kernel being a vanilla kernel.
Try installing kernel 4.4 on your Ubuntu. Maybe it will work.

---

### Post by togop2 on 2016-01-21
Do you know how to fix wifi after suspend on fedora? Touchscreen works for me, too, with vanila 4.4

---

### Post by isnogood2 on 2016-01-22
I haven't tried anything about this problem yet. But I remember something called "suspend modules", which takes care of this. Maybe it's mentioned in this thread.

---

### Post by sac123 on 2016-07-24
Hi all,

was anyone able to use a linux distro productively on Venue 11 Pro?

I just received mine (Core-M) and installation went relatively smoothless (after I discovered that the ISO images should be written in DD mode to the USB stick with Rufus). I tested Fedora 24, Ubuntu 16.04.1, Kubuntu 16.04., Ubuntu Gnome 16.04.1, Kubuntu 16.10, Neon User 20, OpenSuse Tumbleweed & Xubuntu 16.04.1. However all had the following issues:

**Fedora:** cannot wake up after the screen has been switched of (lid closed or inactivity)
**Ubuntu:** no wake up problems (the screen is always on), but touchscreen is not precise (try to touch the Firefox menu button)
**Ubuntu Gnome: **cannot wake up after the screen has been switched of (lid closed or inactivity) & touchscreen is not precise (try to touch the Firefox menu button)
[B]Kubuntu: the only supporting resume from suspend, but there's no Virtual Keyboard ( [https://blog.martin-graesslin.com/blog/2016/05/virtual-keyboard-support-in-kwinwayland-5-7](https://blog.martin-graesslin.com/blog/2016/05/virtual-keyboard-support-in-kwinwayland-5-7) )
OpenSuse: [/B]cannot wake up after the screen has been switched of (lid closed or inactivity)

Was anyone able to make suspend work on other distros? Seems the power button is not supported for locking ( [https://bugzilla.kernel.org/show_bug.cgi?id=102281](https://bugzilla.kernel.org/show_bug.cgi?id=102281) ), but as Kubuntu shows it can still be used to activate / deactivate suspend. This is somehow critical for me, but there are also some luxus issues: 
- no tested distribution was able to rotate the screen automatically, although the HW support seems to be there: [http://www.linlap.com/dell_venue_11_pro](http://www.linlap.com/dell_venue_11_pro) 
- automatic brightness adjustment is not working
(all the other HW is working out of the box: front&back camera,WLAN,slim typecover&touchpad)

Would be cool if anyone could recommend a distro, already solved some issues or has some info if I'm just not using this correctly (I always tested without swap partition & fully encrypted system).

Update: Standby issue: Added a comment to Kernel bugs including some workarounds ( [https://bugzilla.kernel.org/show_bug.cgi?id=102281#c56](https://bugzilla.kernel.org/show_bug.cgi?id=102281#c56) ). Solutions are there, but seems we need to follow some processes to get this into the distros.

---

### Post by sac123 on 2016-07-25
OK, so everything comes down to: [https://bugzilla.kernel.org/show_bug.cgi?id=102281](https://bugzilla.kernel.org/show_bug.cgi?id=102281)

All HW is working, but Distro independent there are 2 remaining Kernel problems:
1. keyboard / dock changes are not recocknized by linux (leads to the problem that the keyboard is not always recocknized after re-docking the tablet, leads to the problem that it cannot be woken up after sleep / freeze)
2. power button is not recocknized (leads to the problem that it cannot be locked / unlocked or woken after standby / freeze / monitor disable)

If anyone knows Kernel ACPI or has some contacts within the linux ACPI mailing list, it would be great if you can support [https://bugzilla.kernel.org/show_bug.cgi?id=102281](https://bugzilla.kernel.org/show_bug.cgi?id=102281) (I also forwarded the case to Dell, seems some faulty BIOS implementation prevents quick submission of the kernel patch).

---

### Post by christosmichaelas on 2016-08-07
I've got a Venue 10 Pro 5056 with Ubuntu 16.04.1 kernel 4.4.0-31 and below are the issues I'm currently experiencing:

- Touch screen not functioning
- Power button is not recognized
- Dell Venue keyboard brightness is not recognized (even root manual changes to brightness/ actual_brightness file makes no difference)

Other then the above, everything is working perfectly. I couldn't bare Windows any longer, so am willing to stick with Ubuntu until the above are fixed!

I'd like to think I can poke around a little, but I'm no expert...if any info is needed to help on this, I can post outputs and what not. 

By the way....battery life difference between running Windows 10 and Ubuntu? Windows would reach 4~ hours. Ubuntu - still measuring and nearing the end of the day...ha!

---

### Post by christosmichaelas on 2016-08-08
After some poking around, I couldn't find any touchscreen device using lsusb or xinput, so I started simply experimenting using the terminal application "screen" and the ttySxx files located in /dev/.

I placed an entry within the rc.local file to use a fujitsu driver for the ttyS0 device, even though the screen application would have no input from the touchscreen (I was just making a random change with no expectation of change). With a restart, still no difference although the xinput showed a Fujitsu device with id=11 (I thought "meh", probably just the input I made). I removed this change, restarted the tablet and for the most random of reasons, this has now appeared:

Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ITE Tech. Inc. ITE Device(8910)             id=8    [slave  pointer  (2)]
&#9116;   &#8627; ITE Tech. Inc. ITE Device(8910) Touchpad    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 4810 Pen stylus                   id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 4810 Finger touch                 id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 4810 Pen eraser                   id=14    [slave  pointer  (2)]

You can see there is now a Wacom touchscreen. Interestingly enough, the id is 11, the same as the random ttyS device I selected to use the fujitsu driver.

Anyhow, before all of this I updated the kernel to 4.4.0-34, the newest update, which had no effect before the above. It is possible it did, but it was not apparent until the above was done. 

No idea if this would be useful, as I don't believe I made any changes to the system...but it's working for now, which is great.

---

