---
title: "Visual Effects not retained after reboot"
date: 2010-02-27
forum: Multimedia Software
---

### Post by Icarus315 on 2010-02-27
I have an issue I was hoping I could get some pointers with.  I like my wobbly windows, love 'em.  Recently on the latest ATI manual driver update they went away.  From boot, log into desktop, my pidgin window defaults to open.  Can move it for about 1.5 seconds and be wobbly then the screen does it's reinitialize thing and the window becomes non-wobbled again.  At any time I can go to System > Preferences > Appearance > Visual Effects and enable the effects and they work without issue.  So, start up with visual effects, something right away turns them off, I can turn them back on at any time and they will stay on.  I don't think its actually anything to do with my graphics cards drivers - those seem to be fine.  Rather I believe it is a Gnome setting somewhere.  I have tried setting my Visual Effects to None, rebooting setting them back to where I like them and rebooting again in case it was a corrupted setting.  Unfortunately this did not resolve the issue.  I'm not scared to edit text files, its knowing where to look that I could use some help here with.  Thank you in advance.

---

### Post by Icarus315 on 2010-03-01
No suggestions?  Occasionally on a boot the visual effects will remain enabled but more often than not they get set to "None" and I have to set them.

---

### Post by rgrant222 on 2010-03-01
I've been searching the forms for the very same reason!  I installed Ubuntu about 4 or 5 days ago, and I have been struggling to make the visual effects stick after rebooting for exactly that long.

However, I have finally solved the issue (for me, at least).  Someone on another thread similar to this one reported that he (or she) fixed the problem by updating his nVidia drivers to version 185.  I thought I'd just take a look under System->Administration->Hardware Drivers, just to see what it had to tell me.  Lo and behold, the driver in use was version 173, although it listed (and even recommended) version 185.  This, by the way, is despite the fact that every time I chose "Extra" in the "Visual Settings" tab of the System->Preferences->Appearance dialog box, Ubuntu would report that it was searching for available drivers before proceeding to apply the extra effects (presumably because it had indeed found better drivers).

Anyway, I clicked version 185 to highlight it, then I clicked the "Activate" button at the bottom of the dialog box.  Ubuntu downloaded the driver (that's right, the driver, apparently, wasn't even ever on the machine), installed it, and prompted me for a reboot.  After rebooting, I noticed that AWN loaded upon startup (like I had told it to), which was good, but I did have to go back in and click "Extra" once more, then configure the CompizFusion settings again (as they had reverted to their defaults), and reboot one final time.

In the end, this produced success.  CompizFusion loads perfectly on startup, and retains it's settings between sessions.  To be fair, when I check to see if "Visual Settings" are still set to "Extra," none of the choices appear to be selected (all the radio buttons are empty).  Nonetheless, everything works fine, as if the "Extra" option is in fact selected.

Your post was the first one I saw when I seriously began searching the forms for answers.  I saw that the post was two days old and no one had responded, so when I solved the problem for myself, I felt the need to come and help you (I hope I did).  Please let me know if this was any help for you at all!

---

### Post by Icarus315 on 2010-03-02
Thank you for your reply ;)  Unfortunately I'm Ati so installing the nVidia driver won't help in my particular situation :D  But.. Perhaps later on this month when Ati's 10.3 drivers come out I'll see what happens.  It is turning into a very odd situation for me now, it was all the time visual effects would be set to None, now for some reason it is some times (with a bit heavy on the some part) the visual effects will be set to None.  In the end it is a very minor annoyance and when you think about it I'll be installing 10.04 in a few short months so if no suggestions appear I *can* just live with it ;)  Again, thank you: your solution will be indexed by search engines and will hopefully help someone else ;)

---

### Post by jaycee23 on 2010-03-23
> **Icarus315 said:**
> I have an issue I was hoping I could get some pointers with.  I like my wobbly windows, love 'em.  Recently on the latest ATI manual driver update they went away.  From boot, log into desktop, my pidgin window defaults to open.  Can move it for about 1.5 seconds and be wobbly then the screen does it's reinitialize thing and the window becomes non-wobbled again.  At any time I can go to System > Preferences > Appearance > Visual Effects and enable the effects and they work without issue.  So, start up with visual effects, something right away turns them off, I can turn them back on at any time and they will stay on.  I don't think its actually anything to do with my graphics cards drivers - those seem to be fine.  Rather I believe it is a Gnome setting somewhere.  I have tried setting my Visual Effects to None, rebooting setting them back to where I like them and rebooting again in case it was a corrupted setting.  Unfortunately this did not resolve the issue.  I'm not scared to edit text files, its knowing where to look that I could use some help here with.  Thank you in advance.

I've got exactly the same issue with the same driver!

Would be interested to know if you found a solution

---

### Post by jaycee23 on 2010-03-26
> **Icarus315 said:**
> I have an issue I was hoping I could get some pointers with.  I like my wobbly windows, love 'em.  Recently on the latest ATI manual driver update they went away.  From boot, log into desktop, my pidgin window defaults to open.  Can move it for about 1.5 seconds and be wobbly then the screen does it's reinitialize thing and the window becomes non-wobbled again.  At any time I can go to System > Preferences > Appearance > Visual Effects and enable the effects and they work without issue.  So, start up with visual effects, something right away turns them off, I can turn them back on at any time and they will stay on.  I don't think its actually anything to do with my graphics cards drivers - those seem to be fine.  Rather I believe it is a Gnome setting somewhere.  I have tried setting my Visual Effects to None, rebooting setting them back to where I like them and rebooting again in case it was a corrupted setting.  Unfortunately this did not resolve the issue.  I'm not scared to edit text files, its knowing where to look that I could use some help here with.  Thank you in advance.

Just upgraded to ATI 10.3 driver. So far seems to have cured the problems with compiz

:D

---

### Post by Icarus315 on 2010-03-27
Upgrading to 10.3 seems to have fixed it for me too!  Keeping fingers-crossed ;)

---

### Post by Sandy Al on 2010-04-30
I have this same issue after upgrading to 10.04 today.
Running on a hp tx1499us.

Any help?

For me this means i have to plug in an external monitor to be able to see what I'm doing, then I can set the 'extra' visual effects (at which time my laptop screen regains its usefulness), which only remains in place until reboot...

... and the cycle begins again.

---

