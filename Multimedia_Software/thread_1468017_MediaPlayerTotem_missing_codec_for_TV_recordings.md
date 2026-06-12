---
title: "MediaPlayer/Totem missing codec for TV recordings"
date: 2010-05-01
forum: Multimedia Software
---

### Post by BrokeMahPC on 2010-05-01
I am using Ubuntu 10.04 and Me TV 1.1.2 to record DVB-T television which saves the file as an mpeg.
when you open that mpeg with Movie Player (Totem 2.30.0) it asks to search for a codec, does not find it - details:
private/x-dvbsub decoder
It will play the file but you can't scroll through the video using the slider bar or picture goes black.
Running the file in terminal gives:
$ totem --play /media/sdb6/Buzzcocks.mpeg
** Message: Missing plugin: gstreamer|0.10|totem|private/x-dvbsub decoder|decoder-private/x-dvbsub (private/x-dvbsub decoder)

VLC plays the files with no problems?
I have restricted extras and w32codecs.

---

### Post by BrokeMahPC on 2010-05-01
I got an answer from the developer:
Me-TV encodes the subtitle streams in the recordings and totem does not know what to do with it.
Play these files with VLC and you will not have a problem.

---

### Post by piginabox on 2010-07-15
Solved?
It's ridiculous that the solution to this is to use a different player. Even when Totem plays the DVB mpeg recordings it doesn't let you skip forward without it freezing.
Can you change this thread to being UNSOLVED, please?

---

### Post by Skybinary on 2010-12-28
Solved?
That is not how i see it either, shelved more like.

---

