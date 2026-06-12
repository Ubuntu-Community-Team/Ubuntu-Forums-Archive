---
title: "Compiling mencoder with aaac support"
date: 2008-06-11
forum: Multimedia Software
---

### Post by bugs87 on 2008-06-11
Hi!

I'm trying to convert some video files to a format my mp3 player can playback, it needs to be H.264 video + mpeg 4 aac audio in a MP4 container, resolution 320x240. The files I have are all good except for the resolution. Not surprisingly, I'm having several problems here:

1: I've tried re-encoding the files with mencoder. I think I've got the wideo all right, but not the audio. I've tried with -oac faac option, and seemingly everything is fine when encoding, but when it's done, there's no audio on the file.

2: Mencoder can't output to MP4 containers, I've tried dumping the audio and video from the AVI file produced by mencoder, and then muxing them with MP4Box, but it complains about the AAC audiotrack ("Invalid ISO-media")

3: I've also downloaded SIVE, a frontend for mplayer, mencoder and mp4creator, but when I run it it says mencoder is lacking faac support, and that I should re-build mencoder with this support. How do I do this.

Obviously, there's a lot more stuff I don't get, I have tried many different procedures and read a lot of guides, but all I wanna do here is change the resolution of some files, without changing the codecs or format. It seems to me that getting SIVE to work would be the easiest thing for me, but I would be very happy if someone knew a simpler way. (Or, just the right way to do it with mencoder + a mp4 muxer, I've really gotten the taste for mencoder after fooling around so much with it.

I'm running Ubuntu Hardy, the mp3 player's a Sony A829.

I should probably mention that I have one file which actually plays in my mp3player, but it has no sound and it's pretty grainy, and I don't remember how i did it :(

---

