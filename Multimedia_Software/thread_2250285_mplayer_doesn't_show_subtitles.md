---
title: "mplayer doesn't show subtitles"
date: 2014-10-27
forum: Multimedia Software
---

### Post by VMC on 2014-10-27
lubuntu gnome-player "mplayer" doesn't show subtitles embedded in MKV file. Installed VLC and it does show subtitles. The option to display subtitles "V" is turned on. The MKV was created using handbrake.

I searched for anything relating to this issue, and changed .config file, but still no subtitles.

---

### Post by VMC on 2014-10-28
Installing smplayer fixed the issue. I'd like to know what smplayer used to add subtitles to mplayer, since its the frontend.
In any case, I'll mark this solved, since what I wanted was subtitles for mplayer.

---

### Post by andrew.46 on 2014-10-28
> **VMC said:**
>  I'd like to know what smplayer used to add subtitles to mplayer, since its the frontend.

Have a look at Options --> View Logs to find a few hints...

---

### Post by SeijiSensei on 2014-10-29
My guess is they are "[Advanced Substation Alpha]("http://en.wikipedia.org/wiki/SubStation_Alpha#Advanced_SubStation_Alpha")" subtitles.  As Andrew suggests look in the log file for the switches like "-ass".

---

