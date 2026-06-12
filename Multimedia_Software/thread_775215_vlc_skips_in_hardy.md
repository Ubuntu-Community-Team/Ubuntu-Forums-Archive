---
title: "vlc skips in hardy"
date: 2008-04-29
forum: Multimedia Software
---

### Post by djrobthaman on 2008-04-29
Hi everyone,

since installing hardy, I've noticed that vlc, and any other video player for that matter, has jumpy video outpu when I set it to fullscreen.  This even happens when I reboot and happens under both compiz and metacity so it can't be a memory problem.

I wish I could be more specific, but I don't know what else I could say about it.

I'm using ati propriety drivers for an ati x1300.

---

### Post by quixotic-cynic on 2008-04-30
Does it matter what kind of file your are playing back (.mkv, .avi, DVD, etc)?

---

### Post by djrobthaman on 2008-04-30
I'm not 100% sure.  I was trying to play strictly .avi files last night (different encodings though).  However, I found a few posts today that say it's a general problem.  Apparently with hardy, xglserver is not needed to run compiz and a few people have solved the problem by uninstalling it .  Others say doing that solves the jumpy video problem but makes the video pixelated.  I couldn't find anything about a general solution being found.  So I'm going to try uninstalling xgl when I get home today.

I'll also try other types of videos, just to make sure it is a general video problem on my end.

---

### Post by quixotic-cynic on 2008-04-30
[I was asking because Hardy trashed my ability to play .mkvs and I know a bit about that problem now - I don't know about the more general problem though, so my apologies...]

---

### Post by djrobthaman on 2008-04-30
Yeah... I tried a couple other files and it looks like it's a general problem.  There's also a dotted white-ish line to the right when the video's in full screen mode which is strange.

But I actually tried uninstalling xgl and compiz definitely did not work for me after that.  I'm not sure if I had to uninstall and reinstall compiz so that it could adjust or something, but that didn't work.

Anyway, thanks for trying to help.  I guess I'll just troll around some more and see if I can find a fix.

---

### Post by acrane1 on 2008-05-05
Yeah I am having a problem with my media players to. For my it is pretty much only MKV files. The larger the MKV the worse it gets. It is really annoying since all my favorite movies are in MKV due to the fact there HD. Any suggestions on a fix

---

### Post by djrobthaman on 2008-05-05
I fixed most of my problem (the performance is still not 100% but now the picture looks good) by changing the ouput module to x11.  I hope this helps you guys.

---

### Post by quixotic-cynic on 2008-05-07
Unfortunately switching to x11 didn't fix it here.

The basic problem afaik is that my pc is using just my cpu to render the images, rather than the gfx card too.

Now, this was not a problem in gutsy - my player could just about cope with mkvs and avis where no problem. In hardy, however, mkvs play very badly.

The 'radeon' driver works 2d only with my card (mentioned in the manual page) and fglrx also seems to hate my pc.

---

### Post by Wyld on 2008-05-15
On a hunch, I set the output to OpenGL, and now, VLC won't open at all.

:(

Hmmmmm...

---

### Post by soxs on 2008-05-21
Wrong thread -.- sry

---

### Post by hp79 on 2008-09-28
I found out when the hard disk is a little busy, the movie never skips frames. I moved to 2nd desktop area, and play mp3 player with 0 volume in loops, and watch a movie in 1st desktop area. It's not skipping any more.

I found out while copying 10 GB's worth of data to another laptop on local network, and the movie never skiped frames. Started skipping once copying was done, and HDD was idle.

---

