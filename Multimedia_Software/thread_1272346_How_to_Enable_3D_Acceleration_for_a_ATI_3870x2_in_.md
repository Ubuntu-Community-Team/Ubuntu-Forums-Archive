---
title: "How to Enable 3D Acceleration for a ATI 3870x2 in Jaunty"
date: 2009-09-22
forum: Multimedia Software
---

### Post by asyed94 on 2009-09-22
After searching countless hours on the internet and combing through pages and pages of Google search results, and so many reinstalls of Jaunty that I have lost count, I have found a way to enable 3d acceleration on the Radeon HD 3870x2 in Jaunty. Here is a guide I have compiled on how to accomplish the above task.

**Diclaimer:** Thanks to the efforts of those who confirmed this guide, I can safely say that it will most probably work on most systems, but still I cannot guarantee that this guide will work on *every* system.

**Before you begin:** Remember to [COLOR=Red]backup all important data[/COLOR] on your computer [COLOR=Red]externally[/COLOR] (ex: an external hard drive, an external flash drive, etc...). I cannot stress this enough. More than once, I have installed glitchy graphics drivers only to find a black and/or garbled screen on restart which doesn't respond to any key combos except Ctrl+Alt+R, S, E, I, N, U, B (the restart combo). So play it safe and back up your data.

Without further ado, the guide:

-The ATI Radeon HD 3870x2 is not supported officially by the fglrx proprietary ATI Linux Driver. This is because it uses some sort of on-board CrossFire technology which is unsupported by fglrx, to put 2 3870 gpu's into one unit. ([http://www.phoronix.com/forums/showthread.php?t=10091&highlight=3870x2+ubuntu](http://www.phoronix.com/forums/showthread.php?t=10091&highlight=3870x2+ubuntu) : 5th post)

-To make this card work, we'll need to spoof Jaunty into using only one of the two 3870's on the board. By doing this, we will inadvertently be cutting the boards performance in half. But hey, half of a graphics card working is better than all of a graphics card broken. ([http://www.phoronix.com/forums/showthread.php?t=9259&highlight=3870x2+linux](http://www.phoronix.com/forums/showthread.php?t=9259&highlight=3870x2+linux) : 4th post)

-To fool Jaunty, we'll need to hack the fglrx driver, then put a ChipID override into our xorg.conf to force Jaunty into using only one of the gpus of the 3870x2. ([http://www.phoronix.com/forums/showthread.php?t=9259&highlight=3870x2+linux](http://www.phoronix.com/forums/showthread.php?t=9259&highlight=3870x2+linux) : 8th post)

**STEP 1)** Download the ATI Linux Driver version 9.7 from here:

[http://support.amd.com/us/gpudownload/linux/9-7/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/9-7/Pages/radeon_linux.aspx)

[B]
STEP 2)[/B] Install the necessary packages in the terminal:

```
$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms
```[I](*Note: This is step 2 of the Unofficial Fglrx Wiki's guide to install fglrx on Jaunty: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide*"))
[/I] 

**STEP 3)** Follow this guide outlining the hack posted by Kano on the Phoronix forums: [http://www.phoronix.com/forums/showthread.php?p=39830](http://www.phoronix.com/forums/showthread.php?p=39830).

I have pasted the guide here for simplicity:
> 
Extract the driver with:

```
$ sh ati-driver-installer-9-7-x86.x86_64.run --extract 9-7
```Patch it:

```
$ cd 9-7
$ echo " FGL_ASIC_ID(0x950F)," >> common/lib/modules/fglrx/build_mod/fglrxko_pci_ids.h
```Create packages:

```
$ ./ati-installer.sh x --buildpkg Ubuntu/jaunty
```Install packages:

```
$ sudo dpkg -i ../*.deb
```IMPORTANT: Use your version of Ubuntu in place of "jaunty"

instead of:

```
./ati-installer.sh x --buildpkg Ubuntu/jaunty
```use this:

```
./ati-installer.sh x --buildpkg Ubuntu/hardy
```for computers running Ubuntu Hardy. Or this:

```
./ati-installer.sh x --buildpkg Ubuntu/karmic
```for computers running Ubuntu Karmic.[B]


STEP 4) [/B]After installing the generated .deb packages, you can update your xorg.conf file either automatically or manually.

      **Automatically:**

Follow these instructions by NeKit1000:

> **NeKit1000 said:**
> Extract fglrx 8.10:

 ```
$ sh ati-driver-installer-8-10-x86.x86_64.run --extract 8-10 
```Overwrite /etc/ati/control with 8-10/common/etc/ati/control:
```
$ sudo cp 8-10/common/etc/ati/control /etc/ati/control 
``` Fglrx now will think that 3870x2 is supported, aticonfig and others tool also will work.


Then, type the following into a terminal to auto-configure your xorg.conf:

```
$ sudo aticonfig --initial -f --adapter=all
```[B]
      Manually:

[/B]After installing the generated .deb packages, to update your xorg.conf manually, type this in the terminal:

```
$ sudo gedit /etc/X11/xorg.conf
```In xorg.conf, find the the part that looks like this:

*(*Note: Doing this step may break your xorg.conf, so [COLOR=Red]back it up[/COLOR] before proceeding.*)*

[I](*Note: Your xorg.conf may look different based on your system configuration.*)
[/I] 
```
Section "Device"
          Identifier         "Configured Video Device"
          ...
EndSection
```edit it to look like this, and then save it.

```
Section "Device"
          Identifier         "Configured Video Device"
          Driver                 "fglrx"
          ChipID          0x9501
EndSection
```[B]


STEP 5) [/B]Now go to System>Administration>Hardware Drivers and enable fglrx. This is important.
[B]

