---
title: "Port sound through mic input and out of speakers"
date: 2011-01-31
forum: Multimedia Software
---

### Post by dd1linux on 2011-01-31
Hi all, I am sure this has been asked repeatedly, but I cannot find it anywhere.  I have my TV's sound plugged into my mic input, and can see it registering a signal but I cannot get it to play out through my speakers.  I have done this on older versions, but I cant remember the name of the mixer that allowed me to do it.  Any help would be greatly appreciated, and I apologise if this is redundant.

---

### Post by dd1linux on 2011-01-31
Im pretty sure it was aumix, but when I try to run it, it says:

aumix:  error opening mixer: No such file or directory

even though i just installed it via apt-get install aumix

---

### Post by dd1linux on 2011-01-31
Ok, I downloaded Pulseaudio Volume control, and I can see perfectly the signal coming in through mic 1.  But there is no option to have that sound come out through the speakers.  PLEASE someone help!

---

### Post by dd1linux on 2011-01-31
FIXED:

I downloaded xfce4-mixer, and it had all I needed. I am still at a loss as to how the sound works in linux (also, oss, etc.)  If anyone has any helpful links, please post them.  At least if anyone runs across the same problem I had, they'll know how to fix it!

---

### Post by inobe on 2011-02-01
start here [http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture](http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture)

---

### Post by squarethumps on 2011-02-28
> **dd1linux said:**
> FIXED:

I downloaded xfce4-mixer, and it had all I needed. I am still at a loss as to how the sound works in linux (also, oss, etc.)  If anyone has any helpful links, please post them.  At least if anyone runs across the same problem I had, they'll know how to fix it!

I know the thread says solved, but the solution isn't clear to me.
When you say it had all you needed ... what on that did you manipulate to get the sound to come through the speakers?

I have everything on and everything turned up.  

Also, as far as I can tell, xfce4-mixer is just a prettier implementation of alsamixer.  I didn't really see the advantage.

I appreciate all the help.

Thanks.

---

