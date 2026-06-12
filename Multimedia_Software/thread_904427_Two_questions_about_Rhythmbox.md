---
title: "Two questions about Rhythmbox"
date: 2008-08-29
forum: Multimedia Software
---

### Post by potiphera on 2008-08-29
Two questions about Rhythmbox:

a) how come when I import .wav files, they play in a somewhat glitchy manner?  I.e., they'll play all the way through, but the timbre sounds like there are some digital glitches happening (this occurs with all .wav files I've opened in Rhythmbox, and the same files sound fine in Audacity and a variety of other programs).

b) how come when Rhythmbox can't find the album art for mp3s on my computer, it shows me the cover of a Bee Gees tribute album?

Thanks!

---

### Post by potiphera on 2008-08-30
(bump)

---

### Post by potiphera on 2008-09-01
(bump) Anyone?

---

### Post by minky311 on 2008-09-01
You can try going into /home/yourname/.gnome2/rhythmbox/covers and deleting the album covers that are incorrect and see if it displays the right one next time you play the artist. Or just find the album cover yourself and copy it into that directory.

As for the .wav file could you start rhythmbox in the terminal Applications->Accessories->Terminal by typing in rhythmbox and then posting the output.

---

### Post by potiphera on 2008-09-02
Thanks for the response!  Still playing around with the covers thing, but I just tried running Rhythmbox from the terminal.  Just typing rhythmbox doesn't give me any output in the terminal, but man rhythmbox told me that I can do rhythmbox -d for debug output.  So I tried that, but there's way too much information that way.  It says you can do -D to match specific strings, but I don't know what strings I would be looking for.

---