STEP 6)[/B] Finally restart your computer, and you should see a "AMD Unsupported Hardware" watermark at the bottom right part of your screen. This is an indicator that the hack has worked and you now have 3d acceleration. If the hack did not work, than try the Ctrl-Alt-R, S, E, I, N, U, B combination to force restart your computer.

This is my first guide, so please gently correct any mistakes I might have made while compiling it, thank you.

[COLOR=Red][B][I]UPDATE: Instructions for removing the AMD Unsupported Hardware watermark are in post #7, thanks to NeKit1000.

UPDATE: Instucrions on how to auto-configure xorg.conf are in post #15 thanks to dany74q
[/I][/B][/COLOR]

---

### Post by NeKit1000 on 2009-09-25
Thanks, but still can't get it to work. I tried 9.4 and 9.5, because haven't never versions. Now trying to download 9.7.
Kubuntu 9.04 Jaunty x64. [Here]("http://www.binpaste.com/v.php?id=u0cwe") is Xorg.0.log.

---

### Post by asyed94 on 2009-09-25
Thanks for you comment. As for your problem,

the link in STEP 2) provides additional steps for installing on 64 bit systems.

To follow them, do my guide up till STEP 3). After creating the .debs, go to the link in STEP 2) and in that guide follow steps 4 and 5 for 64 bit OS's.

Once you do the additional 64-bit instructions, come back to my guide and continue on from STEP 4).

Hope that helps.

---

### Post by NeKit1000 on 2009-09-26
Thanks for the guide! All I needed was to download 9.7. As for additional 64-bit steps, I have ia-32 libs already installed.
Also, used /etc/control file from fglrx 8.10 to get rid of "AMD Unsupported Hardware" logo.

---

### Post by nukaway on 2009-09-27
i try to install the new 9.9 catalyst drivers with my hd3870x2 and its tuto and it didn work.

---

### Post by asyed94 on 2009-09-28
nukaway: hmm... maybe this hack only works with fglrx 9.7
 
NeKit1000: Im glad I could help :). How specifically did you rid yourself of the "AMD Unsupported Hardware" logo? It'd be a great addition to this guide.

---

### Post by NeKit1000 on 2009-09-28
> **asyed94 said:**
> nukaway: hmm... maybe this hack only works with fglrx 9.7
 
NeKit1000: Im glad I could help :). How specifically did you rid yourself of the "AMD Unsupported Hardware" logo? It'd be a great addition to this guide.
Extract fglrx 8.10:

 ```
$ sh ati-driver-installer-8-10-x86.x86_64.run --extract 8-10 
```
Overwrite /etc/ati/control with 8-10/common/etc/ati/control:
     ```
$ sudo cp 8-10/common/etc/ati/control /etc/ati/control 
```
 Fglrx now will think that 3870x2 is supported, aticonfig and others tool also will work.
