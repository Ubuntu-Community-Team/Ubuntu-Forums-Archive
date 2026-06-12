---
title: "MKV End-Of-File"
date: 2009-04-07
forum: Multimedia Software
---

### Post by spongypants23 on 2009-04-07
Hi guys. Having a bit of trouble playing videos that are using the MKV container.

It seems that when I try to play them, the video stops playing abruptly. This happens in any media player. I've tried Totem, VLC, and MPlayer. (All from the Ubuntu repos.)

Usually the message is something along "End of file" or "End of stream" or something along those lines, even though the timer says something like 12:03/42:30. Clearly the video isn't at it's end. This always happens at the same point in the video, and sometimes at multiple points.

Any ideas/help/fixes?

---

### Post by dacorr on 2009-04-07
sound like the index is messed up, the only thing i can think of is to install mencoder(Terminal Based) and re-encode the file to an AVI or somthing

Dac

---

### Post by spongypants23 on 2009-04-07
Though it's not just the one file. It's any .mkv file I try to play.

---

### Post by andrew.46 on 2009-04-07
Hi ,

Sounds a little curious. Have you tried remuxing one of the files with mkvmerge? There is a nice gui that makes it a drag and drop undertaking:

```

andrew@skamandros:~$ apt-cache search mkvmerge
mkvtoolnix - Set of command-line tools to work with Matroska files
mkvtoolnix-gui - Set of tools to work with Matroska files - GUI frontend

```

This should eliminate any problems with badly muxed matroska containers I would hope :-).

Andrew

---

### Post by rydell on 2010-02-21
I've been having this problems for a _long_ time, but never got around to looking for help for it. This is because it seems that hardly anyone has encountered it.
I have the same problem on both Debian (on x86_64) and Ubuntu (i686), in any of: mplayer, totem, vlc. The movie players simply reach EOF at certain points in mkv files, and exit. Each mkv has its own point(s) in the file, which _always_ causes this. In order to watch them, once I reach this (these) point(s), I have to restart the player and then manually skip over the part in question (and hope that there aren't any other such points in the video).
This might be a problem with the files, but on Windows vlc doesn't exit - it plays the same video files smoothly, so this leads me to think that some shared library that all players are using is somehow at fault here.
But how come hardly anyone's encountered this?

---

### Post by wladyx on 2010-04-30
I have the same exact behaviour, but on Arch Linux...no solution yet.

---

### Post by no2498 on 2010-04-30
try installing smplayer it brings in more codes like 264
open a terminal type smplayer
it tells you how to install it

hope this helps

---

### Post by Tig3rzhark on 2010-05-01
> **spongypants23 said:**
> Hi guys. Having a bit of trouble playing videos that are using the MKV container.

It seems that when I try to play them, the video stops playing abruptly. This happens in any media player. I've tried Totem, VLC, and MPlayer. (All from the Ubuntu repos.)

Usually the message is something along "End of file" or "End of stream" or something along those lines, even though the timer says something like 12:03/42:30. Clearly the video isn't at it's end. This always happens at the same point in the video, and sometimes at multiple points.

Any ideas/help/fixes?
I have tried as well to play .mkv files and I'm still having trouble playing them.  They would start playing for a while and then the video player would either shut down or if I had another video in the playlist, just move on to the next video in the playlist although it hasn't reached the end of the clip.

I've tried finding a way to convert the .mkv file to .avi without success and right now it is giving me a headache.  I would appreciate it if there was a patch made to fix this problem.  In the meantime, I'll just have to stop playing my .mkv files until an update is released.

Unless anyone has any ideas...

---

### Post by Tig3rzhark on 2010-05-01
I tried remuxing some .mkv files in hopes that I could solve the problem but no luck so far.  

I even tried converting the files using Winff and I can't even do that.

We could really use some help here.

---

