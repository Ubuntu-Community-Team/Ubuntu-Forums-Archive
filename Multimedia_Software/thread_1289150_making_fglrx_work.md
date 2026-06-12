---
title: "making fglrx work"
date: 2009-10-12
forum: Multimedia Software
---

### Post by Debianforce on 2009-10-12
Hello there. 
I have the ATI graphics card Asus EAH4850 Radeon HD.
A AMD64 processor, 4GB RAM, a Gigabyte mainboard ( with integrated gpu, disabled in bios )and a awesome chassis called antec fusion remote max.  
This is connected to a 37" LCD TV from Hitachi. ( DVI on  PC to VGA on TV. On HDMI cable, this installation is 100% impossible. ) When booting a ubuntu install CD, Debian install CD, or even e linux mint install CD, the installer ask med to enter a fitting screen resolution before continuing. whatever I choose, this fails. ( this happens after you push ENTER and the cd boots.. It boots to a terminal and asks for correct resolution ) After this, the screen is black, no matter what I try..

When trying to install windows7, windows xp, or even wintendo 2000, they all installs fine. No problemo...

The only installer that works for linux, is Opensuse 11. That installer correctly finds the 1024x768 resolution, and I can continue the installation.

Why is this? 

Also, on whatever distro I try, the fglrx drivers are impossible to install it seems. The only OS that shows the gnome desktop or the KDE desktop in 1024x768 resolution, is, once again opensuse 11..

When the driver is installed "The hard way" the sceen gets black and nothing works. The opensuse OS, also fails if I try the fglrx driver there...( yes i have tried around 1000 ways to install the driver.. )


Could someone please tell me what the xorg team / the linux kernel team have done to the systems? Why is it so hard to install the graphics card now?

For about 3 years ago, this was never an issue, because you had total control over your xorg.conf file, and you could change it as you wished. Now the file is almost ignored by the system.. 

Is there a way to bypass this, and make sure the computer boots into 1024x768.
It seems the kernel is talking to a "hal" or "hald" file, and gets information from this, during boot? 
According to my logs the kernel boots the pc into some insane resolution more fitting to a laptop.. like 1940x2024 or something like that. This happens in ubuntu, debian, fedora, linux mint and so on.. 

Except opensuse 11..

Whats going on? I'd like to use linux. Opensuse is okay, but..my heart belongs to debian.. or ubuntu :-)
Could someone please point me in the right direction to find out this?
:wink:

---

### Post by markbuntu on 2009-10-12
Your best bet would be to install in "safe graphics mode" which you can choose with F4 when the first menu comes up from the live cd. This will use the default VESA driver and get you installed albeit with a low resolution graphics screen like 1024x768 or something like that.

Once you are installed and things are working you should skip the offered proprietary driver and get the latest one from the ati driver site and install that.
Be sure to read the installer instructions.

DO you have a 4850x2??

---

### Post by manishsk on 2009-12-04
Try below commands immediately after installing the fgrlx driver and then reboot:

>  sudo aticonfig --initial -f
 sudo aticonfig --acpi-services=off 

---

### Post by efflandt on 2009-12-04
I could see where you may have trouble booting if actually connected with DVI digital (or HDMI), but puzzled why you are having an issue when using the analog of DVI to VGA (which I would think would be effectively VGA and default to some usable VGA mode).

My 1280x1024 monitor booted fine using DVI or VGA.  When I switched to an older widescreen 1280x720 native HDTV using DVI, X worked fine.  Although, I switched monitors during suspend and it came up in 1280x1024 stretched mode, once I logged out of X and back in it recognized its native 1280x720 in proper aspect ratio (ie, circles were round and squares were square).  However, when I rebooted, after the grub2 menu, I got a blinking cursor for a second and then black (no video or disk activity forever).  Although, I could boot fine to a console in recovery mode, and gui login worked perfectly if manually using grub2 commands.

Then it dawned on me that it might be a video mode issue, and when I switched from DVI to VGA, it booted with no issues at all.  Except when using VGA, X did not know its native mode, and the only optional widescreen mode it offered was 1360x768 (which did work).

Apparently something has an issue with "splash" as a boot parameter, and if I remove that in /etc/default/grub and sudo update grub, then I can boot fine using DVI widescreen.

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# "splash" apparently does not like widescreen DVI/HDMI
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

Note that setting GRUB_GFXMODE=640x480 instead, seemed to be ignored and did not fix the splash DVI/HDMI boot falure.

I do have an ATI AGP 256 MB video card, but fortunately other than the "spash" issue, it works fine in Ubuntu 9.10 with default radeon kernel module and default X modules.

---

