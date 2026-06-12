---
title: "How can I use Kazam Screencaster In Terminal?"
date: 2011-03-24
forum: Multimedia Software
---

### Post by XsheepX on 2011-03-24
I want to use Kazam Screencaster to record my vids, but it goes to the tray when you record, and I don't use a panel (my desktop is the very definition of minimalistic. I just use all shortcuts and terminal.)

So, my question is, is there any way I can record/stop it with the terminal?
Thanks in advance :)

---

### Post by XsheepX on 2011-03-24
Never mind, I figured it out. When I ran it through the terminal, I noticed it said "Press 'q' to stop ffmpeg"
So, when I was done, I stopped it by pressing Q in the terminal, and found the video saved automatically in the tmp folder.

Hope this helps anyone else, because I couldn't find a thing about it on Google.

---

### Post by Script Warlock on 2011-03-24
ffmpeg is capable

ffmpeg -f x11grab -s 1024x768 -r 15 -i :0.0 -s 1024x768 -r 15 -sameq sample.avi

---

### Post by gabak on 2011-12-28
i run from terminal kazam and then after recording i press q and nothing.
it did nt stop either record anything at /tmp
what i m doing wrong?

> **XsheepX said:**
> Never mind, I figured it out. When I ran it through the terminal, I noticed it said "Press 'q' to stop ffmpeg"
So, when I was done, I stopped it by pressing Q in the terminal, and found the video saved automatically in the tmp folder.

Hope this helps anyone else, because I couldn't find a thing about it on Google.

---

