---
title: "No video only sound in VLC / movieplayer"
date: 2009-06-15
forum: Multimedia Software
---

### Post by tetsuoharry on 2009-06-15
hello!

Problem I've got is movieplayer, kaffiene have stopped playing video but do play sound. VLC I can get to play video and sound when I change the video output module to X11 otherwise it behaves as above.

I've been trying to get wine to play ball recently and had to downgrade my nvidia drivers from 185.xx to 180.xx and I'm guessing this has caused the problem.

I've tried reinstalling xine but that didn't help and I'm a bit stuck. I also have the all restricted codecs.

---

### Post by tetsuoharry on 2009-06-15
Problem fixed! lol

all that was required was for the movie player to be reinstalled along with gstreamer couldn't tell you why but it works.

---

### Post by chaosdesigner on 2009-10-14
I pretty much have the same Problem you have. No Video Output with kaffeine and totem, only sound. First i had this with vlc but then like you said, X11 works fine. Now you said you solved it by just reinstalling the movie player and gstreamer, didnt work out for me ..

I removed and reinstalled totem-gstreamer and gstreamer0.10-ffmpeg. Am i missing something here?

Thank you for your help.

---

### Post by hellblazer on 2009-10-15
I've had a similar problem and solved it by installing the correct codecs.
Have a look at [this page]("https://help.ubuntu.com/community/RestrictedFormats") for more details on installing the correct packages.

---

