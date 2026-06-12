---
title: "Sound recording"
date: 2009-07-02
forum: Multimedia Software
---

### Post by Melcar on 2009-07-02
I'm trying to record the music from a small flash animation using Ubuntu's *Sound Recorder* app.  The problem is that it's not working; nothing gets recorded.  Back with Intrepid when I had just ALSA running, it was as easy as un-muting the appropriate capture slider.

---

### Post by Revolutionary101 on 2009-07-02
Try this:
[How to record sound on Ubuntu 8.04, 8.10, 9.04]("http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-tp2988982p2988982.html")
[http://n2.nabble.com/How-to-record-s...2p2988982.html]("http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-tp2988982p2988982.html")

---

### Post by Melcar on 2009-07-03
Solved it by switching the recording stream to "monitor" using the PA volume controls.  That seems to work with GNOME's *Sound Recorder* which is enough for me.  Can't get Audacity to record, but I'm not to overly concerned with that.

---

