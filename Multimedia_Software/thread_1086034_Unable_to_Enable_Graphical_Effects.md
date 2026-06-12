---
title: "Unable to Enable Graphical Effects"
date: 2009-03-03
forum: Multimedia Software
---

### Post by RetroX on 2009-03-03
I decided to put Ubuntu 8.10 on my six-year old laptop (since it has XP installed, although it doesn't run well).

It runs wonderfully, however, it won't let me enable graphical effects.  Sure, the graphics card has only 8MB of memory, but I honestly don't believe that the GNOME graphic effects are intensive enough that the computer won't run.  After all, my graphics card is an ATi Radeon (old, but still an ATi).

I mean, it's not like I'm running Vista Aero on this machine - it should work.  I haven't run into any graphics-related problems with this card running both XP and Ubuntu, yet Ubuntu won't let me enable them.  And I don't think that there's some rendering method used that my graphics card doesn't support.

Is there a way to force Ubuntu to enable the graphics effects, or is there a reason why I shouldn't be enabling the effects?

My laptop is a Dell Latitude C600 and my card is an ATi Mobility M3, if you want to look up further specs on that.

---

### Post by Dadsgé on 2009-03-03
have you tried to install compiz?
just go to synaptic and search for compiz
then install the package 'compiz-configmanager' or something like that
normally it should work after the installation
you can choose your effects in the manager
system > preferences > advanced desktop effects

---

### Post by RetroX on 2009-03-03
Compiz comes with 8.10. :P

Although compizconfig-settings-manager isn't.  I'll try that.

Although, what I mean is when you go to Appearance > Effects.  It won't let me raise the effect level, because it says my graphics card can't handle it.

EDIT: Nope, that didn't work either.  It still won't enable the effects.

---

### Post by Dadsgé on 2009-03-04
in which way did you try to enable?
in advanced desktopeffects settings or just in effects?
because i had the same problem, i couldn't raise it either, but with the advanced desktopeffects settings i can use the cube and every other option.

---

### Post by athaki on 2009-03-04
Could you refresh my memory: are there any restricted drivers installed that could possibly enable desktop effects (granted ATI isn't exactly linux friendly).  You could try running glxgears in a terminal and see what kind of FPS you're getting from your video card.

---

### Post by RetroX on 2009-03-04
I have the Radeon driver from synaptic (although it was installed with Ubuntu), so there shouldn't be any driver issues.

For GLXGears, I got around 32 FPS, but I also have Firefox (with many add-ons) and a couple other programs open, so it might get up to about 40 without anything open.  Although (guessing), I would probably get around 50 FPS if I ran it in XP with nothing open.

---

