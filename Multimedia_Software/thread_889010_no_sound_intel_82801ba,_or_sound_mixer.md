---
title: "no sound intel 82801ba, or sound mixer"
date: 2008-08-13
forum: Multimedia Software
---

### Post by Foudre on 2008-08-13
Randomly last night there was no sound on my friends computer after moving it from one room to the other. I tried following the stickied guide but it isn't helping me much.

on kubunutu hardy

I try to even do alsamixer and it return 
```

raamroc@raamroc-Sexbox-2000-Mark2:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```
the kmix icon in system tray says can not find mixer

what made the guide not work for me is after getting to where he suggested 

```

sudo modprobe snd-

```

and hitting tab nothing shows up as possibilities, i even tried reinstalling alsa to no avail.

I tried popping the live cd back in and sound worked, so the soundcard still works.

idk what to do at this point besides reinstalling kubuntu, which would take a while, i'd like to avoid doing this is if possible. if any one knows what might be wrong, or a way to solve this with out reinstalling that'd be great.

---

