---
title: "Resolution Doesn't &quot;Stick&quot;"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by jsimmons on 2007-06-26
Installed nVida proprietary drivers, and this allows me to select my resolution and freq, but...

When I rebooted, Ubuntu reset itself to the original resolution I got when it was first installed.

After I rest it to 1680x1050x32 at 60hz in the nVidia control panel, I checked it in System/Preferences/Display, and while the resolution was coirrect, the freq read 87hz.  

How can I fix both of these issues?

---

### Post by longlegs on 2007-06-26
hi
see my post a few minutes ago about editing /etx/X11/xorg.conf

Good Luck
longlegs

---

### Post by wizardofyendor on 2007-06-26
That's because when you open the nvidia control panel, it runs as you not as root.  To get the settings to stick, open a terminal, then type 
```
gksudo nvidia-settings
```
then make your changes to resolution, and remember to click write settings to xorg.conf

Then when you log off and back on, it will remember your settings.

---

### Post by Biased turkey on 2007-06-26
Thank you for trying to help people.
You are all lucky to be able to at least select the resolution in the Nvidia control panel. In my case I only have a 800 x 600 resolutions and no other choice . I can't even select 640 x 480 lol.
Everyrhing goes back to normal if I **disable** Nvidia proprietary drivers.
There are just 2 possible causes to that problem:
Nvidia drivers is buggy ( I doubt it because I don't have that problem with the Mepis distro that is based on Ubuntu )
or the Ubuntu proprietary drivers package is faulty.

By looking at the posts on the video subforum it looks like I'm not the only one with that problem.

---

