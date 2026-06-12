---
title: "ATI Driver Problem x1950 AGP"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by oVIXx on 2008-01-29
Does anyone know how, or had any success on installing the latest ATI proprietary drivers with this agp card on Debian etch or Ubuntu gutsy? For a week I've been trying to get this card to have 3D acceleration but to no avail. So far nothing on Debian etch 4.0r2, Ubuntu gutsy, Slackware current, or Fedora 8, Mandriva 2008, Linux Mint, Mepis, and Gentoo all of which were fresh installs/updates Except Mandriva and Gentoo, those both crashed and faile dto load up the "Live" cd's.. So I'm back to a fresh install of Ubuntu, Roughly the process I've followed for Debian are..

Download the installer, currently "ati-driver-installer-8-01-x86.x86_64.run"
cd to the download directory

# apt-get install module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base linux-headers-$(uname -r) gcc autoconf automake1.9 libtool flex bison cvs

# chmod +x ati-driver-installer-8-01-x86.x86_64.run

# ./ati-driver-installer-8-01-x86.x86_64.run --buildpkg Debian/etch

# dpkg -i *.deb

# cd /usr/src

# m-a build fglrx

# m-a install fglrx (also tried it in one command #m-a a-i fglrx)

#aticonfig --initial

I've tried a few variations of that list of commands which include adding symlinks and not using module assistant but compiling and moving the fglrx.ko manually. Some guides I've tried..

[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)
[http://technowizah.com/2006/10/debia...i-drivers.html](http://technowizah.com/2006/10/debia...i-drivers.html)
[http://wiki.cchtml.com/index.php/Deb...allation_Guide](http://wiki.cchtml.com/index.php/Deb...allation_Guide)
[http://linuxized.blogspot.com/2007/0...gl-compiz.html](http://linuxized.blogspot.com/2007/0...gl-compiz.html)

I gave Envy a go with the same results. That was the only method I tried that had errors, but those were md5 mismatch errors when downloading the ati installer. So far no matter what install method I try, when I type "fglrxinfo" I get..

display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

This is an entry from the xorg.0.log

(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed! *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available *
(WW) fglrx(0): ********************************************* *

My relevant entries in the xorg.conf are..

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
BusID "PCI:1:0:0"
Option "DynamicClocks" "true"
Option "VBERestore" "true"
Option "backingstore" "true"
Option "RenderAccel" "true"
# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
#Option "NoDDC"
# === Video Overlay for the Xv extension ===
Option "VideoOverlay" "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
# will be disabled automatically
Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
Option "UseInternalAGPGART" "yes"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
HorizSync 30-97
VertRefresh 50-160
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
Load "GLcore"
# Load "extmod" but omit DGA extension
# (the DGA extension is broken in the fglrx driver)
SubSection "extmod"
Option "omit xfree86-dga"
EndSubSection
EndSection

Upon searching more I found a post here that boasts a solution..

[http://linuxmint.com/forum/viewtopic.php?t=6317](http://linuxmint.com/forum/viewtopic.php?t=6317)

However that solution does not work with Ubuntu gutsy or Debian etch. With gutsy I got the hard locked black screen, for both drivers, and Debian just defaults to mesa. I think Lolo Uila is on the right track of bypassing the recognition of the R570 chip as a PCIe bus.

Anyone have any ideas of how blacklisting fools Mint into recognizing the card correctly? Or how I can have the same effect on Debian, or Ubuntu?

THANKS in Advance

---

### Post by oVIXx on 2008-01-29
dam 2 hours an already bumped to the second page.

---

### Post by oVIXx on 2008-01-30
1 day and 6 pages into the pile.

---

### Post by JoePits on 2008-01-30
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by oVIXx on 2008-01-30
Yeah, I used that guide already, both on Debian and Ubuntu, Ubuntu hard locks, and Debian defaults to Mesa. Anything else than a link?

---

### Post by Yellow Pasque on 2008-01-30
Yeah, Catalyst isn't known for playing nice with AGP. You could try the radeonhd open-source driver, which just recently had 2D acceleration added to it for the X1k series. You won't get the eye candy effects or acceleration in games right now, but at least you should get a very lightweight and usable 2D config.

---

### Post by JoePits on 2008-01-30
fwiw i didnt want to settle for anything less than the 8.01 or 8.1 w/e it is on a fresh gutsy.   i messed up things, compiz wouldn't work anyways even with the n ew thing, so now im back on a fresh reinstall of gutsy and i dont even care about compiz this time because i went and had a cigarette instead.  :)

---

### Post by oVIXx on 2008-02-01
Thanks for the posts. As far as the 2D goes, all the distro's except Gentoo and Mandriva worked fine using Mesa/vesa. I was really going for the 3D acceleration, for a few different programs I need to run. Trying to recover 100GB of space that Microsoft still occupys on my HDD!

---

### Post by oVIXx on 2008-02-04
It's been  few weeks now, anyone?

---

### Post by Yellow Pasque on 2008-02-04
> **oVIXx said:**
> It's been  few weeks now, anyone?
Sorry, mate, but I think you're in the same boat as a lot of other people (i.e. waiting for next month's driver release).

---

### Post by oVIXx on 2008-02-18
Has anyone had any success with the newest release version 8.2?

---

### Post by Shadowmeph on 2008-02-18
your best bet is to do what I had to do and it took more over 20 reinstalls of Gutsy Gibbon to figure it out, during everything I state here don't do any multi tasking at all and I mean don't do anything it seems that the OS doesn't like Multi tasking while it is doing important things
1) do a fresh install
2) update 
3)download Envy
 ( I know I know but this is how I got it took work for me tested it 3 times in a row and once I figured it out it worked all three times also remember do give in to the temptation of downloading Envy during the update because this will screw up everything)
4) install envy and then use it to install the drivers , after the install **Do not turn on restricted drivers** first reboot
5) after reboot turn on restricted drivers and then reboot again.
now if everything is good and you didn't Multi task during any of the Above instructions you 3d stuff should be working . If it isn't working and when you type in fglrxinfo into the terminal and it shows the  Messa drivers then your best bet is to repeat the process but ans Like I stated I did over 20 reinstalls and during those 20 + reinstalls I sometimes Multi tasked which screwed up The install of the drivers the I wasted precious hours trying to reinstall but once I realized that you can't Multi task it went and I followed my instructions to the letter it works I did this three times in a row and every time it worked like a charm.
So good luck and be patient

