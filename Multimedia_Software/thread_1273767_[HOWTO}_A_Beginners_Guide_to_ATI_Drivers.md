---
title: "[HOWTO} A Beginners Guide to ATI Drivers"
date: 2009-09-23
forum: Multimedia Software
---

### Post by humphreybc on 2009-09-23
Hi guys, I just wrote all this up for the [Video Community Documentation]("https://help.ubuntu.com/community/Video") and I thought I would post it in here for some feedback. I'll make the changes you guys suggest and then hopefully I can remove this paragraph and we can have it as a sticky. I think at the moment it's quite confusing for new Ubuntu users to decide what drivers to use, and how to use them... there is a lot of information but not much is summarized on one page. Please note, **I AM NOT AN EXPERT ON ATI DRIVERS**, so some of this information will probably be inaccurate or incomplete, that's why I need your help.

Here goes:

**A NOTE ON THE DIFFERENT TYPES OF ATI DRIVERS**

This covers:
 - The two different driver types
 - How to get your hands on these drivers
 - How to install/upgrade the fglrx drivers (the easy way)
 - How to recover a non-booting system due to driver malfunction

**The two different driver types and How to get your hands on these drivers**

At present, there are two types of drivers available for ATI graphics cards.

1) The community-maintained open source xserver-xorg-video-ati or xserver-xorg-video-radeon driver (sometimes referred to as "radeon")

and

2) The proprietary (closed source) driver from ATI themselves (referred to as "fglrx").

There are several pros and cons for each type of driver. The most prominent are that the fglrx driver supports better 3D and OpenGL, as well as better Hardware processing as it is developed by the ATI engineers themselves and often has better features. It also supports Xinerama for dual-screen setups. On the other hand, the open-source driver supports older graphics cards, and is open source for those wanting a complete "free" system. It supports limited 3D, but full 2D acceleration and is suitable for most people, and some argue that it has better dual screen support that ATI fglrx drivers - although in recent driver versions (Catalyst 9.5 and above), ATI have made many bug fixes that address dual screen issues in previous versions.

With that in mind, there are presently FOUR ways to install these drivers:

1) By default on a fresh install of Ubuntu, the open source "radeon" driver is installed. This provides 2D acceleration and limited 3D acceleration for newer cards. In Synaptic Package Manager, this driver is called "xserver-xorg-video-ati" or "xserver-xorg-video-radeon".

2) In "Hardware Drivers" (found in System > Administration), Ubuntu will suggest an often OLDER version of the proprietary drivers to install. These are not the latest drivers from ATI, as they have been tested by Ubuntu developers which takes time. These drivers are often quite reliable and very easy to install, but will not provide the cutting edge new features and bug fixes from ATI. They are automatically updated with Update Manager, but updates for this driver infrequently come out. At the moment, it is not possible to see what version of Catalyst drivers are being installed by Hardware Drivers until after you install them... making it difficult to compare with the ones available on ATI's site.

3) The fglrx drivers can also be installed/uninstalled in Synaptic Package Manager. The relevant packages are:

xorg-driver-fglrx
fglrx-amdcccle

This installs the fglrx driver and the Catalyst Control Center. As in 2), it is not possible to see what version of the Catalyst drivers are being installed until after you install them (and then you can run fglrxinfo in a terminal window to check, or go to the Catalyst Control Center). These drivers share the same properties as the ones in 2). PLEASE NOTE: If you install the open source drivers, you do NOT need these drivers installed. Also, If you install the drivers from the ATI website (4), then you do NOT need these drivers installed. This prevents unnecessary conflict of drivers.

4) The final way to get drivers is from the ATI website ([www.ati.amd.com](www.ati.amd.com)). These are the most recent and full-featured drivers, but are also the most complicated to install, are not fully tested by the Ubuntu developers, and are not automatically updated by Ubuntu. These drivers are released once a month, with the current release being Catalyst 9.10 (as at October 2009). From Ubuntu Karmic Koala, the 9.10 drivers are INCLUDED, so the drivers available in numbers 2) and 3) will be the latest Catalyst drivers. Please note these will get out-of-date over time until the next Ubuntu release, in April 2010. Please see the binary HowTo to get the ATI drivers installed. 

**How to install/upgrade the fglrx drivers (the easy way)**

Here is a quick guide on how to install/upgrade the proprietary drivers from ATI:

Open a terminal window and issue these commands:

First, uninstall the old ATI drivers:

NOTE: Please, please, please be careful with the "rm -rf" command - if you get this wrong, it could break your system!! Proceed with caution.

```

cd /usr/share/ati/
sudo sh ./fglrx-uninstall.sh
cd ~
sudo rm -rf /etc/ati/
sudo apt-get remove -purge xorg-driver-fglrx fglrx-amdcccle

```

Change the ownership of the installer downloaded from ATI and run the installer. This presumes you downloaded to your HOME directory. Please remember to change the filename depending on driver version.

```

sudo chmod +x ati-driver-installer-9-9-x86.x86_64.run
sudo sh ati-driver-installer-9-9-x86.x86_64.run

```

