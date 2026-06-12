---
title: "X Server Crashes"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by sbjaved on 2006-07-27
Hi,
I'm a newbie to Linux and ubuntu is the second distro i've gathered up courage to try (First being RedHat 9.0)
Upon popping in ubuntu CD and selecting install, i encountered a "X Server Crash" message and a suggestion that i should reconfigure it. Frankly i don't have clue what "X Server" is (so much for reconfiguring it), but i didn't throw the CD out of the window...I gave it another shot. I tried to use the "Safe Graphics" mode which yielded a similar result. For the technically enlightened, here's what the screen told me (It seems gibberish to me though):

-------------------------------------------------------------------
Failed to start X Server

X Windows System 7.0.6
X Protocol Version 11

(WW) VESA: No Matching Device Section
(WW) ****INVALID MEM ALLOCATION**** b: 0x20000000 e: 0x27ffffff
correcting^G
(EE) VESA(0): cannot read V_BIOS
(EE) Screen(s) found, but none have a usable configuration
-------------------------------------------------------------------

Note: I have Windows XP SP2 on Primary C: Drive and my ATi card works perfectly with it, if ubuntu is suggesting something's wrong with my card.

MY SYSTEM:

Intel Pentium 4 1.8GHz
Intel D845GLVA
Kingston 512MB RAM
ATi Radeon 9200SE 128MB PCI version (Intel's integrated Video disabled)
Seagate HDD 80GB IDE
Liteon DVD-ROM

---

### Post by tseliot on 2006-07-27
Please follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vga" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by sbjaved on 2006-07-28
Thanks a bunch elliot...

But umm...

What do you mean by "alternate installation CD"? I only have a single CD in my possession which was sent by ubuntu guys...Should i try installing from some other CD?

Saad

---

### Post by tseliot on 2006-07-28
> **sbjaved said:**
> Thanks a bunch elliot...

But umm...

What do you mean by "alternate installation CD"? I only have a single CD in my possession which was sent by ubuntu guys...Should i try installing from some other CD?

Saad

You have the Desktop CD but you need the Alternate Install CD if you want to solve that problem:
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

---

### Post by sbjaved on 2006-07-28
> **tseliot said:**
> You have the Desktop CD but you need the Alternate Install CD if you want to solve that problem:
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)
Any other way than downloading the 'Alternate Installation CD'? I use a dial-up so its not possible for me...someguys on the forum asked me to edit xorg.conf file and manually change the "Driver" and "Identifier" entries...My current ones are this:

File /etc/X11/xorg.conf

Section "Device"
Indentifier: 'intel 845/825 Brookdale Chipset"
Driver: "i820"
BusID: 0:2:0

I have the intel's integrated chip disabled in Windows...

---

### Post by tseliot on 2006-07-28
> **sbjaved said:**
> Any other way than downloading the 'Alternate Installation CD'? I use a dial-up so its not possible for me...someguys on the forum asked me to edit xorg.conf file and manually change the "Driver" and "Identifier" entries...My current ones are this:

File /etc/X11/xorg.conf

Section "Device"
Indentifier: 'intel 845/825 Brookdale Chipset"
Driver: "i820"
BusID: 0:2:0

I have the intel's integrated chip disabled in Windows...

Try changing the driver to "vga" so that it looks like this:
```
Section "Device"
Indentifier: 'intel 845/825 Brookdale Chipset"
Driver: "vga"
BusID: 0:2:0
```

Then type this (I've never tried it though)
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by sbjaved on 2006-07-29
> **tseliot said:**
> Try changing the driver to "vga" so that it looks like this:
```
Section "Device"
Indentifier: 'intel 845/825 Brookdale Chipset"
Driver: "vga"
BusID: 0:2:0
```

Then type this (I've never tried it though)
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```
Nope...doesn't work...the "/etc/init.d/gdm restart" command gives 'fail' error...Maybe that's bcz we're trying to force the disabled chip to run??? Intel's integrated chip is DISABLED(at least in my windows) and i use my Ati 9200SE for display. The BusID for intel's integrated chip(disabled one) is 0:2:0...while for ati its 1:0:0...but even inputing that doesn't work...

What is going on?

---

### Post by tseliot on 2006-07-29
> **sbjaved said:**
> Nope...doesn't work...the "/etc/init.d/gdm restart" command gives 'fail' error...Maybe that's bcz we're trying to force the disabled chip to run??? Intel's integrated chip is DISABLED(at least in my windows) and i use my Ati 9200SE for display. The BusID for intel's integrated chip(disabled one) is 0:2:0...while for ati its 1:0:0...but even inputing that doesn't work...

What is going on?

I didn't notice that you have an Intel card too.

The solution should be the following:

1) unplug your ATI card

2) connect your monitor to your Intel integrated card

3) the livecd should work fine therefore you can **install** Ubuntu now

4) after you have installed Ubuntu you can use this guide to use your ATI card instead of the integrated one:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by sbjaved on 2006-07-31
Fine... i'll try that...

---

### Post by sbjaved on 2006-08-02
The dpkg-reconfigure xserver-xorg did the trick!!!!

I was welcomed by a Ubuntu screen with all the icons...Yayyy!

But i didn't find an install button to install Ubuntu on the Hard disk...

Where would that be? Plus if i reboot will the xorg.conf file be restored to default values??? I would have to run the configuration utility again?
Edit/Delete Message

---