I can't remember where I've read about this, but it works.
Also, maybe another old fglrx package will suit.

---

### Post by Lodamned on 2009-10-16
Hello:)
I can confirm that this works.

i followed the steps in post1 using the 9.7 driver:)

Bump this:) i know there are many people out there that realy want support for the hd3870x2 card:( 

according to the post by that amd guy in one of the forum links you provided they say that fglrx driver doesnt support crossfire..
well take a look at the latest catalyst suite, read and it supports the 4xxx x2 series;) 
is there that bigof a diffrence ?

this should be looked into..

---

### Post by snoopo71 on 2009-10-16
Confirmed, it works great!!!

---

### Post by kv1dr on 2009-11-07
Drivers version 9.9 don't work with this ATI graphic card.

---

### Post by morris4 on 2009-11-12
hi,

has anybody tried this on karmic (9.10)? i tried both the 9.7 and 9.10 ati drivers, but it seems X could not be properly started. i get a terminal prompting for user/password and the screen is flickering, and input is pretty hard.

additionally, i wonder why the patch is required - both 950F and 9501 are already in the header files for 9.7 and 9.10. and, why is the ChipID 9501 different to the suggested patch (950F)? is there any reason for this?

are there any log files i can check as to find out why X could not be started?

**update:**
i removed all fglrx packages and removed the /etc/ati directory completely. then, i installed the driver via the restricted hardware manager. i did not have to patch anything nor change the xorg.conf, and it works. i still have the watermark, though. remember that this is on karmic, not on jaunty.

---

### Post by klutti on 2009-11-13
Hi morris4,

I tried this also on Karmic (9.10) but I'm stuck right now with the blinking cursor. It blinks so fast, that I'm unable to enter my password correctly, because I don't know if I entered anything when pressing the key before. :(

So I booted in recovery mode from Grub2 -> netroot and uninstalled the packages using

apt-get remove fglrx*
dpkg-reconfigure xserver-xorg

I also removed the /etc/ati folder completely as you did afterwards, but still I get the blinking cursor after reboot. 

What did you mean by "installed the driver via the restricted hardware manager". What did you do exactley?

Thank you so much for your help!

---

### Post by asyed94 on 2009-11-26
Thanks to everyone who tested this hack with versions greater than 9.7, and confirmed that they do not work. Ill update my original post to include that.

@morris4, Could you please post the exact instructions for getting this to work on Karmic? I'm sure it would help tons of users who have made the switch. Regarding the patch, I too am not really sure why the patch is required. I just happened to find pieces of the solution to our driver problem scattered about the internet, and after many attempts in trying to put them together, compiled them all into this guide.

We must all remeber though, that this is only a hack. It seems that I have stumbled upon a delicate balance of version numbers, which may come crashing down if some subtle, unknown dependency was to change. As always, Im still anticipating the release of a permanent solution.

---

### Post by zoso on 2009-11-29
These steps worked for me on a fresh install of Kubuntu 9.10, including getting rid of the 'unsupported hardware' overlay. I'm running two ATI Radeon 3870x2 cards in crossfire mode. To make matters more complicated I've got two LCD monitors hooked up to the whole thing.

Once I got the settings for xorg.conf figured out everything went smoothly.

```
Section "Device"
	Identifier "Radeon1"
	Driver "fglrx"
	BusID "PCI:4:0:0"
	ChipID 0x9501
	Screen 0
EndSection


Section "monitor"
	Identifier "DFP1"
EndSection

Section "Monitor"
	Identifier "DFP2"
	Option "RightOf" "DFP1"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "DFP1"
	Device "Radeon1"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Virtual 3360 1050
	EndSubSection
EndSection
```

---

### Post by dany74q on 2009-12-04
This tutorial works on any ubuntu distro that I tried.
But to make things much less complicated,instead of configuring xorg.conf manually,
I just did what netkit1000 said,and than just did 
$ sudo aticonfig --initial -f --adapter=all
and ati software will configure xorg.conf automatically and accurate.
Thank you for this great tutorial!
Currently I`m working with 9.11 and Karmic.

---

