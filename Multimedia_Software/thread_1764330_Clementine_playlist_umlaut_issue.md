---
title: "Clementine playlist umlaut issue"
date: 2011-05-21
forum: Multimedia Software
---

### Post by tom957 on 2011-05-21
First off, I'm running Clementine 0.7 r3213 on Natty w/ classic desktop. I love Clementine and won't let this keep me from using it; It's just kind of annoying.

Whenever I queue up any songs from an album or artist whose name contains an umlaut, it gets double-queued (attachment #1). Fortunately, only one copy of each song plays as it should and the other is greyed out after it's skipped. I've retagged all my songs with EasyTag, and they all work fine in Rhythmbox and Banshee. When I go to edit the track info in Clementine, the greyed-out file has the diamond-shaped icon with a question mark instead of the umlautted character (attachment #2) even though it doesn't actually exist in the album's folder. The correct file shows the correct filename (attachment #3). A full library rescan doesn't fix anything.

Thanks for any help.

---

### Post by tom957 on 2011-05-22
Bump!

---

### Post by ivanovnegro on 2011-05-25
Remove manually the folder where are the tracks in outside of your music folder from the file browser and put it back into the music folder.
Also enable the monitor library function.
Clementine has a weird behavior updating the music folder.
[Here]("http://code.google.com/p/clementine-player/wiki/LibraryScanning") some read.
You should also put any issues on Clementine's bugtracker on Google Code Clementine.

---

### Post by tom957 on 2011-05-30
Well, I just decided to delete my .Clementine folder. After readding my library everything showed up without a hitch. Thanks for the reply, ivanovnegro.

---

