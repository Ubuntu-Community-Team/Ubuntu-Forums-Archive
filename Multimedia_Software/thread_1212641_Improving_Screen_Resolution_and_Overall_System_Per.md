---
title: "Improving Screen Resolution and Overall System Performance"
date: 2009-07-13
forum: Multimedia Software
---

### Post by maporojo on 2009-07-13
I have installed a 64-bit version of Jaunty Jackalope on a SONY VAIO FW490. The swap size is 11.5GB. It has Intel® Core&#8482; 2 Duo Processor P8700 (2.53GHz), 4GB DDR2-SDRAM, and ATI Mobility Radeon&#8482; HD4650 graphics card with 512MB vRAM. The maximum screen resolution the 16.4" display can handle is 1600X900. At the moment, the only two options that I have in ubuntu are 800X600(4:3) and 640X480(4:3). While I will certainly have more questions on how to properly configure the machine to run ubuntu, the most pressing one is the following. How may I add higher resolutions to the list of options?

---

### Post by cozmicharlie on 2009-07-14
You need to install the ATI proprietary drivers.  Go to System>Administration>Hardware drivers.  You should see the ATI driver listed.  To install, follow the instructions here ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)).

Typically, the drivers listed are older but you can install them and update or install it manually ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English)).

hope this helps

---

### Post by maporojo on 2009-07-14
Thank you very much! I used the ATI driver listed under System>Administration>Hardware drivers. The display is great!

I have another question if you don't mind. How do I make ubuntu recognize the Pioneer CD & DVD reader and burner? I downloaded an image that I would like to burn to a DVD but Brasero Disc Burner says "No available disc". I can't even play an audio disc because RhythmBox Music Player does not recogninze the CD.

---

### Post by cozmicharlie on 2009-07-14
> **maporojo said:**
> Thank you very much! I used the ATI driver listed under System>Administration>Hardware drivers. The display is great!

I have another question if you don't mind. How do I make ubuntu recognize the Pioneer CD & DVD reader and burner? I downloaded an image that I would like to burn to a DVD but Brasero Disc Burner says "No available disc". I can't even play an audio disc because RhythmBox Music Player does not recogninze the CD.

Glad to hear the driver worked.

Strange that it is not recognizing your cd/dvd drive.  Was the cd/dvd drive installed when you installed ubuntu?  Normally, in Ubuntu you should not have to do anything for it to work.  

Lets try this first:

Open a terminal and type or copy and paste 
```
sudo modprobe ide-scsi
```
Press the Enter key to select the highlighted option. It sometimes takes more than one try.

If that works you are good to go.  If not then run:
```
cat /proc/scsi/scsi
```
Do you see your cd/dvd drive?

run
```
dvd+rw-mediainfo /dev/dvd

```
Does this see the drive?

As per playing music.  Have you installed the "Ubuntu Restricted Extras"?  Have you installed all the codecs (mp3 etc)?  If not follow the instructions here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and install all the codecs.

Hope this helps

---

### Post by maporojo on 2009-07-14
Thanks! I was able to get the music to work. I implemented the procedures upto Part 2/5 from the link you gave me. I don't think I need Part 3/5 so I omitted it. I didn't implement Part 4/5 and following because of the first note in Part 4/5 concerning disabling CD/DVD-ROM which I didn't understand.

The issue with audio at the moment is that when I plug in a headphone, I get sound from both the built-in speaker(s) and the headphone. Do you know how to correct this problem?

I still cannot get ubuntu to recognize the CD/DVD drive. The drive came with the machine and in fact I used Vista Home Edition to create three recovery DVD's before installing ubuntu using the entire HDD. Before I show you what messages I got after typing the commands above (and rebooting), let me mention that anytime I boot the machine since installing ubuntu, I see two error messages saying something like:

[6.964010] ata2.00 failed to set xfermode err_mask=0x4
[97.308010] ata2.00 failed to set xfermode err_mask=0x4

and then the booting sequence continues until I get the log-in window.

Now, the commands and messages I get are:

Command:    sudo modprobe ide-scsi

Output:

FATAL: Module ide_scsi not found.