Now, reconfigure the xorg.conf file (READ: DON'T DO THIS IF YOU HAVE A SPECIAL SETUP, eg. DUAL MONITORS.) The backup is created automatically.

```

sudo aticonfig --initial -f

```

Then reboot your computer:

```

sudo reboot now

```

Your computer should boot up with the new drivers. To check what version you have, either run the Catalyst Control Center (if it is not in the Application menu, right click and go "edit menus" and check the option to display it), or you can run this:

```

fglrxinfo

```

**How to recover a non-booting system due to driver malfunction**

If your computer does not boot when you have upgraded drivers, press escape at the GRUB bootloader, then choose "recovery mode" for your latest kernel. Drop down to "root shell" and then run the ATI uninstaller:

NOTE: Please, please, please be careful with the "rm -rf" command - if you get this wrong, it could break your system!!

```

cd /usr/share/ati/
sh ./fglrx-uninstall.sh
cd ~
rm -rf /etc/ati/
apt-get remove -purge xorg-driver-fglrx fglrx-amdcccle

```

Then run this to restore your xorg.conf file to default:

```

dpkg-reconfigure -phigh xserver-xorg

```

The computer should boot now using the open source "radeon" drivers, (it is important to keep these installed for a backup for this exact reason). If it doesn't boot with the radeon drivers automatically, go:

```

nano /etc/X11/xorg.conf

```

Where it says "Device" you want to type "radeon" or "ati" in the "Driver" field, so it looks like this:

```

Section "Device"
	"Driver"      "radeon"
EndSection

```

Once you have booted back into Ubuntu, revert to an older version of the fglrx drivers, or continue to use the open source drivers if you like.

NB: These instructions can also be used with the LiveCD if you don't feel comfortable with using a root shell environment. I'll add some instructions on how to do this with the LiveCD later if there is demand for it.


==== GOOD LUCK! ====

---

### Post by humphreybc on 2009-09-28
Nobody has any feedback? Am I going to assume it's perfect! haha

---

### Post by Yellow Pasque on 2009-09-29
A comprehensive proprietary ATI driver guide: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Also, special consideration needs taken when switching from proprietary back to open-source drivers: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by Pasdar on 2009-09-29
Drivers from ATI website most complicated to install?

chmod +x file.bin
./file.bin

click click... done

really that difficult?

I've heard there are ways to solve certain issues, like video tearing and delay in maximize, etc... tweaks... how about a tutorial explaining those kinds of things... :p

---

### Post by Bloemetjesgordijn on 2009-09-29
Thx humphreybc for your how to

I have allways had issues with installing ATI drivers. (especially with Hybrid Crossfire). But I will give it a go again.

Wish me luck

Cheerz

Bloemetjesgordijn

---

### Post by humphreybc on 2009-09-29
> **Pasdar said:**
> Drivers from ATI website most complicated to install?

chmod +x file.bin
./file.bin

click click... done

really that difficult?


Well they are difficult relative to the other ways to install drivers - ie, Add/Remove programs, Hardware Drivers, or Ubuntu doing it automagically.

> 
I've heard there are ways to solve certain issues, like video tearing and delay in maximize, etc... tweaks... how about a tutorial explaining those kinds of things... :p

I would, but unfortunately these "tweaks" are often not a general answer for everyone, so it's rather hard to make a *beginner* guide for this, as it would use a lot of variables (ie "ifs" and "buts") which can be confusing. The aim was simple and to the point just to get people aware of the different types of drivers, and where to get them.

---

### Post by mudsnake on 2009-09-29
Hi..Since I am new to the Linux desktop it helped. Before this I had some issues. Now if it only had a crossfire option or maybe I am over looking it. I am probably not looking in the right place if it's even possible..
I do appreciate the help....oh and I used the driver download from ATI :P

---

### Post by markbuntu on 2009-09-29
You should note that some of the newer cards like the 4890 and 4870 and many of the 3xxx agp cards and igps are not supported by the fglrx driver in the repository. Also, multi gpu and multi monitors is now usable with the newer fglrx drivers from ati with any 3xxx and 4xxx cards though not with igps. Also x2 cards need to be initialized with

aticonfig --adapters=all --initial

It would also be good to tell people that older fglrx versions must be removed before installing new ones or the fglrx kernel modules will fail to build on kernel updates.

---

### Post by markbuntu on 2009-09-29
> **mudsnake said:**
> Hi..Since I am new to the Linux desktop it helped. Before this I had some issues. Now if it only had a crossfire option or maybe I am over looking it. I am probably not looking in the right place if it's even possible..
I do appreciate the help....oh and I used the driver download from ATI :P

aticonfig --help 

will list crossfire configuration options

---

### Post by Milonguero Viejo on 2009-10-02
How would you address this problem: A certain Gigabyte mobo with built in graphics (Radeon 2100) runs Vista and detects just fine my Toshiba 40X645  HDTV  used as monitor. A brand new 9.04 install will ALWAYS detect the screen as a 47" screen and will display accordingly (aweful). All commands and menus are hidden by the extra real estate that is out of sight. Is this a driver issue?. The Xorg.conf file is completely empty. Any ideas?

---

### Post by humphreybc on 2009-10-02
> **Milonguero Viejo said:**
> How would you address this problem: A certain Gigabyte mobo with built in graphics (Radeon 2100) runs Vista and detects just fine my Toshiba 40X645  HDTV  used as monitor. A brand new 9.04 install will ALWAYS detect the screen as a 47" screen and will display accordingly (aweful). All commands and menus are hidden by the extra real estate that is out of sight. Is this a driver issue?. The Xorg.conf file is completely empty. Any ideas?

Are you using the fglrx catalyst drivers, if so, what version? Or are you using the open source radeon/ati drivers?

There should be something in your xorg.conf file. Check you're looking at the right one:

sudo gedit /etc/X11/xorg.conf

Remember, Linux is case-sensitive.

---

### Post by humphreybc on 2009-10-02
> **markbuntu said:**
> You should note that some of the newer cards like the 4890 and 4870 and many of the 3xxx agp cards and igps are not supported by the fglrx driver in the repository. Also, multi gpu and multi monitors is now usable with the newer fglrx drivers from ati with any 3xxx and 4xxx cards though not with igps. Also x2 cards need to be initialized with

aticonfig --adapters=all --initial

It would also be good to tell people that older fglrx versions must be removed before installing new ones or the fglrx kernel modules will fail to build on kernel updates.

Sweetbix, thanks for your advice, i'll look into it and update the post and community docs.

Cheers!

---

### Post by EJeanmaire on 2009-10-05
> **humphreybc said:**
> 

```

cd /usr/share/ati/
sudo sh ./fglrx-installer.sh
cd ~
sudo rm -rf /etc/ati/
sudo apt-get remove -purge xorg-driver-fglrx fglrx-amdcccle

```



I think you mean:

```

sudo sh ./fglrx-uninstall.sh

```

---

### Post by humphreybc on 2009-10-05
> **EJeanmaire said:**
> I think you mean:

```

sudo sh ./fglrx-uninstall.sh

```

Oops! Cheers!

---

### Post by mudsnake on 2009-10-06
> **markbuntu said:**
> aticonfig --help 

will list crossfire configuration options
  
I have a question I have a list of commands which I can't seem to do anything with. If I put this command in [aticonfig --lsa] it returns both cards as [ * 0. 01:00.0 ATI Radeon HD 3870
  1. 02:00.0 ATI Radeon HD 3870] They are both single gpu cards. When I type [aticonfig --cf
aticonfig: option '--cf' requires an argument
aticonfig: parsing the command-line failed. ] then if I type
[aticonfig --cf on
No CrossFire chains defined]
How do I get these cards linked together and is [aticonfig --adapters=all --initial] for dual gpu cards? 
Thanks for the help
EDIT: I found the proper order of commands and crossfire now works. I had the order of commands wrong

