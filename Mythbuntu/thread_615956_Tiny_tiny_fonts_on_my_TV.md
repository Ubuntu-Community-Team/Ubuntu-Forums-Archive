---
title: "Tiny tiny fonts on my TV"
date: 2007-11-17
forum: Mythbuntu
---

### Post by Sexy Pants on 2007-11-17
Hey folks

I had a sorta screwy but semi-functional MythTV setup for a while, but I decided to wipe it all clean and use Mythbuntu. Here I am with a problem I never really faced before.

I use my setup on a normal ~21" CRT TV with RCA video ins. I have no idea what resolution I'm running because I can't read anything - the font is too small. Right now I have it at a resolution that at least fits the whole screen, which is a plus and I got there from ctrl+alt+plus and minuses and lucky breaks fiddling with the display settings that I couldn't read. I've also managed to increase the font size in the console so I can now read that just fine.

from looking around I've run the command that tells me my current DPI is 38x46 DPI. Since I'm using an onboard nvidia TV-Out, I tried editing the monitor settings in /etc/X11/xorg.conf and adding Option "DPI" "96x96" but found no difference after ctr+alt+backspace (and double checked that it saved). I've also tried setting "font size" to "big" in the mythbuntu settings but who knows if it actually said that. 

While I've been using linux for a few years off and on now, I'm far from a wiz and you'd might as well speak to me like I've never used it before.

Thanks!
Hunter

---

### Post by foxbuntu on 2007-11-19
Have you checked your DPI since you changed to 96x96, Also I would say to set it to 100x100 (Pretty Std for TV). What resolution is default. [Check your xorg.conf in the Display settings you should see a default "Depth" and in the depth section look at what the first resoultion is listed]

---

### Post by pksings on 2007-11-19
from the Menu, System, Login Window Preferences, Security, Configure X Server, under the Server Settings section, on the line labed Command, add your desired dpi setting by adding onto the end of the line. I put "-dpi 96" 

My entire command line then reads, "/usr/bin/X -br -audit 0 -dpi 96"
click , close, close, close to save and exit.
Kill your X server, ctrl-alt-bkspace.

Should be fixed, it was for me.

---

### Post by thematadorme on 2007-12-14
I've just posted a solution that I think will help you.
[http://ubuntuforums.org/showthread.php?t=640389]("http://ubuntuforums.org/showthread.php?t=640389")

---