Command:    cat /proc/scsi/scsi

Output:

Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Hitachi HTS54323 Rev: FB4O
  Type:   Direct-Access                    ANSI  SCSI revision: 05

Command:    dvd+rw-mediainfo /dev/dvd

Output:

/dev/dvd: unable to open: No such file or directory

---

### Post by cozmicharlie on 2009-07-15
Well we are 2 for 3 at least.

The cd/dvd is baffling because it is recognizing the cd/dvd.  The cat /proc/scsi/scsi command shows it is attached.  I forgot to tell you to put a blank dvd into the drive then run  dvd+rw-mediainfo /dev/dvd.  It is seeing your drive but it may not be mounting it for some reason.  Let me do some searching and see what I can find.  If this is beyond my somewhat limited expertise I would suggest posting a new thread with a new subject - something like "cd/dvd drive not responding".  You would not be double posting because this thread started out on another subject.  Let me do some digging first and see what I can find.

---

### Post by cozmicharlie on 2009-07-15
two more items I need.

type this in a terminal and post the results:
```
cat /etc/fstab
```

Type this in a terminal and post the results:
```
lspci
```

---

### Post by maporojo on 2009-07-16
Thanks for the feedback. I'll post the message shortly. I inserted a blank DVD+R and below is what I got.

Input: dvd+rw-mediainfo /dev/dvd

Output:

/dev/dvd: unable to open: No such file or directory

Input: cat /etc/fstab

Output:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7e25bcff-5a79-4b74-88e0-336d22848146 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a162b9de-1a0c-4a26-9286-b1740d9bb58b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Input: lspci

Output:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
06:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
0a:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

---

### Post by cozmicharlie on 2009-07-17
Go ahead and post a new thread - I am sure someone will help. I am not sure why it is not mounting your drive.

---

### Post by maporojo on 2009-07-17
Thanks! I greatly appreciate your help. Now if I can only find the link to post a new thread ... I wonder whether this site's layout/design changes often or the link for creating new threads is just hidden somewhere.

---

### Post by cozmicharlie on 2009-07-17
> **maporojo said:**
> Thanks! I greatly appreciate your help. Now if I can only find the link to post a new thread ... I wonder whether this site's layout/design changes often or the link for creating new threads is just hidden somewhere.

No problem - I am sure someone will help with the drive.

Go to Forum Tools.

---

### Post by niceguy123 on 2009-07-19
> **cozmicharlie said:**
> You need to install the ATI proprietary drivers.  Go to System>Administration>Hardware drivers.  You should see the ATI driver listed.  To install, follow the instructions here ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)).

Typically, the drivers listed are older but you can install them and update or install it manually ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English)).

hope this helps

I'm using intrepid on a sony VGN-FW250j 1600X900 screen. 

1. I went to System>Administration>Hardware drivers, its empty. Nothing to choose from there. 

2. Tried this:
```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```
and got 
```
insmod: can't read '/lib/modules/2.6.27-7-generic/volatile/fglrx.ko': No such file or directory
```

Can someone help me configure my screen resolution 'cause it really uncomfortable to work with the screen all stretched out of shape.

Thanks.

---

### Post by cozmicharlie on 2009-07-20
niceguy123 - what type of graphics card do you have in your computer?

---

### Post by niceguy123 on 2009-07-21
> **cozmicharlie said:**
> niceguy123 - what type of graphics card do you have in your computer?

I'm not sure how I see the specs actually on the computer but from a google search I got the following:

> The VAIO FW is a 16.4" notebook featuring an Intel Core 2 Duo P8400 processor with great options including: Blu-Ray, a 1600 x 900 viewing format, a HD video card, ATI 3650 or ATI 3470, and an HDMI port to output.

---

### Post by cozmicharlie on 2009-07-21
> **niceguy123 said:**
> I'm not sure how I see the specs actually on the computer but from a google search I got the following:

To find out which graphic card you have, copy and paste he following in a terminal:
```
lspci -nn | grep VGA
```

According to the specs you provided it should have an ATI card.  Older cards are not supported by the newer ATI drivers (fglrx), that is why you do not see anything listed under "Hardware drivers".  You should be using the radeon driver which should be installed when you install Ubuntu.  You can check by going into synaptic and search for radeon.  