---

### Post by humphreybc on 2009-10-06
> **mudsnake said:**
> I have a question I have a list of commands which I can't seem to do anything with. If I put this command in [aticonfig --lsa] it returns both cards as [ * 0. 01:00.0 ATI Radeon HD 3870
  1. 02:00.0 ATI Radeon HD 3870] They are both single gpu cards. When I type [aticonfig --cf
aticonfig: option '--cf' requires an argument
aticonfig: parsing the command-line failed. ] then if I type
[aticonfig --cf on
No CrossFire chains defined]
How do I get these cards linked together and is [aticonfig --adapters=all --initial] for dual gpu cards? 
Thanks for the help
EDIT: I found the proper order of commands and crossfire now works. I had the order of commands wrong

Hi, i'm sorry I can't help you with crossfire and ATI drivers as I use a laptop so have never had dual GPUs. 

I'm sure someone else will be able to help though :)

---

### Post by harishgayatri on 2009-10-08
Are you able to Play HD Videos.

---

### Post by humphreybc on 2009-10-08
> **harishgayatri said:**
> Are you able to Play HD Videos.

Yep, I can play HD videos quite fine using the free drivers and VLC player.

---

### Post by orangemoose on 2009-11-29
Excellent! I successfully upgraded ATI drivers using your tutorial.
Thanks for the clear, concise tutorial.
+orangemoose

---

### Post by mkaut on 2009-11-29
Nice guide, thanks.

I didn't know that the open-source drivers provide some acceleration as well - though it does not seem to be enough for Compiz, i.e. I cannot enable Compiz with the open-source driver - or is there some way?

Can anyone confirm whether the Xfce compositor in Xubuntu can be used with the open-source drivers?

Thanks
Michal

---

### Post by humphreybc on 2009-11-29
> **orangemoose said:**
> Excellent! I successfully upgraded ATI drivers using your tutorial.
Thanks for the clear, concise tutorial.
+orangemoose

Hey no problem, pleased it worked for you. If you want to read more stuff then you can check out my blog, I post daily interesting articles, including quite a lot of Ubuntu stuff.

