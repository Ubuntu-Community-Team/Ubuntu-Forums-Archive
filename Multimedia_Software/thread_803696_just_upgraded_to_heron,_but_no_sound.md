---
title: "just upgraded to heron, but no sound"
date: 2008-05-22
forum: Multimedia Software
---

### Post by jake23 on 2008-05-22
I just upgraded from edgy eft to heron.  I did a clean install rather than merely upgrading on top of eft.

Everything is working great, except for sound.  I'm clueless here.  Any suggestions?  Thanks!

---

### Post by wolfen69 on 2008-05-22
in terminal:
```
lspci
```
we need to know what sound card you have.

---

### Post by Novus on 2008-05-22
I had sound problems too.. for me it was simple :) check System > Preference > Sound. Check that pulse audio is selected.
and Xchat refused to play sound at events, I just needed to set paplay as external program.

---

### Post by Bubba64 on 2008-05-22
> **wolfen69 said:**
> in terminal:
```
lspci
```
we need to know what sound card you have.

This lspci code is the best way to identify your sound card and other info that will allow this poster to direct you. I have pulse audio disabled on my computer that is not the answer.

---

### Post by jake23 on 2008-05-22
> **Novus said:**
> I had sound problems too.. for me it was simple :) check System > Preference > Sound. Check that pulse audio is selected.
and Xchat refused to play sound at events, I just needed to set paplay as external program.

Thank you Novus!

I switched over to pulse audio and I now have sound!

I didn't have to do that when I installed edgy eft, so I was dumbfounded when I did the clean install yesterday.  This is the first time I've upgraded since being converted to ubuntu.  Thanks again!

---

### Post by Bubba64 on 2008-05-22
> **jake23 said:**
> Thank you Novus!

I switched over to pulse audio and I now have sound!

I didn't have to do that when I installed edgy eft, so I was dumbfounded when I did the clean install yesterday.  This is the first time I've upgraded since being converted to ubuntu.  Thanks again!

I stand corrected, usually the problem is the sound card. If you have problems with types of programs playing install Ubuntu restricted extras from add remove along with the gstreamer and vlc and ffmpeg stuff.

---

