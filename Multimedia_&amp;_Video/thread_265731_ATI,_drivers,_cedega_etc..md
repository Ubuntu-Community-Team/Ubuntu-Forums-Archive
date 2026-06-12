---
title: "ATI, drivers, cedega etc."
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by SonnyBonds on 2006-09-26
Hi everyone, first-time ubuntu user here!

So.. after hours and hours of trying to figure out how to get the ATI drivers to work i managed to get them installed.

I am a little confused, because glxgears gives me 300 fps, however Enemy Territory runs blazing fast (im guessing 60-100).

On Cedega, World of Warcraft runs ranging from 5 to 130 fps (huh?)
That is, 130 indoors and 5, for example, in a crowded Orgrimmar / Booty Bay area.
Eve-online runs totally crap, 10fps and crashes after a while.

I know im no experienced user, but i really wanna go full-time linux and am wondering how much less hassle nvidia would be? 

I am really puzzled about the performance jumping so much.

PS: Yes, i've read many ATI-related posts on other forums. Many people seem to get WoW for example running very well on ATI cards. Don't tell me this is distro-related too?

---

### Post by pay on 2006-09-26
If I had an x1900gt I wouldn't get a new card... glxgears isn't exactly the most accurate benchmark program. How does Warcraft run on windows? I know that running Warcraft in Wine with an Ati card requires a patch but Cedega would be different.

---

### Post by SonnyBonds on 2006-09-26
Performance in Windows is, well... awesome ~60-120fps (40ish on raids:-)

I tried fgl_glxgears now, and that one outputs about 1500fps, but if they are not accurate i won't be starting at them any longer.

*sigh*

---

### Post by pay on 2006-09-26
You can expect a performance hit from using non-native games through wine because the games are after all designed for Windows. Try a patched wine.

---

### Post by SonnyBonds on 2006-09-26
patched wine? So you want me to ditch cedega, or somehow patch the wine-part of it.

Sorry, as said, i'm new to this ](*,)

---

### Post by pay on 2006-09-26
No don't ditch Cedega, after all you paid good money for it. Sorry I cant really help you with Cedega since I've never bought it. I'm just saying install wine alongside of it and see how wine works with it. Is Warcraft officially supported by Cedega?

---

### Post by SonnyBonds on 2006-09-26
Ah, ok.
Yeah it's officially supported, but the transgaming forums/support doesn't really help- they all come to the same conclusion that ATI just blows :p

---

### Post by pay on 2006-09-26
Haha... Helpful. My Ati card runs doom3 very nicely under linux... but thats a native game...

---

### Post by SonnyBonds on 2006-09-26
Ok, did some xorg.conf tweaking.
Now i am getting reasonable framerates in WoW.
(20fps in a crowded area aint that bad)
I peaked 140fps staring at a wall ;D

Next up, getting eve-online to work.

---

### Post by pay on 2006-09-26
What xorg.conf tweaks did you use?:)

---

### Post by SonnyBonds on 2006-09-26
i added Option "KernelModuleParm" "agplock=0" and "locked-userpages=0" to the Device section.

I have no clue what those actually do, but it worked for me.
(atleast for WoW, everything else still blows)

---

### Post by pay on 2006-09-26
Cool. I'll look into it after i get some sleep.

---