[http://humphreybc.wordpress.com](http://humphreybc.wordpress.com)

@mkaut

Yes open source drivers can enable 3D for certain cards. You can check if your card has 3D support [here.]("https://help.ubuntu.com/community/RadeonDriver")

Just a note, the R600/R700 based cards have 3D support using the experimental radeon driver and a newer kernel. If you've got one of these cards then I can try to run you through the setup.

I'm not sure about Xubuntu but I would assume that it works for me on Ubuntu so it should for you on Xubuntu.

Cheers

---

### Post by mkaut on 2009-12-01
> **humphreybc said:**
> 
Just a note, the R600/R700 based cards have 3D support using the experimental radeon driver and a newer kernel. If you've got one of these cards then I can try to run you through the setup.


I have a HD 3650 card, ie. R600. "Experimental driver and a newer kernel" sounds scary .. could you just give me a link, so I can follow the development and maybe try at some later point?

By the way, the reason I want to use the open-source driver is that I run into some problems with two-monitor setup with Catalyst drivers - as I described here: [http://ubuntuforums.org/showthread.php?t=1341050](http://ubuntuforums.org/showthread.php?t=1341050).
Do you know whether there is a way to achieve what I write about there using the Catalyst drivers?

Thanks.

Michal

---

### Post by thecliff on 2010-02-06
This worked perfectly!  My problem was being unable to tell which version of the driver was installed... followed document and rebooted PC.  viola!  I can know use my 24" monitor in 1920x1200.  :cool:

---

### Post by Bloemetjesgordijn on 2010-02-09
@ mudsnake

I have had Crossfire working once... I followed the following instructions. Maybe these help.

[http://ubuntuforums.org/showthread.php?t=1028151&page=3](http://ubuntuforums.org/showthread.php?t=1028151&page=3)

---

### Post by lonerjoe on 2010-02-20
Kind of a noob question here. I have Ubuntu 9.10 and an ATI HD 3650. I installed the Catalyst driver and had issues getting into the administrative settings mode. I found the fix for that (on this forum I believe. Thanks). I thought everything was OK til I tried to log out and ended up in a black screen. Long story short it was going to black screens on startup randomly and on logout always. I found another post regarding this issue to switch from "fglrx" to "ati" in my xorg.conf. This fixed the bootup/logout issue but I had no 3D. Sometime after that I installed Kubuntu on top of Ubuntu and switched from GDM to KDM and that fixed the bootup/logout issue. I switched back to GDM to verify the issue and black screen again. Now I'm totally lost and not sure what to troubleshoot. Sorry for the long post and please excuse my ignorance. Any help would be appreciated.

---

### Post by Chaos Punk on 2010-03-29
Dude, you're a beast, it worked, I now can use my graphics card to the fullest!

---

### Post by charlesp on 2010-04-21
I'm a complete noob at Ubuntu. I have an ATI Mobility Radeon 9000 IGP graphics card in my Toshiba Satellite a75. I looked in the syn. pack. manager and see that by default the open source drivers for ati and radeon were installed (I forget the actual nomenclature). My graphics on this computer suck! I have to use the lowest settings even in the display options and most of the games wont even load due to no graphics card. I have tried a couple of times now to update the driver and I am screwing it up somewhere! (had to do a new clean install yesterday due to failure to boot up) My questions are this:
1) how do I back up my files so that if I try out this install and it does not work, I can recover/restore to previous settings?
2) how can I tell which driver option would be best for me? 
3) your thread was pretty clear except for the part where you said "Change the ownership of the installer downloaded from ATI and run the installer. This presumes you downloaded to your HOME directory. Please remember to change the filename depending on driver version." What the heck does that mean?
 Sorry if this is a long post, I am completely new to this and need things broken down to a barney level for most applications. Any help would be greatly appreciated.

---

### Post by Yellow Pasque on 2010-04-21
@charlesp: Your card is too old to use the proprietary drivers. Your only option (besides the generic, unaccelerated vesa driver) is already installed.

---

### Post by charlesp on 2010-04-21
Crap! I was worried about that. What recommendation would you have about a replacement graphics card that is compatible with Ubuntu? Thanks for the response too, I appreciate it!.

---

### Post by Belegose on 2010-05-03
Greetings,

