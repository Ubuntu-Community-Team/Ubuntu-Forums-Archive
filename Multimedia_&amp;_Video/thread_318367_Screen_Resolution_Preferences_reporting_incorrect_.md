---
title: "Screen Resolution Preferences reporting incorrect refresh rate"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by Yfrwlf on 2006-12-13
The refresh rate on my desktop right now seems quite nice.  It's at least 75 if not 85 or higher.  The refresh rate in the Screen Resolution Preferences box only lets me choose 50, 57, 58, and 59 Hz.  When people normally think of refresh rate they think of 60, 75, 85, 90, or 100 or so, and I'm assuming that they are talking about the vertical refresh in Hz?  If so, then I'm on the same page, and the refresh rate is being reported far lower than it actually is.  Does anyone know why this might be?

At first I was worried that it was actually 50 Hz (without remembering that it would look extremely flickery if it was actually 50 Hz), so I dove into xorg.conf to try to fix the problem.  I added the vert and horiz lines to the monitor section as follows (after finding out the specs on my monitor) thinking that it would fix the problem.

```
Section "Monitor"
    Identifier     "G90f-2"
    Option         "DPMS"
    HorizSync      30-97
    VertRefresh    50-180
EndSection
```

My monitor was detected correctly, it filled in the "identifier" line all by itself, so everything is probably right, but it would be nice if the refresh rate were to display correctly so that I could change my refresh rate.  Adding those lines did not change anything, I still have the same refresh rate options in the System > Preferences > Screen Resolution dialog box.  Anyone have any ideas as to why this is?  :)

P.S.  I have a friend who just installed Ubuntu (6.10, like me) and I was disappointed to learn that Ubuntu did not correctly detect his monitor and instead it shows up as a Generic Monitor and he says it's flickery, too.  I'm going to have him specify his sync/refresh rates like I have done, and I think in his situation it will help him.  He also needs to specify additional resolutions in the Screen section, if I understand correctly, to get the higher resolutions if they aren't already there.  I tried putting "1920x1440" in the default depth section of 24 at the beginning since my monitor says it supports that resolution, but after rebooting X I still did not have that resolution available to me in the Screen Resolution Preferences box.  I am assuming that it's because it's not compatible with both my monitor and video card, or because it doesn't support it at a 24-bit depth.  I hope my friend will have better luck with the changes in xorg.conf actually showing themselves as his situation is much more dire.

---

### Post by Yfrwlf on 2006-12-13
Oh, one more comment.  It would be cool if there was someplace (and there might be) where he could let the developers know his monitor model, refresh ranges, and max resolutions.  If everyone could help contribute to the list of models that Linux recognizes, it'd help a lot faster!  I was thinking it might be especially awesome if anytime a monitor was detected as generic (not detected), it could open a little user-friendly dialog that would let them, if they chose to, enter the information about their monitor manually and then it could automatically add that information into xorg.conf, plus send the information to a group of developers so they could add it.  Just a thought :)

---

### Post by Yfrwlf on 2006-12-15
If I try to select one of the other refresh rates, like 59 for example, it get's much much more flickery.  So, I'm using a refresh rate that's like 85 or so even though it says 50.  What kind of craziness is going on here?  Anyone know?

---

### Post by Yfrwlf on 2006-12-18
Just an update to my own problem so everyone knows, if anyone is reading this. =D  I installed Kubuntu, just for fun, and it turns out that it does show the correct refresh rate in the monitor settings section.  So, I'm pretty sure this is a bug with the Screen Resolution program thingy in Gnome.  Guess I will report the bug. ^^

---

