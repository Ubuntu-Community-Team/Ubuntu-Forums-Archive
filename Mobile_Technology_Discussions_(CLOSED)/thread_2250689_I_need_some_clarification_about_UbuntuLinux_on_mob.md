---
title: "I need some clarification about Ubuntu/Linux on mobile devices."
date: 2014-10-30
forum: Mobile Technology Discussions (CLOSED)
---

### Post by bart15 on 2014-10-30
Hi!
I'm not new to Linux - I've started using Slackware in about 2001, but I'm completely new to Linux on mobile devices, well and I'm not very interested in hardware. So I would like to clarify some of my findings.
Since some tablets are now build on Intel processors I was thinking of buying such device with external keyboard instead of small notebook.

Now - some general Linux questions (in points - I hope it'll be less messy this way):
1. Do I assume this correctly? If tablet is based on Intel Atom 32bit processor, and I'll install Linux on it, then I can install any 32bit version of package (deb, rpm) from distro software repository. I'm not limited only to software which was compiled on ARM. Or am I missing something?
2. The device should allow to disable secure boot, and enabling sth. which is called legacy boot. Of course the distro should have drivers for all hardware, but leaving this aside, are those only 2 limitations to install Linux on the device?
3. Where the distro will be intalled? When tabled has 32Gb of internal storage, can I install it there, or only on SDcard?
4. Does the installation process is similar to normal PC installation - I plug USBstick, boot from USB and proceed with installation.

And the Ubuntu-specific questions:
1. I've found this description [http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/) but it seems it targets Nexus so afaik ARM processor, thus I assume that all apps for Ubuntu tablet distro are build for ARM and won't run on Intel. Is that correct? Is there Ubuntu tablet version for Intel processors?
2. What is Ubuntu for Android - is it sth. like an emulator (virtual machine) for Android system? Or is it completely different system which creates its own file system and uses Android only to boot Ubuntu? For me the description on [http://www.ubuntu.com/phone/ubuntu-for-android](http://www.ubuntu.com/phone/ubuntu-for-android) has to little details.
3. What is Ubuntu SDK. You see, I'm targeting the Intel tablets so I could install all the aps from Ubuntu repositories. But I've started to wonder if this SDK isn't some kind of virtual machine with gcc and libs so I can run any app and don't mind whether I'm using ARM or Intel. Or SDK only allows to run HTML5 apps on different platforms and when I'd like to install e.g. Gimp I still need Gimp compiled for Arm or Intel.
4. Final;) Did anyone had success with installing Ubuntu (typical 32 desktop distro) on"
- Dell Venue 8 (I saw a topic above;) but it is about PRO version) this one uses Intel® Atom&#8482; Z2580, 2.0 GHz and Android 4.2
- Lenovo Yoga 2 with Intel® Atom&#8482; Z3745, 1,33 - 1,86 GHzand Android 4.4
- Kiano Intelect 10 [http://www.imei.info/phonedatabase/15085-kiano-intelect-10/](http://www.imei.info/phonedatabase/15085-kiano-intelect-10/)
- Asus VivoTab smart with Intel® Atom&#8482; Z2760, 1,8 GHz and Windoes 8.1 32bit.
Since I was usually installing Linux next to Windows I thought the Asus will be right choice, but Kiano is half the price. Also I'm afraid that brands like Asus, Dell, Lenovo may use some safety settings which won't allow to install different system.
Some ideas? What would you choose?
Thanks.

---

### Post by grahammechanical on 2014-10-30
I think that you are confusing two different things. There is Ubuntu desktop which can be installed on X86 compatible CPUs made by Intel and AMD.  Whether Ubuuntu can be installed on the devices that you are thinking of, I suggest that you do not take anything for granted. You may be an early adopter in this matter. You may find a thread somewhere on this forum about installing on a Intel Atom powered machine. What you also need to find out is whether there is a video driver for the GPU. And then there is Ubuntu for devices. This is being developed to be preinstalled on Ubuntu phones and tablets for retail. And they will be powered by ARM CPUs. Over the next 18 months the Ubuntu for devices code will be merged into the Ubuntu desktop code so that there is one Ubuntu code base. I am posting this from the Ubuntu phone user interface but I am running an Intel Core 2 Duo desktop machine. I have installed Ubuntu Desktop Next (amd64). It is where this convergence of the phone/tablet code into the desktop code is taking place. Right now it has the phone user interface without access to the standard Ubuntu desktop user interface. So, there is a long way to go. The Ubuntu Software Centre does not offer applications that cannot run on the hardware.  By the way, posting multiple questions like this is not the best way to get accurate information. Break your questions up into separate threads and post into the appropriate section of the forum.

---

### Post by grahammechanical on 2014-10-30
The Ubuntu Software Development Kit (SDK) runs on Ubuntu desktop. It is designed to make it easy for developers to write applications for Ubuntu, primarily, applications for Ubuntu for devices (phones and tablets). It makes it easy for the developer to package the application and to get it approved for inclusion in the Ubuntu for Devices app store. It is not some kind of Virtual Machine or emulator for that matter. It is an Integrated Development Environment (IDE) that uses a limited set of programming languages (including HTML5) but it could in future be developed to include other programming languages. There is a Ubuntu Emulator but that emulates the hardware of certain mobile devices. It purpose is to make it possible for developers to test their applications without having to purchase the various devices.

---

### Post by grahammechanical on 2014-10-30
And then there is the Ubuntu Developer Tools Centre. That also is not meant to be an Android emulator. It purpose is to make it very easy to install on Ubuntu the Android Software Development Kit and Android Studio. I do believe that it will help an Android developer port their apps to Ubuntu for Devices. This is all part of an intention to make Ubuntu the platform of choice for developing applications and not just for Ubuntu and Linux.

---

### Post by oldfred on 2014-10-30
There is this thread on Dell 

       Dell Venue Pro 8/11 with ubuntu?
    [http://ubuntuforums.org/showthread.php?t=2187204](http://ubuntuforums.org/showthread.php?t=2187204)

Recently there has been a 32bit version of Linux UEFI boot.
Some of those type systems have the UEFI class 3 devices which then do away with the CSM/BIOS boot option. And since Linux did not have 32 bit version, they thought they locked system. But they usually are 64 bit hardware crippled with a 32 bit operating system to prevent anything other than Windows from installing.

       Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)
Packard Bell ENME69BMP InsydeH2O  or Gateway LT41P04u
32-bit UEFI Support Proposed For Ubuntu Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE)

 Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

---

### Post by sam-c on 2014-11-06
Android from Google is Linux. Ubuntu is a very popular linux from Canonical.
Start from there and "Drill Down" a lot of info is on wikipedia. 
Uncle Sam
PS True Some Mobiles are Ubuntu Touch Friendly others not.

---

