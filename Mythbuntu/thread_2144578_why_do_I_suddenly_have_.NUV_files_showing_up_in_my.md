---
title: "why do I suddenly have *.NUV files showing up in my /recordings folder?"
date: 2013-05-12
forum: Mythbuntu
---

### Post by grunge09 on 2013-05-12
I have *.NUV files showing up in my /recordings folder within the last 2 weeks.  

I have a HVR-2250,and 2 PVR-500 video cards sing dual analog tuners only.  All setup as IVTV in the backend.  When I installed the 2nd pvr-500 my system freaked out and I had to revoed all cards from the backend and re-install them.  the 2250 showed up as IVTV and it seemed to work fine so I left it alone.  

Now I have been tinkering with turning on transcoding,since it has been OFF since I installed MYTHTV a few years ago.   Did I do somethjing on tgeh front end opr backend to have ti create NUV files instead of MPG files.  

and this is again only within the last few weeks this is happening.  

What did I do to cause this and can it be fixed?

Thanks in advance.

---

### Post by hansdown on 2013-05-12
Hi 
grunge09.

That is a mythtv file.

Mythtv, mythnuc2mkv, and vlc should open these.

Please see screenshot.

[ATTACH=CONFIG]242538[/ATTACH]

---

### Post by grunge09 on 2013-05-13
I realize it is a mythtv file, but back to the original question, why is it suddenly showing up after 3 years of mythtv use?

---

### Post by Rotak on 2013-05-13
Aren't analog recordings supposed to be NUV files while digital MPEG recordings are recorded as MPG files (MPG-TS format)? I am not sure if this is an error.

---

### Post by tgm4883 on 2013-05-13
> **grunge09 said:**
> I realize it is a mythtv file, but back to the original question, why is it suddenly showing up after 3 years of mythtv use?

> **grunge09 said:**
> I have *.NUV files showing up in my /recordings folder within the last 2 weeks.  

I have a HVR-2250,and 2 PVR-500 video cards sing dual analog tuners only.  All setup as IVTV in the backend.  When I installed the 2nd pvr-500 my system freaked out and I had to revoed all cards from the backend and re-install them.  the 2250 showed up as IVTV and it seemed to work fine so I left it alone.  

**Now I have been tinkering with turning on transcoding,since it has been OFF since I installed MYTHTV a few years ago. **  Did I do somethjing on tgeh front end opr backend to have ti create NUV files instead of MPG files.  

and this is again only within the last few weeks this is happening.  

What did I do to cause this and can it be fixed?

Thanks in advance.

That is why.

> **Rotak said:**
> Aren't analog recordings supposed to be NUV files while digital MPEG recordings are recorded as MPG files (MPG-TS format)? I am not sure if this is an error.

Analog recordings are only NUV files if the analog card doesn't contain a hardware encoder. Digital recordings are recorded in whatever they come as (be it MPEG2, MPEG4, etc)

---