If as I suspect the above is correct then you need to adjust your xorg file to fix this.  I would first update your xorg file to the latest stable release.  To do this follow the steps below (note this is a stable release so it should be safe but make sure and backup any important files just in case).

Open Synaptic and go to Settings>repository>Third party software and click "Add">  Add the following lines one at a time.
[HTML]deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main [/HTML]    
[HTML]deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main [/HTML]
Close Synaptic, open a terminal, copy and paste the following:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
```
```
sudo apt-get update

```
Restart your computer.

This will update your xorg file and may fix the problem.  If not then we will have to try some of the suggestions posted here [http://ubuntuforums.org/showthread.php?t=83973&highlight=VAIO+FW](http://ubuntuforums.org/showthread.php?t=83973&highlight=VAIO+FW).

---

### Post by niceguy123 on 2009-07-22
Coz,

Thank you for your help.

Here are the specs:

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
```

Aside for that none of this worked for me. I tried to exit X and got a never ending error message, some thing like:

```
[number] bad:scheduling from the idle thread!
``` 

If I do ```
sudo nano /etc/X11/xorg.conf

``` 

How and where do I update the file?

---

### Post by cozmicharlie on 2009-07-22
You do not have to update the file at /etc/X11/xorg.  When you run the command sudo apt-get update it updates it for you.  I googled the error and it looks like a bug that is fixed in the newer kernel (see this thread - [http://ubuntuforums.org/showthread.php?t=977090](http://ubuntuforums.org/showthread.php?t=977090)).  It appears a kernel upgrade using the "proposed" repository will fix this.  The easiest way to do this is go into Synaptic>settings>repository>updates and check Pre-release updates (jaunty-proposed).  Restart your computer.  

If that does not work then we will try this [http://ubuntuforums.org/showthread.php?t=1124159&highlight=bad%3Ascheduling+idle+thread](http://ubuntuforums.org/showthread.php?t=1124159&highlight=bad%3Ascheduling+idle+thread).

---

### Post by niceguy123 on 2009-07-23
Coz,

I've tried all of the above, BTW updated my OS to Jaunty on the way. Still no change for the resolution. What do you suggest I do now?

---

### Post by cozmicharlie on 2009-07-23
> **niceguy123 said:**
> Coz,

I've tried all of the above, BTW updated my OS to Jaunty on the way. Still no change for the resolution. What do you suggest I do now?

I should have asked - I assumed you were in jaunty.  Since you moved to Jaunty did you do the upgrades using the proposed repository?  If so then we have to resort to doing it as described here [http://ubuntuforums.org/showthread.php?t=83973&highlight=VAIO+FW](http://ubuntuforums.org/showthread.php?t=83973&highlight=VAIO+FW).  Do you know the screen resolution and refresh rates for the monitor?  It should be in the manual.

---

### Post by niceguy123 on 2009-07-23
> **cozmicharlie said:**
> Do you know the screen resolution and refresh rates for the monitor?  It should be in the manual.

No, I do not have the refresh rates. The resolution is 1600X900; Aspect ratio 16:9

I found manuals on the internet but didn't see refresh rates listed there.

---

### Post by cozmicharlie on 2009-07-23
The first change to make is this ([http://ubuntuforums.org/showpost.php?p=679706&postcount=23](http://ubuntuforums.org/showpost.php?p=679706&postcount=23)) so you can see the changes without having to restart your computer.

I assume I do not have to tell you to open a terminal and copy and paste commands.  Anytime you see code assume you need to open a terminal and type or copy and paste the command.

```
sudo xinit -- :2
```

Now you should be able to view the changes to x by doing (ctrl+alt+F9) and if something is wrong you can go back to your original X by typing (ctrl+alt+F7)

Lets start with a couple things that make life in Ubuntu much easier.  Install Ubuntu Tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)).  go to the download page and follow the directions for Jaunty.  Start Ubuntu Tweak and go to System>Nautilus and check "Nautilus with open terminal", Nautilus with root previleges", hit apply.  Then go to personal>scripts.  On the right column find 'Open with gedit as root", Browse as root" and open with gedit" and move them to the left column. Go to Applications> third party source and check "medibuntu", Ubuntu tweak (unstable version) and Ubuntu X then refresh.  The update manager should appear and you should update.  Go into synaptic and install the "ubuntu restricted extras".  Restart your computer.  Ubuntu Tweak is a great program so play around with it.  What I had you do is add Nautilus scripts that allow you to change to root and edit as root by right clicking.  Open a folder, right click on a subfolder and go to "scripts".  You should see the scripts we just added.  So now to open a file like xorg which requires root permissions all you do is go to the file, right click>scripts>open with gedit as root.  Or you can "browse as root".  Another way to browse as root is go to the menu>edit>open as administrator.  This makes life very easy.  One more change I always make is in Nautilus (just open a folder) go to  edit>preferences>behavior I always check "include a delete command that bypasses trash".  That is up to you - I just hate using trash.

Once you do that we are ready to edit xorg.  Go to /etc/X11/xorg and open it by right clicking>scripts>gedit as root.  Before we start paste your xorg file so I can see what it looks like.  Then we will start the changes.

---

### Post by niceguy123 on 2009-07-23
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by cozmicharlie on 2009-07-23
This shows you are using the vesa drivers which are not going to give you many options.   Based on the specs you provided your computer should have an ATI card and therefor you should be using the radeon drivers which are much better.  Run one more command and see if an ATI card shows up.

```
lspci
```

---

### Post by cozmicharlie on 2009-07-23
Is this your computer?
[http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGNFW250J&LOC=3](http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGNFW250J&LOC=3)

---

### Post by niceguy123 on 2009-07-23
> **cozmicharlie said:**
> Is this your computer?
[http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGNFW250J&LOC=3](http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGNFW250J&LOC=3)

Yes, that is my computer.

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
09:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

```

---

### Post by cozmicharlie on 2009-07-24
First backup your /etc/X11/xorg.conf file to somewhere safe so we can go back to it if we get in trouble.  The problem is that you do not have an ati card but intel embedded graphics.  I have found a few things that people have reported to work.  lets start with the easiest.

According to everything I have read, an update should fix this.  Did you mark the proposed updates and do an update?  If so then apparently it is not working as they say.  If that does not work then follow the step below.

Lets start making just a few changes and see if they work.  Open the etc/X11/xorg.cong as edit as root and make the changes to the device section.  Restart and (or cnt+alt+F9).

Section "Device"
Identifier "intel"
Driver "intel"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

---

### Post by niceguy123 on 2009-07-24
Coz,

It worked!!!

This is amazing!!!

Thank you so much for your help and your patience.

BTW - I have a new problem, since I upgraded to Jaunty I can't shut down or restart. When I do, I just get a black screen with a little sensor but the computer does not turn off. The only way I can get it totally closed down is to detach the power and battery. Can you help?

---

### Post by cozmicharlie on 2009-07-24
> **niceguy123 said:**
> Coz,

It worked!!!

This is amazing!!!

Thank you so much for your help and your patience.

BTW - I have a new problem, since I upgraded to Jaunty I can't shut down or restart. When I do, I just get a black screen with a little sensor but the computer does not turn off. The only way I can get it totally closed down is to detach the power and battery. Can you help?

Great!  I don't know why Ubuntu still has so much trouble autoloading the drivers but it does.  Glad it worked.

As per the shutdown.  I have had this problem before and it usually gets fixed with updates.  Since yours has not I would try booting using the noapic command.  When you boot, hit escape when grub comes up.  This should take you to the menu with the kernel listed, go to options, select e to edit the kernel, add "noapic" (without quotes) to the line, hit enter and hit b to boot.  This is only a temporary fix so if it works then you will need to add the noapic line to the grub boot menu.  To do this open /boot/grub/menu.lst as root.  Look for this line:
> # kopt=root=/dev/sda1 ro
Change it to this (do not remove the #)
> # kopt=root=/dev/sda1 ro noapic
Run this:
```
sudo update-grub
```

That should work - if not you may have to just live with it until an upgrade fixes the problem.

---

