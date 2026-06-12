---
title: "[SOLVED] Firefox prevents movie playback"
date: 2008-07-22
forum: Multimedia Software
---

### Post by R3N3G4D3 on 2008-07-22
My current system is as follows:
Intel Core 2 Duo 1.86 GHz
2GB Mushkin memory
On-board GMA950 video (set to 224 MB shared memory)
1920x1080 resolution for monitor
Default Ubuntu interface (Gnome)
Compiz disabled

I can play movies fine in MPlayer or Totem, I also have Firefox flash plugin installed, which works correctly as well. The problem occurs when I have firefox open on the background with at least 1 flash movie or advertisement open on the background (even if not currently playing) and try to play a movie on Totem or MPlayer. The movie freezes on MPlayer (although MPlayer itself does not freeze), on Totem the movie plays extremely slowly with no sound. This is similar to the issue I had when I just installed Ubuntu when I couldn't play movies at all (even without Firefox running). The issue seemed to be that by default Ubuntu was only using something like 12 MB of memory for video. But now that I'm using 224 MB I see no reason for the issue to occur, even with firefox having flash open on the background (especially if the flash movie isn't playing and Firefox is minimized). This is an odd issue that I have not experienced even with my old GeForce Ti4400 card which only has 128 MB memory (although it is dedicated).

Sometimes it seems that even pages without Flash content in them cause this behavior in MPlayer and Totem. I have learned to deal with the issue by closing Firefox when playing a movie, and closing movie player when using Firefox (even when a movie is paused, Firefox refuses to load new Flash content). However, I'm frustrated having to do this, and would prefer to be able to run both at once.

---

### Post by Octagonal on 2008-07-22
I can confirm that something similar is happening to me as well--possibly with a recent update?  

I would have firefox open with flash content and attempt to open amarok which would hang after trying to start playing music.  But if firefox and amarok are closed--opening amarok first seems to allow firefox to work with flash fine for me.

This definitely seems like an issue with flash and pusle audio.

---

### Post by R3N3G4D3 on 2008-07-22
Octagonal, thanks for pointing me to the correct source of the problem, I have finally solved it. My problem was indeed due to the sound and not video as I originally thought. As a positive side effect, my sound quality in Linux improved as well, the bass was non-existent before.

Here is the link that explains how to fix the sound in other applications while flash content is open (it will also equalize the sound, making it seem less flat):
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
As a side effect of the above solution, however, the sound in flash will completely disappear. To remedy this new problem, follow the .deb located here:
[http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/)

---

### Post by Octagonal on 2008-07-23
excellent, I'll give that a try.

---