This is my first post on these forums.  I am a newbie to Linux, and I just installed Ubuntu 10.04 on an old laptop (Sony Vaio Z1RA, 14.1" SXGA +TFT with                            ATI Technologies Inc Radeon Mobility M6 LY).  I know essentially nothing about hardware.  No, I mean it, nothing.

After I installed the OS, I noticed that some of my applications were not working (e.g. Thunderbird).  The display was weird in that it would open a window that I was supposed to use to enter settings and so on, but in the widow would be a slice of my desktop background pic instead of text boxes and such.

It seemed like it was more of a display issue, so I decided to change my display settings.  I cut them down from 1400x1050 to 1280x960, and this fixed the display problem with my applications.  But, whenever I booted the computer, the screen would be fractured in a weird way with bits of it assembled like a jig saw puzzle put together wrongly.  If I re-booted several times, eventually it would display properly.

So I thought maybe my driver for my video card was corrupted.  I came to this page and installed the fglrx driver with your method 3 (Synaptic Package Manager, which I had never seen before and still do not understand), and now it works beautifully.

Thanks for posting this!!

---

### Post by xzero1 on 2010-05-04
> **humphreybc said:**
> Hey no problem, pleased it worked for you. If you want to read more stuff then you can check out my blog, I post daily interesting articles, including quite a lot of Ubuntu stuff.

[http://humphreybc.wordpress.com](http://humphreybc.wordpress.com)

@mkaut

Yes open source drivers can enable 3D for certain cards. You can check if your card has 3D support [here.]("https://help.ubuntu.com/community/RadeonDriver")

Just a note, the R600/R700 based cards have 3D support using the experimental radeon driver and a newer kernel. If you've got one of these cards then I can try to run you through the setup.

I'm not sure about Xubuntu but I would assume that it works for me on Ubuntu so it should for you on Xubuntu.

Cheers

Since Ubuntu docs have a tendency to go out of date, I thought I might add a link concerning feature support:

[http://wiki.x.org/wiki/RadeonFeature]("http://wiki.x.org/wiki/RadeonFeature")

Excellent 'howto' by the way.

---

### Post by privateabstract on 2010-05-05
This guide is absolutely brilliant. Thank you so much for writing it.

The section I found most useful was the little snippet, **sudo aticonfig --initial -f**.

Thanks a lot. :D

---

### Post by sjhupp on 2010-05-23
Sorry to dig this up, but did interest me a lot, and as a noob with ATI in ubuntu, I had a question.
If I can find a 3870 to use in my linux box, will I be able to get some reasonable 3D acceleration out of it?
Any better than a crappy nvidia G210/9400GT level card?
Thanks.

---

### Post by ridz on 2010-05-25
Hi  humphreybc

I read your guide with great interest as I am at my wits end trying to get the 'fglrx' driver working on my Lucid or Karmic PC. I have an ATI HD 4670 Radeon video card and no matter what I do I simply cannot get this to work properly in Lucid or Karmic.

As noted in your guide (I quote "PLEASE NOTE: If you install the open source drivers, you do NOT need these drivers installed.") does this mean I have to remove the "xserver-xorg-video-ati" or "xserver-xorg-video-radeon" driver before I install the xorg-driver-fglrx and the fglrx-amdcccle? FYI, I tried activating the restricted hardware driver (via System > Administration) but that did not work - I got the Black Screen Of Death (BSOD by God!) instead. I have not tried installing the fglrx driver via Synaptic but this is basically the same as activating the restricted hardware driver.

Hope you can answer me on this issue and any suggestions would be much appreciated.

---

### Post by Mark Phelps on 2010-05-25
While I certainly applaud anyone taking the initiative to put together a How-to-guide, with this one, I think you need to add strong emphasis near the beginning regarding the "legacy" ATI cards/chips for which the fglrx drivers will NOT work. 

Not everyone knows it has to be a R6x card or newer, and folks with the older cards will see this, try to force a driver installation, and corrupt their displays in the process.

Other than that, well done.

---

### Post by ridz on 2010-05-27
> **ridz said:**
> Hi  humphreybc

I read your guide with great interest as I am at my wits end trying to get the 'fglrx' driver working on my Lucid or Karmic PC. I have an ATI HD 4670 Radeon video card and no matter what I do I simply cannot get this to work properly in Lucid or Karmic.

As noted in your guide (I quote "PLEASE NOTE: If you install the open source drivers, you do NOT need these drivers installed.") does this mean I have to remove the "xserver-xorg-video-ati" or "xserver-xorg-video-radeon" driver before I install the xorg-driver-fglrx and the fglrx-amdcccle? FYI, I tried activating the restricted hardware driver (via System > Administration) but that did not work - I got the Black Screen Of Death (BSOD by God!) instead. I have not tried installing the fglrx driver via Synaptic but this is basically the same as activating the restricted hardware driver.

Hope you can answer me on this issue and any suggestions would be much appreciated.

I rarely reply to my own posting but this time I could not resist it :)

As per my original post to humpreybc (quoted above) I had problem getting the restricted 'fglrx' driver to work on my ATI HD 4670 video card. After that post I decided to try other versions of Ubuntu on my PC to see whether they will work with the restricted 'fglrx' driver supplied with each version. Before I proceed to describe my adventures, allow me to describe my PC. It's not a latest generation PC but it has served me well over the years and has been very reliable in running Linux, BSD, OpenSolaris, Windows (XP, Vista and 7) OS'es. It is self-made and is based on an Asus M2NPV-VM motherboard with an AMD Athlon X2 5200+ CPU and 8 GB (4 x 2G sticks) of DDR2-800 RAM. Since I like to play around with various OS'es, I use a removable HDD dock (or tray) and I simply switch HD to change OS. The current video card is a PCI-E ATI HD 4670 and this works perfectly on accelerated 3D mode with Windows - playing games of course.

When Valve announced that they will be porting some of their game titles to Mac and Linux, I got excited and decided to configure my Ubuntu Linux (Karmic and of course, Lucid) to use accelerated 3D as required by some OpenGL games that I already possess - like Doom 3 and Quake 4 (both of which had Linux versions). This is where I got stuck - no matter what I do and after searching the web for guides and following them, all I got was the Black Screen Of Death. This was characterized by the PC freezing with a black screen upon startup and was unresponsive to any key press. The only was I could recover was by pressing the reset key, and then via the Grub recovery mode and a root console, deleted the /etc/X11/xorg.conf file (after making a backup copy) - after which the PC was able to boot up normally. Note that this happens for both Karmic and Lucid - both 32 and 64 bit versions and for the restricted 'fglrx' driver as well as the latest proprietary binary drive supplied by ATI (version 10.4).

I then decided to try getting the video card to work in accelerated 3D mode using the older versions of Ubuntu. Sad to say, the same thing happened to Jaunty, Interpid, Hardy and Gutsy - all BSOD'ed. To say the least, I was extremely disappointed.

A friend of mine (who watched my experiments with amusement) suggested using an Nvidia video card in place of the ATI and was willing to loan me a 9800GT card for testing. I accepted and after swapping out my ATI card with the Nvidia card I started up Ubuntu Karmic 32-bit (which already had all traces of fglrx drivers - open and proprietary - removed). It booted up normally and using System -> Administration -> Hardware Drivers, installed the restricted nvidia driver for the video card. I then rebooted the PC watched it go through the boot process with bated breath! Lo and behold! It booted up normally (no BSOD by God!) and I was able to check via 'glxinfo' that the driver was actually being used. I then installed the Doom3 and Quake4 games - both WORKED!! Upon testing with the 64-bit Karmic, I discovered the same thing - normal bootup and fully working 3D games.

The experiment I carried out so far gave me food for thought. Clearly there is something wrong with the supplied ATI drivers (both open and proprietary) - they simply will NOT work with the HD 4670 card (which BTW is RV700 based) and a fully-up-to-date Karmic. If anybody out there has been successful in getting this combo working, I would like to know how they got it to work.

BTW, I will carry out more experiments with the nvidia card - this time with Lucid as well as older versions of Ubuntu. I will keep you all informed if it is of interest.

---

### Post by jsaumer on 2010-05-28
I followed the guide, but I can't seem to get mine to work.

I have Ubuntu 10.04, and a Radeon x800 series card hooked up with the DVI.

When I try and do a aticonfig, I get this:
```
aticonfig: No supported adapters detected
```

Here is my output from lspci -nn | grep VGA
```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) [1002:554d]
```

Any ideas on how to get these drivers properly installed on my system?

Thanks,
jsaumer

---

### Post by amdemas on 2010-05-28
Would this fix issues with Mobility Radeon x1600? or am I stuck

---

### Post by raudue on 2010-05-28
I followed the guide too, comprehensive as it was, I still fail to get fglrx working at all, either from the repos or ATI.

One thing I noticed was that the packages built from the ATI installer (Cat10.4/5 on 10.04 Lucid) include:
fglrx
fglrx_dev
amdccle
fgrx_modaliasses

There's no *xorg-driver-fglrx* or *fglrx-kernel-source* as mentioned in examples for Jaunty.
Is this going to be part of the problem, do you think?
However, installing these from the repos doesn't seem to do much either.

---

### Post by Yellow Pasque on 2010-05-28
> **jsaumer said:**
> I have Ubuntu 10.04, and a Radeon x800..Any ideas on how to get these drivers properly installed on my system?
You won't. Your card is too old. Follow this to fix: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

> Would this fix issues with Mobility Radeon x1600?
No. That card is too old. Follow the link above if you tried to install Catalyst/fglrx drivers. If you want to use the latest open-source drivers, see: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by jsaumer on 2010-05-31
> **Temüjin said:**
> You won't. Your card is too old. Follow this to fix: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Thanks for the info, the issue seems to be an issue with how my monitor via DVI is being picked up, it is being seen as a 7" monitor and not a 19" monitor, I have started another thread for this already.

---

### Post by benjamimgois on 2010-06-09
I have follow this guide step-by-step on a fresh ubuntu lucid installation but fglrx still does not work with my mobility radeon 4550. After installing fglrx with Jockey or the version downloaded from ATI/AMD site the screen just goes black after the reboot. I already tried Catalyst 10.3 , 10.4 and 10.5 but all of then give me the same result, black screen. The strange thing is that Mobility 4550 is listed as supported by this driver.

lspci -nn | grep VGA

[PHP]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series] [1002:9555][/PHP]


I check the X.org log and it seens that it has an invalid ATI BIOS. Please anyone has any idea of what is happening ?

/var/log/Xorg.1.log

[PHP](II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
	Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:58
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9555) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x1a855e0
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4500 Series " (Chipset = 0x9555)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x1409)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xe8400000
(--) fglrx(0): I/O port at 0x00006000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Bad V_BIOS checksum
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): Invalid ATI BIOS from int10, the adapter is not VGA-enabled
(EE) fglrx(0): Invalid video BIOS signature!
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitAdatper failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "fglrxdrm"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(II) UnloadModule: "fglrxdrm"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/PHP]

