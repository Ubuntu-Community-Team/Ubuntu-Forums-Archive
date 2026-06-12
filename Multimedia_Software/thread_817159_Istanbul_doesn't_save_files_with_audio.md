---
title: "Istanbul doesn't save files with audio"
date: 2008-06-03
forum: Multimedia Software
---

### Post by cogadh on 2008-06-03
I'm trying to use Istanbul to record some Wine gaming sessions and I can't get it to save the file if I have audio enabled. Without audio, it prompts me almost immediately to name and save the file, but if audio recording is enabled, the tray icon switches to the hard drive icon as if I am going to get the option to save the file, but the save dialog never pops up and I end up having to kill the process (yes, I waited quite a while before killing it). When I try running Istanbul from the terminal with debug output, no errors are reported at all. I have checked /tmp and when audio recording is enabled, a silent video file is created there, but there doesn't appear to be any separate audio track. System specs, just in case:
Kubuntu 7.10
Pentium 4 HT 3.0 GHz
2GB RAM
Creative Audigy LS
GeForce 7600GS 256MB
Istanbul and all dependencies installed from repository, except Theora library. Manually updated that to 1.0beta3 in an attempt to correct the problem.

EDIT - Well I found a [Gnome bugzilla report](http://bugzilla.gnome.org/show_bug.cgi?id=430151) on this problem that included a hack to get around the lockup, but I'm still stuck with a video file that has no sound. Anyone have any pointers/suggestions for that issue?

EDIT 2 - Ack, I'm an idiot. Istanbul cannot record system sounds, when you enable recording sound, it is trying to record from your microphone #-o
Well, silent movies are better than no movies at all (for now). Anybody know of a decent desktop session recorder that also records system sound?

---

### Post by wolfen69 on 2008-06-03
as far as i know, istanbul will not record audio from the desktop. only audio from an input source.

---

### Post by cogadh on 2008-06-03
Yeah, I was discovering that while you were posting. Know of any session recorders that do record system sound?

---

### Post by wolfen69 on 2008-06-03
no i dont. if you have a mic, you can record whatever is coming thru your speakers though.

---

### Post by cogadh on 2008-06-03
Unfortunately, I have a crappy mic and my PC is not in the best location for recording (open windows and a TV very close by). Unless anyone has any other suggestions for a session recorder (already tried recordMyDesktop, not as good as Istanbul on the video quality), I'll just have to make silent films.

---

### Post by adking80 on 2008-11-11
> **cogadh said:**
> Unfortunately, I have a crappy mic and my PC is not in the best location for recording (open windows and a TV very close by). Unless anyone has any other suggestions for a session recorder (already tried recordMyDesktop, not as good as Istanbul on the video quality), I'll just have to make silent films.

Same problem here.  Seems really weird to me that you can't just select an audio stream to record.

---

