---
title: "ATI Rage driver frustration. What version/desktop/other distro should I use?"
date: 2013-04-30
forum: Multimedia Software
---

### Post by Lukfi on 2013-04-30
Hello. I have an old computer with an ATI Rage series graphics card (I think it's Rage 128 with 16 MB memory, but does it really matter?). I want to use the machine primarily as a samba server, but it should also be able to function as a PC for web browsing and other simple stuff. The graphics card of course limits my selection of desktop environments to those that don't use 3D acceleration.
I had Ubuntu 12.04 installed on the machine up until a few days ago, when for no apparent reason I was no longer able to log onto the machine locally, only through ssh or telnet. Since Unity 2D is gone, what other choices do I have?

Already some time ago I wanted to try Linux Mint with its MATE desktop, but I had a weird bug where typing on the keyboard caused the graphics driver to crash, so I could not finish installing from the Live CD. (See here for details: [http://forums.linuxmint.com/viewtopic.php?f=46&t=130517](http://forums.linuxmint.com/viewtopic.php?f=46&t=130517) ) I was using Mint 14 (Quantal based). On the now-defunt 12.04 installation I installed MATE and it was working OK, so MATE is not the culprit.

Next I tried Lubuntu 13.04. I used the alternate CD to install since I wanted a smaller HDD footprint (in the future I want the system to be running off a USB flash drive, so all hard drives can sleep when not used). I'm having the exact same problem as with the Mint, key strokes crash the graphics driver. It doesn't happen on a GeForce 4 Ti (that one has different bugs, menu icons are flickering on and off and highlighted items are displayed incorrectly). Anyway, I'd prefer to use the ATI, since it's low power and passively cooled.

*Thinking out loud: there is a pattern here. 12.04 was OK, 12.10-based Mint and 13.04 are not. Apparently a new version of the r128 driver was shipped with 12.10. It could be the cause of these problems, or maybe there's a new version of Xorg or something else that doesn't work correctly with the driver.*

Xubuntu 12.04.2 I was not able to install at all, the Alternate CD installer hung itself on entering Wi-Fi SSID and password and just didn't seem to get my (access) point. So I later just installed xubuntu-desktop on the existing Lubuntu installation (how? well, only some applications crash the desktop when typing into them, terminal wasn't one of them). I could use XFCE instead of LXDE, sure. The problem is, since this is originally Lubuntu and not Ubuntu, it has a login dialog and guess what, bingo, the graphics crash several times before I can successfully type in my seven letters of a password. Otherwise it has not crashed while in the desktop, I think.

*Oh and the other stuff I tried. Fedora booted to a blank screen, courtesy of a driver bug. The bug is there in Ubuntu as well, but it only causes grub and other stuff to be invisible, I get picture as soon as the login screen or desktop environment loads. Ubuntu minimal install went well at first, I installed MATE on it, and then couldn't start it because 'startx' was a command not found. Bodhi Linux is lightweight all right, but it fails on the user friendliness side of things.*

Clean Lubuntu, before the Xubuntu hijinks, only took about 1,1 GB space on the HDD, which is very nice and also a far cry from the recommended minimum 5 GB.
To recap: I want a lightweight but nice looking and user friendly system with minimal bloat that will run on this graphics card. Lubuntu crashes, Xubuntu has a broken alt-CD installer, plain Ubuntu will install a lot of stuff I don't need (Unity and its GNOME based apps). So what are my options here? (apart from carrying the machine to a place where an ethernet cable is available and installing Xubuntu from there)

*Thank you if you've read this far. Please don't tell me I have to get a newer graphics card. You're not helpful. I don't need fancy 3D acceleration. The GeForce I mentioned is newer and still suffers from driver glitches. I could maybe get a Radeon 7000 or 9250, but do I have any guarantee it will work better?*

---

### Post by gordintoronto on 2013-04-30
The Rage 128 has become a "generic VGA card." It's 15 years old now, and you can't expect driver support for hardware which belongs in a museum.

At the same time, I would have expected Xubuntu or Lubuntu to work just fine with your ancient computer. How much memory is in the beast? Have you reviewed the system requirements for the systems you are trying?

---

### Post by Lukfi on 2013-05-01
> **gordintoronto said:**
> The Rage 128 has become a "generic VGA card." It's 15 years old now, and you can't expect driver support for hardware which belongs in a museum.
I'd beg to differ. Ubuntu still supports i386 even though the last 32bit CPUs were sold 6-7 years ago and those were i686.
Also, server motherboards used Rage XL chips for basic display capability as recently as 2006.
> At the same time, I would have expected Xubuntu or Lubuntu to work just fine with your ancient computer. How much memory is in the beast? Have you reviewed the system requirements for the systems you are trying?
The rest of the PC is newer. It's an Athlon XP 2500+ and 1 GB RAM on an nForce2 chipset. I got the Rage as a replacement for a faulty motherboard with integrated graphics. Like I said, I could replace the Rage with maybe a Radeon 9000/9200/9250 or 9550/9600 series if I'm lucky, but these are also very old cards and anything better for AGP is hard to come by. Also I don't want to invest in something I don't really need.

---

### Post by imacg3ppc on 2013-05-07
I have an r128 in use with lubuntu 12.04.. just got this working and it looks great! you are correct it's ancient, not quite 15 years yet, but if you're not processing 3d graphics it should be fine. There is different tweaks and workarounds for the r128s if you look thru the documentation for your card. Cant wait to design some tshirts in GIMP once the printers are working. this is 2001 imac special edition, sweet lil cpu and im gonna give it some lovin.

---

### Post by Yellow Pasque on 2013-05-07
> maybe there's a new version of Xorg or something else that doesn't work correctly with the driver.
It could be that. I would try L/Xubuntu 12.04.1 and if you do, make sure you don't install xserver-xorg-lts-quantal/raring packages. You should stick with xserver-xorg-lts-precise and 3.2.x kernel.

---

### Post by Lukfi on 2013-05-07
Why 12.04.1 and not 12.04.2? :?
And what will I do when 12.04 is no longer supported? :(
It does however seem that the older kernel works better. I tried Linux Mint Debian, which still uses 3.2.0 kernel in its latest version, and it works like a charm. (It's a bit too chubby for a flash drive installation, though.)

---

### Post by Yellow Pasque on 2013-05-07
> **Lukfi said:**
> Why 12.04.1 and not 12.04.2?

Because 12.04.1 uses Xserver 1.11.x and kernel 3.2. 
12.04.2 uses quantal's Xserver  (1.13.x) and kernel 3.5.x out of the box.

Once you have 12.04.1 installed, you can update all packages except the ones I mentioned previously.

> And what will I do when 12.04 is no longer supported?
If you find that newer kernel/X is really the problem, you have 4 years to report it and get it solved ;)

---

### Post by Lukfi on 2013-05-08
> **Temüjin said:**
> Once you have 12.04.1 installed, you can update all packages except the ones I mentioned previously.
Sounds like a great deal of fun when I get hundreds of available updates after installation.
> If you find that newer kernel/X is really the problem, you have 4 years to report it and get it solved ;)
I've never done that before. Who and where would I report this to? The kernel bugtracker? X server bug tracker? Or to the driver developers? And how do I know what exactly is causing the problem? I don't really feel like trying all the different combinations of kernels and X servers.
Then there's the question of whether anyone cares, since Rage is so old and scarce :)

But thinking about it, I don't think 12.04.2 causes trouble. I installed this version of Xubuntu and the graphics are working... I just couldn't get the Wi-Fi to run (which is probably a freak bug in the installation CD or something, plain Ubuntu 12.04 worked previously).

---

