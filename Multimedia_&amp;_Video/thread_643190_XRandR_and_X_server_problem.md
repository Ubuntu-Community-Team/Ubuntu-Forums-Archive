---
title: "XRandR and X server problem"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by kentpend on 2007-12-17
I solved the problem-

I forgot that I hadn't reset xorg.conf after using a dual monitor set up a while ago, and that was screwing things up.

---

### Post by kentpend on 2007-12-17
Ok.. I'm not sure why that posted itself before I finished typing it.

Regardless, here's the issue I'm experiencing:

When I try to change the screen resolution, I get an error message saying
> The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

This was not a problem earlier, but it has been a while since I tried to change the resolution that I don't know what might have caused this problem.

Any ideas?

---

### Post by pizpot on 2008-03-06
I just got that error too. To fix it removed my restricted nvidia drivers, rebooted, and then put them back. They are in System->Administration->Restricted Drivers Manager.

Nvidia must have hired new programmers who are re-writing everything rather than building on it is my guess. Just look at how many people cant play old games anymore once they upgrade vid cards. :-( Cossacks!!!!

---

### Post by elustran on 2008-05-05
I'm having the same problem, I have an ATI card, and I've tried numerous things, such as reinstalling the drivers, but nothing has worked.  It's a random problem too.  I can't for the life of me think of what I changed before I started having this problem.

---

### Post by wordchisler on 2008-05-06
I had the same problem when I upgraded to hardy heron. Disabling nvidia driver, rebooting, enabling, rebooting did not help. Installing Nvidia-settings gave me a clue to search for "enable xrandr" which yielded a fix: [http://www.systemparadox.co.uk/XRandR](http://www.systemparadox.co.uk/XRandR)

> Submitted by Simon on Wed, 2006-06-21 10:17. 

The XRandR (X Resize and Rotate) extension isn't loaded, how do I enable it?
A simple task, one would have thought, but I only found the answer after several days of Googling and asking around. Hopefully this will help someone else with the same question.

To enable XRandR, simply add the following to your xorg.conf file:
[FONT="Courier New"]Section "ServerFlags"
        Option "RandR" "on"
EndSection[/FONT]

At present, XRandR will not load if Xinerama is enabled.
If you have a dual head system, you will need to look into using MergedFB instead.

Why Xinerama goes in the ServerLayout section, XRandR goes in the ServerFlags section and glx goes in the modules section I don't know.

After adding those lines and rebooting, I was able to load the Screen Resolution dialog and save nvidia-settings. Xinerama was disabled, I do not recall disabling it, but I might have. I might try twinview.

---

