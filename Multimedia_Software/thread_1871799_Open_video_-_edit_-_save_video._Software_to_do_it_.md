---
title: "Open video - edit - save video. Software to do it easily?"
date: 2011-10-29
forum: Multimedia Software
---

### Post by The Bright Side on 2011-10-29
Hey guys!

This is a total noob question, and I hope you can help me with it. I have a very simple task I want to do, but unfortunately, the video editors I have checked out so far are far too sophisticated for it.

I have the DVD "I'm only looking" by INXS, and I am annoyed by the fact that between the music videos, there are small clips of the band members introducing the songs.

So I have been ripping the music videos off the DVD to MKV files, keeping the DTS soundtrack intact (lossless). Now, since I am really only interested in the 5.1 mixes of the songs and hardly watch the videos, what I'd like to do next is cut down the video "Taste It", which has a bit of movie at the beginning.

So here's what I'd like to achieve:

[LIST]
[*]Open MKV file
[*]Delete the first 1:38 minutes
[*]Save and close MKV file
[/LIST]

Do you know if there's a software that does it? Without compromising the video's sound quality?

The editors I've tried all open "Projects", into which I can import the clips, and then edit them together etc, and export them again - but only in stereo?! :-(

Thanks!

---

### Post by little_penguin on 2011-11-01
Here are a few possibilities:
 
Avidemux
Openshot
Kino
Cinelerra
Jakasha
Lives

---

### Post by aeiah on 2011-11-01
id go with avidemux. you can crop without re-encoding and the whole process is pretty simple. crop to keyframes, though.

---

### Post by The Bright Side on 2011-11-01
A-ha! Thanks guys. I will try this.

I have been tinkering with Avidemux (which seemed like the best one for me, too), and it did everything very well except saving afterwards. It gave me an error message at first saying that the first frame is not a keyframe, and I should move the A marker, so I did that and then it "saved" my file, giving me a "success" message.

And then I had a 0 bytes big mkv file.

I will retry when I have some more time, this time *cropping* to keyframe.

---

### Post by little_penguin on 2011-11-02
If your Avidemux problem editing Matroska files isn't resolved, try Mkvtoolnix and Mkvtoolnix-gui, mentioned here. See Ron999's post:
 
[http://ubuntuforums.org/showthread.php?t=1477820](http://ubuntuforums.org/showthread.php?t=1477820)

---

