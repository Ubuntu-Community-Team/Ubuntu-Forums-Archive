---
title: "[ubuntu 11.04]  LMMS 0.4.10 VeSTige broken"
date: 2011-05-13
forum: Multimedia Software
---

### Post by koffeinöverdos on 2011-05-13
It was all working perfectly and then I made the stupid decision to upgrade to Natty, and i have no idea what went wrong in the process. I searched hard on google and here until i was ready to pull my hair out (watch somebody pull up a duplicate topic and call me an idiot now).

Alright so, when I first booted up LMMS after my integrated upgrade to natty. I load a project involving use of Vestige, and as the program loads it loads the vst gui's and keeps them up, and when i closed them down it gave me an error about Remote_vst_plugin.exe or something. I know that's not helpful and I wish I could copy the exact error, but now Vestige is broken even further and it simply says "z3ta+.dll could not be loaded for some reason" and that's it.

Are there either alternatives to Vestige in LMMS 0.4.10 or has somebody else had this problem, though not from what I can find?

I tried rolling back to 0.4.9 and same problem, i fiddled with the wine config and no luck..

---

### Post by koffeinöverdos on 2011-05-13
Okay maybe I'm onto a trail of some sort here. I've noticed that Wine itself simply doesn't work anymore at all from trying to open Wine Config from the applications menu even after a restart of the computer. I went into the terminal and executed "winecfg" and it said "wine: virtual memory exhausted" so i tried "wine notepad.exe" and got the same thing. If I right click-open notepad.exe with wine it hangs and then doesn't happen. This is truly the oddest problem here.. I'll try just reinstalling wine and report back if it works or not.

I imagine I'll get it back to the part where it displays the vst gui in one window, and then has another empty window the same size, and gives me that remote_vst_plugin.exe error again.

---

### Post by koffeinöverdos on 2011-05-13
I fixed wine and got back to the bug i had before, then i fixed that and now everything seems to work as before in Maverick (which was hands down the best release of Ubuntu I ever used, i've been a user since Hardy). It appears that the problem was the eye candy they have added into Natty. Even with Ubuntu Classic, which should be the ACTUAL classic gui, something in it screws it up, probably having to do with the slick shadows it feels the need to cast around every window. You have to choose Ubuntu Classic (no effects) at the login screen, at least that is what has appeared to work for me.

Stupid sucky eye candy. Hopefully someone else will at least benefit from my thread then. My apologies for nerd raging.

---

