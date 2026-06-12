---
title: "[SOLVED] Going bald .. Only headphones in gnome-volume-control"
date: 2008-09-19
forum: Multimedia Software
---

### Post by Kanucker on 2008-09-19
I have a gigabyte ep43-ds3l motherboard with a realtek acl888 chipset on it for sound.

The chipset has 3 jacks ( 1 front 2 back) with 6.1 sound. (for all the good it's doing me)

My headphones work fine, but I can't seem to get the jacks in the back to detect.

If I go in gnome manager, all I get is headphones, no speaker. (I'm guessing I should have 2)

I've got 2 inputs plugged in on the speakers (a TV and a sound system) and neither of them works (they both work fine in windows)

I've tried the codex update from realtek, I've added the 3jack 3-dig in my alsa config file (and a number of others to try it out)

I've installed all the alsa and pulse audio files.

I'd love to solve this, but no one seems to have the same problem as me.

Thanks in advance to anyone who can offer ideas for the troubleshooting.

---

### Post by markbuntu on 2008-09-19
Are you talking about when you right click on the speaker on the top panel and go to Open Volume Control?

---

### Post by Kanucker on 2008-09-20
Hi Mark,

No, I mean when I open gnome-volume-control from the terminal. Anyways, I managed to find the fix. I added everything in gnome volume control, and maxed all the sliders. Turns out my speakers where attached to the surround slider, which was minimized, and when I slid it up, my volume came back.

Hope this can help someone with a similar problem.

Cheers.

---

### Post by markbuntu on 2008-09-20
Ok, good. I am glad you got that figured out on your own, even better you marked the thread as solved. So many people don't do that.....

---