---

### Post by xzero1 on 2010-06-10
> **ridz said:**
> I rarely reply to my own posting but this time I could not resist it :)

As per my original post to humpreybc (quoted above) I had problem getting the restricted 'fglrx' driver to work on my ATI HD 4670 video card. After that post I decided to try other versions of Ubuntu on my PC to see whether they will work with the restricted 'fglrx' driver supplied with each version. Before I proceed to describe my adventures, allow me to describe my PC. It's not a latest generation PC but it has served me well over the years and has been very reliable in running Linux, BSD, OpenSolaris, Windows (XP, Vista and 7) OS'es. It is self-made and is based on an Asus M2NPV-VM motherboard with an AMD Athlon X2 5200+ CPU and 8 GB (4 x 2G sticks) of DDR2-800 RAM. Since I like to play around with various OS'es, I use a removable HDD dock (or tray) and I simply switch HD to change OS. The current video card is a PCI-E ATI HD 4670 and this works perfectly on accelerated 3D mode with Windows - playing games of course.

When Valve announced that they will be porting some of their game titles to Mac and Linux, I got excited and decided to configure my Ubuntu Linux (Karmic and of course, Lucid) to use accelerated 3D as required by some OpenGL games that I already possess - like Doom 3 and Quake 4 (both of which had Linux versions). This is where I got stuck - no matter what I do and after searching the web for guides and following them, all I got was the Black Screen Of Death. This was characterized by the PC freezing with a black screen upon startup and was unresponsive to any key press. The only was I could recover was by pressing the reset key, and then via the Grub recovery mode and a root console, deleted the /etc/X11/xorg.conf file (after making a backup copy) - after which the PC was able to boot up normally. Note that this happens for both Karmic and Lucid - both 32 and 64 bit versions and for the restricted 'fglrx' driver as well as the latest proprietary binary drive supplied by ATI (version 10.4).

