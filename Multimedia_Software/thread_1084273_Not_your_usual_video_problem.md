---
title: "Not your usual video problem"
date: 2009-03-01
forum: Multimedia Software
---

### Post by velozoom on 2009-03-01
Been in the IT field for nearly 10 years and it's been a long time since a problem has truly flummoxed me but I can't even sort for sure if this is a hardware or software problem.  

My workstation guts finally started glitching out on me after 4 faithful years and, since I was looking for any excuse to upgrade, I bought new guts for my system- MoBo, CPU, RAM, Power supply, and a couple new case fans.  

Swapped the hardware and Ubuntu Intrepid booted right back up.  The problem is my dual monitors.  The board is an Asus P5QL-Em with dual (1 VGA, 1 DVI) output.  This is where it gets confusing, btw.  

First, I both monitors have input ports for both DVI and VGA.  They've run on DVI for the last several years without issue.  The monitors appear to be in 100% working condition.  

Obviously, one is hooked to the DVI port and one to the VGA.  

When I boot, the POST and GRUB screens are displayed mirrored on both screens.  The Ubuntu log in screen appears on the DVI monitor whilst the VGA is totally black.  Once I log in, the screens lose video for a moment and then come back on.  This time the VGA screen displays its half of the desktop properly but the DVI monitor displays the following message-
> Digital Input
Cannot Display This Video Mode

This appears to be a message from the monitor itself and not Ubuntu or the integrated video card.  But...it's the bloody DVI monitor and it's complaining about Digital Input.....it's been displaying digital input for years.  

The monitor worked fine when the vid display was set to mirror.  Both monitors are detected by the display manager.  When I removed the check to eliminate mirroring and span the desktop is when this issue started. 

I've looked in the BIOS and through the ubuntu display manager settings and not seen anything that made a difference.   

Any ideas where I should start looking?  

Thanks.....

---

### Post by jyaan on 2009-03-01
It's saying exactly what's going on (I hope): It's trying to use an unsupported video mode (eg. wrong resolution). So, you should just need to change it. Hopefully that is all that's wrong here.

In case you don't know already, these settings would in /etc/X11/xorg.conf. However, if you have an nVidia card, you can change the settings more easily with the NVIDIA X Server Settings app. I believe ATI has Catalyst.

---

### Post by velozoom on 2009-03-01
both monitors are set to the same resolution.  my xorg.conf doesn't have the usual list of display modes, however.  It shows a single "virtual" display for the dual screen.  I have done the auto reconfigure of X from the command line that created this situation.  

I went into xorg.conf and tried playing with the resolution settings.  I reset to lower graphics, 800x600 which reverted to a mirrored display.  I changed the display settings to match for both monitors.  Both monitors are identical models bought at the same time so they support the same video modes.  


[EDIT]

Played some more and found a config that worked.  You were right, it was a resolution issue.  I assumed (wrongly as usual) that since one monitor worked and bother were set identically that it wasn't that.....

Still, it's odd.  Thanks for the help, I feel pretty stupid but at least I can see my whole desktop again.  ;)

---

### Post by jyaan on 2009-03-01
I'm glad you got it worked out. It happens to all of us at one time or another. :P

---

