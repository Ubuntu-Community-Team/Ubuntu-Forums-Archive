---
title: "Unusual solution to Low Resolution at boot (Nvidia)"
date: 2008-09-05
forum: Multimedia Software
---

### Post by practic on 2008-09-05
This is not a question but a solution which I'm posting here as I could not find it anywhere else on the web.

I installed a Linux Mint 5 (gnome desktop) distribution on a new computer with a PCIe Nvidia 8400GS Graphics Card.  Mint is built on Ubuntu Hardy, so I think it applies to this forum.

I spent about a week installing software, configuring, and tweaking the new computer, only to have the graphics suddenly boot into low-res (800x600) on a 22" monitor (which normally handles 1680x1050 natively).

Nothing would bring it back.  I tried editing xorg.conf, running nvidia-settings, uninstalling and reinstalling the Nvidia driver, purging nvidia from the system and re-installing using Envy.  No change.

Initially at boot the Nvidia logo appears in hi-res, then the screen goes a few different shades of black (I have auto-logon turned on), and the desktop comes up in 800x600.

Finally I decided to create a small partition at the end of my hard-drive and do a fresh install of Mint, and a fresh install of the Nvidia driver.  I used the updated version of Envy again to install the driver as my card requires the 173 release of Nvidia, not the 169 version that is installed by some of the Ubuntu utilities.  It worked fine.

So I decided to do a brute-force method of elimination.  Opening Nautilus with "sudo nautilus" from the terminal, I wiped out the /etc/X11 directory on my original installation and copied over the contents of the same from the fresh install.  Booted into the original install...same problem...low-res again!  So this convinced me it was not a problem with xorg.conf, and I began to look elsewhere.

My next suspect was something in the home directory, so I backed up everything from home in the fresh install, and brute-force copied everything over from the original.  That caused the fresh install to boot into low-res, so I knew the problem was somewhere in home.

I next began to delete folders from home (home/"user" to be exact) out of the fresh install...taking a few at a time, then logging out and back in to see if the problem was fixed.  I finally narrowed it down to the hidden ".gnome2" directory.  Inside this folder was a file called "monitors.xml" which had the following contents:

- <configuration>
  <clone>no</clone> 
- <output name="default">
  <vendor>???</vendor> 
  <product>0x0000</product> 
  <serial>0x00000000</serial> 
  <width>800</width> 
  <height>600</height> 
  <rate>73</rate> 
  <x>0</x> 
  <y>0</y> 
  <rotation>normal</rotation> 
  <reflect_x>no</reflect_x> 
  <reflect_y>no</reflect_y> 
  </output>
  </configuration>

You can see the entries for width/height as 800x600.  Once this file was removed, my desktop booted in its natural 1680x1050 resolution.  Put the file back into the ".gnome2" directory and the monitor was back to 800x600 at boot.  I'm not sure which utility created this file, as I tried out quite a few different utils over the week.

Anyway, for those struggling with a low-res boot problem, this is one thing to watch out for.

---

### Post by GreatGariny on 2009-07-20
Thanks for the solution.  I had this same problem with Jaunty and my Nvidia 7 series card.  I edited the monitors.xml file in the ~/.gnome2 directory to my resolution settings.  This should work for any Nvidia card that boots up in an incorrect resolution.

---

### Post by igorzwx on 2009-07-21
Very interesting!!!

Have you tried to edit the evil file?

---

### Post by igorzwx on 2009-07-21
you can edit it with a text editor (gedit)

try

System -> preferences -> display

this might be a GUI for the same "evil file", I presume.

---

### Post by RonakG on 2010-10-20
Thanks a lot for this solution.  I too had a monitors.xml file in my ~/.config/ directory.  I just removed the <configuration> entry with output as "default" and it worked.  I have been searching for this for few months.

---

### Post by adampdx on 2010-10-20
Tried that.

It failed.

Won't accept any higher generic resolution typed in that it wouldn't already accept.

---

