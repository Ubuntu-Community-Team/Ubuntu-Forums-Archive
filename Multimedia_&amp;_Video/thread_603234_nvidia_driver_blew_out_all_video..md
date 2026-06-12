---
title: "nvidia driver blew out all video."
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by llanitedave on 2007-11-04
I blame Google Earth.

I had just completed a clean install of Kubuntu Gutsy Gibbon on my wife's Athlon 64.  I enabled all the repositories, installed tons of applications, had Flash and sound working, got a couple of YouTube videos, and all seemed right with the world.

Then I installed Google Earth. As it opened, it popped up a warning dialog that my graphics driver needed to be updated, and it would run very slowly until I did so.

I have an EVGA e-GeForce 8400 GS, in addition to the on-board video.  My monitor is an Acer AL 1916W widescreen.

I dutifully sauntered over to the Systemn Settings utility, opened the Monitor and Dsplay option, and tabbed to hardware.  Sure enough the 8400 GS was listed.  I selected it, and selected "standard" on the driver button.

Then I clicked on the "Test" button.

The bottom dropped out.  The screen became a gay blur, and I couldn't get back to where I had been.  I rebooted, and observered a multi-colored flashing series of horizontal and vertical bars.  I couldn't get any output at all from the on-board video port.

I could still boot into safe mode, so I did, and opened the xorg.conf file using *vim*.  Looking at the driver section, the type was still listed as "nv", so I changed it to "nvidia" and saved the file.

That made it worse.  Now I get no output whatsoever from *either* port.  I can't even go into safe mode any longer, because the screen now simply blanks out before it gets as far as the log-in .

Am I going to have to re-install?  I can boot up with the install disk, but even then, it takes as long as 10 minutes for the screen output to appear.

---

### Post by Levander on 2007-11-05
I wonder if when you selected "standard" if you changed the installed driver somehow?  Then , you started switching video cards and screwed the system up worse.

Every time you switch video cards, you have to reconfigure X.  So, if you unplug your monitor from your 8400 GS card and plug it into your onboard card, you have to reconfigure X.

To reconfigure X, "sudo dpkg-reconfigure xserver-xorg", and then follow the menus.  You'll need to know stuff like which graphics driver you want to use, and if it doesn't detect your monitor, you'll need to know your Horizontal and Vertical refresh rates, which are available in your manual.

---

### Post by llanitedave on 2007-11-05
Thanks for answering, Levander.  Well, I *definitely* screwed the system up worse, since I get no graphic output at all now, not even failsafe mode.

One last question.  Can I reconfigure X from the install cd?

If not, I'll just have to wipe everything and start over.

---

### Post by Levander on 2007-11-05
The install CD will autodetect your graphics card and monitor and set something up.  But, this set up will only be good for that one boot off the LiveCD.  Next time you boot (whether off CD or hard disk) that setup will be gone because when you run off CD, it doesn't even know you have Ubuntu installed on your hard drive.  It's not touching that at all.  

When running off LiveCD, you could tell your system about your hard drive by mounting your hard drive onto the improptu filesystem made by the LiveCD.  Then, you could do something like "cp /etc/X11/xorg.conf /mnt/sda1/etc/X11/xorg.conf"  Is this paragraph sounds weird, don't worry about it for now.

What you probably want to do is to boot off the hard disk, and off the grub menu select the item that says "rescue mode" or "emergency mode" or something like that.  When that rescue mode boots, you'll get a prompt where you'll be logged in as root.  At that prompt, "dpkg-reconfigure xserver-xorg"  - there's no need for sudo here since you're already root.

When you're done reconfiguring X, exit from the shell (either Ctrl-D or type 'exit') and your normal system will be booted (off the hard disk).

---

### Post by llanitedave on 2007-11-06
Apparently I was too far gone even for rescue mode.  I couldn't get a screen at all once I left the bios.

So, I reinstalled from scratch, and configured the driver from the toolbar icon.  This time it seems to have worked fine.  I haven't tried to install Google Earth again yet, but I'm hoping the problem is correct.  Took a couple of extra hours to reinstall.  Took a lot longer than that to troubleshoot!

---

### Post by wolfen69 on 2007-11-06
if i think any problem is going to take more than 25 min, i'll take a re-install anyday. im always trying new distros anyway. keeping all data/media/settings on seperate drives is key. you did the right thing. good luck and have fun.

---

