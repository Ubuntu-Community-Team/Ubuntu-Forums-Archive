---
title: "Flash video lag"
date: 2011-03-08
forum: Multimedia Software
---

### Post by groogrux on 2011-03-08
Hi everyone.  I just recently installed Ubuntu 10.10 (32 bit) alongside Windows 7 (64 bit) and everything went well.  The only problems I have had to deal with were audio problems. Sound did not come from my headphones when I plugged them into the side panel on my Dell Studio XPS 1647.  I found an ehow article telling me how to reinstall my sound drivers (removing alsa and enabling oss). I followed along foolishly, and encountered an error when entering the code into the terminal.  I don't believe the process completed because I still had sound coming from my internal speakers, and I did not follow the "blacklisting" of alsa step.  So I did a little more research and found that I had to add a line into a file relating to my drivers.  After doing so, my functionality was restored.  Now, I'm noticing a little trouble with Youtube videos (as well as some other flash-type videos) regarding sound.  When i click play/pause, there is about a second delay before the sound enables/disables.  The video starts and stops instantly.  Could it be a complication from the drivers I installed/uninstalled using the terminal earlier?  Also, is there a way to check to see if i have more than the necessary audio drivers installed (like alsa and oss, or something like that? I've seen evidence of pulse audio and alsa whilst browsing my OS, but I wasn't sure how to interpret it). Thanks a lot!

---

### Post by groogrux on 2011-03-09
bump

---

### Post by groogrux on 2011-03-10
anyone have any ideas?

---

### Post by groogrux on 2011-03-14
Shameful bump :/

---

### Post by tincansandtwine on 2011-03-20
This, as far as I can tell, is an issue with pulseaudio. It is possible to purge it, but that causes a number of issues, primarily that it uninstalls ubuntu-desktop, which stops updates from happening.  It also removes the volume indicator app, which is annoying, though resolvable.  Instructions for doing so are [here]("http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html").  Be warned, it can cause other strange issues.  But it will probably resolve the issues with Flash that you are having.  It may also improve performance with other programs.

I hope that it's figured out how to better implement pulseaudio, or an alternate is found.  If it weren't for the updates thing, I would definitely keep pulseaudio removed.

---