---

### Post by oVIXx on 2008-02-19
Thanks for the post Shadowmeph. 

I had also tried Envy, I put a line in my original post about it but it didn't work for me either. Ubuntu gave me the hard lock, meaning theres no X desktop, no command line after an X desktop failure, just a black screen. The only thing I can do after that is choose the recovery mode and remove the references to "fglrx" from the xorg.conf.

Debian just defaults to mesa with Envy too. All the  operating systems I've tried are fresh installs with an attempt to install the ATI drver before and after available upgrades from their respective security repositories. Slackware aside.

I'm curious what graphics card are you using. It's been a few weeks now going on months, lots of people look at the post but so far no 3D.   ](*,)

---

### Post by oVIXx on 2008-02-23
Still Nothing?

---

### Post by miciurin on 2008-02-28
I have a X1650 and it gave only problems. I tried installing the latest driver from Ati. Used the manual way (building the ubuntu package from the ATI installler, and also Envy. Everytime I would end up with No 3D acceleration and it would default to mesa. I looked in the Xorg.0.log file and there it says in one place that the card has 256MB, when in fact is 512MB and then a few lines down, predictably, that it fails to remap AGP, bla bla, basically no AGP working. I then went in BIOS and changed the AGP aperture size to 256MB and it works. Its probably a bug in the driver configuration file. 

My advice is to check the Xorg.0.log and see if fgrlx reports a matching memory size with what your card actually has. Otherwise it will fail.

---

### Post by kellemes on 2008-03-07
> **miciurin said:**
> I have a X1650 and it gave only problems. I tried installing the latest driver from Ati. Used the manual way (building the ubuntu package from the ATI installler, and also Envy. Everytime I would end up with No 3D acceleration and it would default to mesa. I looked in the Xorg.0.log file and there it says in one place that the card has 256MB, when in fact is 512MB and then a few lines down, predictably, that it fails to remap AGP, bla bla, basically no AGP working. I then went in BIOS and changed the AGP aperture size to 256MB and it works. Its probably a bug in the driver configuration file. 

For some reason changing BIOS-settings don't work for me, tried this a million times.. In the end I'm forced to use [fglrx 8.42.3]("http://ati.amd.com/support/drivers/linux/previous/linux-r-8-42-3.html") and it works fine..
Still this pisses me off, for some reason the AGP-version of this card is too hard to grasp for the amateurs from AMD.

---

### Post by Johnny.P on 2008-03-08
I recently installed an x1650 which ubuntu did not like and gave me a black screen-as did debian,kubuntu,mandriva and fedora-alas xubuntu works fine with no issues at all- I do not know enough about ubuntu to know how this will affect 3d graphics but I am using the ati restricted driver loaded through the restricted drivers manager and it works for me.

---

### Post by Johnny.P on 2008-03-08
p.s its an agp version

---

### Post by chmavr on 2008-03-25
did anyone had any success with the new drivers 8.3???

---

### Post by thomasbaker on 2008-04-15
No luck with 8.3, if 8.4 ever gets here maybe it will be fixed then.  I'm not going to hold my breath.  I really wish this would get resolved.

---

### Post by JustinClift on 2008-04-26
Hi.  Similar situation.

I'm running a X1950 Pro 512MB (Sapphire), in my old AthlonXP 3000 system.

Now running the 8.4 driver release, but only in 2D only mode.  Enabling DRI hard locks my system. :(

The last driver that worked for me was the ATI "8.40.4" version.  Everything after then until this one wouldn't even let 2D work. :(

256MB AGP GART size setting in the driver plus matching that in the BIOS didn't help at all, etc.  The only thing seeming to work is turning off DRI.  Ugh.

Pretty safe bet there's not going to be anything with the label ATI in my next system.. :mad:

---

### Post by zimbo_ouen on 2008-04-26
god this is so annyoing :(

why if its been going on this long has no one at amd/ati done anything. I have a X1950 Pro 512MB AGP card and its one of the highest agp cards I think to have still...so more than likely people on AGP system will be using one of these.

They should try and fix it like now. This is the only reason why I keep giving up on Ubuntu. If they want people to use they should sort out the issues :/

---

### Post by JustinClift on 2008-04-26
Not sure what sort of CPU you are using, but if it's an intel then this might help:

  [http://linuxmint.com/forum/viewtopic.php?t=6317](http://linuxmint.com/forum/viewtopic.php?t=6317)

From this, the problem looks to be from the driver thinking the card is PCI Express rather than AGP.

The above forum post shows how to disable false PCI-E detection for his specific motherboard, then the card works for him.

For me however, my kernel is compiled without PCI Express support in it at all, yet somehow the driver still things it's PCI-Express and I have no idea how to tell it that it's not. :(

---

### Post by JustinClift on 2008-04-26
Just created a bug for this on the ATI "unofficial" bugzilla:

  [http://ati.cchtml.com/show_bug.cgi?id=1110](http://ati.cchtml.com/show_bug.cgi?id=1110)

If you have the time/inclination to register on there and "vote" for this bug, it will help get it attention.  (Most bugs just have the vote of the submitter for them, so look like it's only affecting 1 person)

Errr.. please assist. :)

---

### Post by JustinClift on 2008-05-03
Hmmm, none of you guys complaining of problems seems to have actually put info or votes on the ATI Bugzilla. :(

Guess you're not really having any problems after all then?

---

### Post by xMachina on 2008-05-13
Hi Justin, I added to your bug report over at ATI.

ATI seem to have put this card in the "too hard basket" as far as Linux drivers go which is pathetic, as mentioned already it's the best AGP card still out there so should be supported.

Ever after buying this card I now do _exhaustive_ research before purchase as to whether my selected HW is known good with Linux, sad but it's the only safe way to go.

---

### Post by xMachina on 2008-05-13
Update ... some guy called Alastair over at the ATI bugzilla has figured out how to get it going! By:

1) Follow the manual install option for the Proprietary ATI drivers at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually)

EXCEPT before rebooting, you also need to make sure the AGP memory listing matches up at 3 places, to avoid the "ATI black screen of death":

2) Look up exactly how much video RAM your card has, eg from the box, receipt, or the ATI control centre in windows (it will either be 256MB or 512MB). For the instructions below I'll go with 512, but substitute as appropriate.
3) edit your /etc/X11/xorg.conf, and add the following line at the end of the fglrx device section:
>  Option      "MaxGARTSize"       "512"
4) edit your grub boot instructions for your kernel in the /boot/grub/menu.lst file, adding vmem=512 to your kernel boot line for your main kernel, e.g.:  
> 
title           Ubuntu 8.04, kernel 2.6.24-16-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16-386 root=UUID=64fa7a1b-a8d7-45fb-a891-a81f3977bc13 ro quiet splash vmem=512
initrd          /boot/initrd.img-2.6.24-16-386

5) Ok, now reboot, but ENTER YOUR BIOS and look for the setting related to AGP memory, for me it was in the "Advanced Chipset Features" section. Change it to the same value as the others, eg 512MB.

...and that worked for me, ~1600 FPS in fg_glxgears ;) Haven't tried Compiz etc yet.

---

### Post by JustinClift on 2008-05-13
Hi xMachina,

Glad something works for you at least! Heh. :)

Not sure how to adapt this to my setup though.  The maximum AGP memory aperture size my bios allows to be set is 256MB, but the graphics card has 512MB ram.

i.e. theres no physical way of getting all the settings to match up. :(

Might try them all as 256MB later on and see what happens. ;->

---