I then decided to try getting the video card to work in accelerated 3D mode using the older versions of Ubuntu. Sad to say, the same thing happened to Jaunty, Interpid, Hardy and Gutsy - all BSOD'ed. To say the least, I was extremely disappointed.

A friend of mine (who watched my experiments with amusement) suggested using an Nvidia video card in place of the ATI and was willing to loan me a 9800GT card for testing. I accepted and after swapping out my ATI card with the Nvidia card I started up Ubuntu Karmic 32-bit (which already had all traces of fglrx drivers - open and proprietary - removed). It booted up normally and using System -> Administration -> Hardware Drivers, installed the restricted nvidia driver for the video card. I then rebooted the PC watched it go through the boot process with bated breath! Lo and behold! It booted up normally (no BSOD by God!) and I was able to check via 'glxinfo' that the driver was actually being used. I then installed the Doom3 and Quake4 games - both WORKED!! Upon testing with the 64-bit Karmic, I discovered the same thing - normal bootup and fully working 3D games.

The experiment I carried out so far gave me food for thought. Clearly there is something wrong with the supplied ATI drivers (both open and proprietary) - they simply will NOT work with the HD 4670 card (which BTW is RV700 based) and a fully-up-to-date Karmic. If anybody out there has been successful in getting this combo working, I would like to know how they got it to work.

BTW, I will carry out more experiments with the nvidia card - this time with Lucid as well as older versions of Ubuntu. I will keep you all informed if it is of interest.

I have an hd 4770 and it works well with Karmic and Lucid (AMD 64). In fact, video with the Lucid open driver is better than when using the hack posted here! For me its been as stable as any previous driver I have used. It is strange that it doesn't work for you. Perhaps a bios setting? It even works when booting from the Live cd.

---

### Post by benjamimgois on 2010-06-17
Using the hot Catalyst 10.6 my system is now able to boot with fglrx, but the compiz and 3d effects are disabled. Anyone ?

---

### Post by ridz on 2010-06-17
> **xzero1 said:**
> I have an hd 4770 and it works well with Karmic and Lucid (AMD 64). In fact, video with the Lucid open driver is better than when using the hack posted here! For me its been as stable as any previous driver I have used. It is strange that it doesn't work for you. Perhaps a bios setting? It even works when booting from the Live cd.

I think I have solved the problem - purely by chance. As mentioned in my post, I have an Asus M2NPV-VM motherboard which is quite ancient (computer hardware-wise that is) and it had developed a problem with the network on-board chip recently. So I decided to retire this motherboard and move all the components to an Asus M2N-E motherboard (where they all worked as they are supposed to be). On a hunch, I decided to try out the ATI 4670 card again with the 'new' motherboard and install Ubuntu Lucid. The install went fine and once it was working I installed the fglrx restricted driver. I was amazed to discover that the driver worked now!

