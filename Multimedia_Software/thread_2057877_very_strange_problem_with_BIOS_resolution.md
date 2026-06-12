---
title: "very strange problem with BIOS resolution"
date: 2012-09-14
forum: Multimedia Software
---

### Post by N00b-un-2 on 2012-09-14
as of yesterday, when I boot up my computer, from the time that I power on up until Plymouth starts, the screen on my laptop is stuck in a "windowed" 1024x768 resolution instead of scaling to 1280x800 like it normally did before.
The problem began after booting my computer off of an old Intrepid Ibex CD.  When X started, the screen was a garbled mess.  It looked like pink and brown TV static if that makes any sense.  So I hit ctrl+alt+F1 to get to the TTY and rebooted.  Upon reboot my BIOS resolution is messed up.
This isn't a huge problem as it doesn't really affect anything except making my graphical bootloader look strange.

---

### Post by N00b-un-2 on 2012-11-16
turned out that it was a BIOS update issue.  I upgraded my laptop's Phoenix BIOS from ver. 1.14 to 1.17, but the ATI VBIOS did not get updated in the process.  After updating again using Winphlash from within Windows XP as opposed to the FreeDOS bootable USB I made, both the motherboard and graphics card BIOSes were updated properly.

On a hunch, I figured that the Winphlash utility would probably only work from Windows XP, and it turned out I was right.  Also not cool, considering that this model to the best of my knowledge was only shipped with Windows XP if it were custom ordered that way, otherwise it came with Vista Home Basic.

... Kind of lame that I had to dig out my old Windows XP disk, create a partition to install it on, install 32 bit Windows XP (on my 64 bit laptop with 4GB of RAM), run updates and install drivers, and then fix my boot loader in order to update my BIOS.  I Could not run Winphlash from Windows 8 Pro 64 bit or Windows 7 64 bit or 32 bit, and no amount of "run in Windows XP SP3 compatibility mode" would change this fact.  It stands to reason that since Windows 7 is built upon Windows Vista technology that I wouldn't have fared any better on Vista.

I should note that while upgrading my BIOS from version 1.14 to 1.17 did fix my graphics card issues, I've run into some new problems on my Acer Extensa 5420 laptop.  First of all, when my computer wakes up from sleep or hibernate my sound no longer works, and the problem persists across all operating systems.  Not a considerable problem for me since I mainly use my laptop at school and have it muted whenever in class.  Still, it is a bug worth noting.

Second, I've completely lost the ability to boot OSX on this laptop.  I understand that this is not an Ubuntu issue nor something that is supported or encouraged on this forum, but I felt it was worth mentioning nonetheless.  I am a programmer and web developer, so having as many platforms available to test on is a must for me.

---

