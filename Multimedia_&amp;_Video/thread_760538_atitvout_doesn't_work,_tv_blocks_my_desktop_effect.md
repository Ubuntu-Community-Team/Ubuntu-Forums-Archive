---
title: "atitvout doesn't work, tv blocks my desktop effects"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by Klaasvaak on 2008-04-20
I want to use my TV as a second monitor, or, if that isn't possible, i'd just want to use it in stead of my default screen and watch movies on it. 
The problem is that whenever i plug my tv into my computer I can't use desktop effects after restart. The error message is the same as when I didn't have the right video card drivers installed.
I have a ATI Radeon x1650, using only one monitor and my tv in the s-video-output. 
Atitvout gives me the following error messages:
```

maarten@Fifi:~$ sudo atitvout detect
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.
maarten@Fifi:~$ sudo atitvout detect -r
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.
maarten@Fifi:~$ sudo atitvout detect-r
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.


maarten@Fifi:~$ sudo atitvout -r pal auto
Forcing Radeon/Rage 128 mode
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!
maarten@Fifi:~$ sudo atitvout detect
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.maarten@Fifi:~$ sudo atitvout -r pal ct
Forcing Radeon/Rage 128 mode
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!

```

I ran out of sollutions. How do I solve the problem with my desktop effects? (I'm typing this having a 800x600 resolution, I don't really like that, seen as this CRT usually gives me tiny pixels...)
And how do I make atitvout work?

---