This gave me more food for thought - was the problem caused by the M2NPV-VM motherboard? If it was, why did Windows worked on it and not Ubuntu Lucid? Was it the chipset? Note that the M2NPV-VM used a nForce 430 MCP while the M2N-E used a nForce 570 MCP. I am still wondering at this moment. Anyways, the ATI 4670 works  now with the fglrx accelerated 3D driver and that all I need.

---

### Post by Browser_ice on 2010-07-29
What do I install for my Lenovo T400 laptop with Lucid ?  Haven't installed hardware proprietary yet (installed Lucid yesterday).

> lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3400 Series [1002:95c4]


> lspci -v
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
	Subsystem: Lenovo Device 210e
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 2000 [size=256]
	Memory at cfff0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at cff00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

> glxinfo (had to install glxinfo as it was non-existent)
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV620 95C4) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:
    GL_EXT_compiled_vertex_array, GL_EXT_texture_env_add, 
    GL_ARB_depth_texture, GL_ARB_depth_clamp, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_provoking_vertex, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_MESAX_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

64 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc3 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc4 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc5 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc6 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc7 24 tc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xc8 24 tc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xc9 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xca 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xcb 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xcc 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xcd 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xce 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xcf 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd0 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd1 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd2 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd3 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd4 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd5 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd6 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd7 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xd8 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xd9 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xda 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xdb 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xdc 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xdd 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xde 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xdf 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xe0 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xe1 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe2 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe3 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe4 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe5 24 dc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xe6 24 dc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xe7 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xe8 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xe9 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xea 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xeb 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xec 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xed 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xee 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xef 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xf0 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xf1 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf2 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf3 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf4 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf5 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xf6 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xf7 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xf8 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xf9 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xfa 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xfb 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xfc 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xfd 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xfe 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xff 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x62 32 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None

96 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x63  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x64  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x65  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x66  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x67  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x68  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x69  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x6a  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x6b  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x6c  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x6d  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x6e  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x6f  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x70  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x71  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x72  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x73  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x74  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x75  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x76  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x77  0 tc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x78  0 tc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x79  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x7a  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x7b  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x7c  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x7d  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x7e  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x7f  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x80  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x81  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x82  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x83  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x84  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x85  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x86  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x87  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x88  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x89  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x8a  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x8b  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x90  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x91  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x92  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x93  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x94  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x95  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x96  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x97  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x98  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x99  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x9a  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x9b  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x9c  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x9d  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x9e  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x9f  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xa0  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xa1  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xa2  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xa3  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa4  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa5  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa6  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa7  0 dc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xa8  0 dc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xa9  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xaa  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xab  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xac  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xad  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xae  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xaf  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb0  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb1  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb2  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb3  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb4  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb5  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb6  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb7  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xb8  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xb9  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xba  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xbb  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbc  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbd  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbe  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbf  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc0  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xc1  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc2  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

---

### Post by Yellow Pasque on 2010-07-29
@Browser_ice:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

### Post by Browser_ice on 2010-07-29
> **Temüjin said:**
> @Browser_ice:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Installing Proprietary Drivers a.k.a. Catalyst/fglrx
=> says which card wont work with it but does not say which ones are recommended to use it

Restricted Drivers Manager
=> does not say which card is recommended for this one (or not)

Ubuntu X Team's PPA 
=> does not say which card is recommended for this one (or not)

Download the latest Catalyst package.
=> saw on AMD site the 10.7 would seam to work for me


None of them say which one I SHOULD install. It simply list all the possible drivers ANYONE can install. I do not want to spend 2 days on a trial-and-error base.  

The only bit of information that is clear in those kind of wikis is when they say which cards are discontinued. Those wikis do not say "for this series of card, install this driver".  Why can't wiki people do it this way so people would stop wasting time ?

---

### Post by Yellow Pasque on 2010-07-29
> Why can't wiki people do it this way so people would stop wasting time ?
Maybe there's more than one way to do it and the "wiki people" don't want to make assumptions as to what will work for you and your specific hardware.
What do you do with your GPU? Watch HD video, play any games?

I'm guessing you'll either end up installing the proprietary driver or you'll end up installing a 2.6.35 kernel if you want to keep your GPU cooler and extend battery life.

> I do not want to spend 2 days on a trial-and-error base. 
Then get a Mac, where hardware choices are expensive/limited and certified to work with a specific OS and specific driver.

---

### Post by Browser_ice on 2010-07-29
> **Temüjin said:**
> I'm guessing you'll either end up installing the proprietary driver or you'll end up installing a 2.6.35 kernel if you want to keep your GPU cooler and extend battery life.

I installed the proprietary driver (on laptop HD) and upon booting I winded up into a black screen. Did not even get to the logon screen. Now I have to undo this mess. Typing from my ubuntu USB key on that same T400 laptop.  This is what I meant by loosing time and trial and error.

While on my USB key, I set a filesystem pointing to my hd. This is what the xorg.conf looks like on it:
> cat xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection


So to fix this, is it simply a matter of changing that xorg.conf or remove the proprietary driver ^

---

