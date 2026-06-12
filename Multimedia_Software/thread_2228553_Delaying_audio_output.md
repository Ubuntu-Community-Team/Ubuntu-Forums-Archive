---
title: "Delaying audio output"
date: 2014-06-08
forum: Multimedia Software
---

### Post by Accidus on 2014-06-08
I want to delay the audio output of a particular application to sync audio and video. I'm following up on the following thread: 
[http://ubuntuforums.org/showthread.php?t=1189559](http://ubuntuforums.org/showthread.php?t=1189559)
though I'm happy to start a new solution from scratch.

(The script in the thread won't work as it cannot find pygst, so I ported it (attached) to PyGI as in [http://jderose.blogspot.co.uk/2011/09/porting-gstreamer-apps-to-pygi.html](http://jderose.blogspot.co.uk/2011/09/porting-gstreamer-apps-to-pygi.html) )

This script captures the sound from a line input. I would like to change this to input from a specified application. I think I need to change line 23, which says (after porting to GI):
```

   self.audiosrc = Gst.ElementFactory.make("alsasrc", "audio")

```

But I don't know what to change it to. Can anyone point me in the right direction please?

---

### Post by tgalati4 on 2014-06-08
This is a super cheesy way to do it:  [http://ubuntuforums.org/showthread.php?t=1576554&highlight=play+rec+pitch](http://ubuntuforums.org/showthread.php?t=1576554&highlight=play+rec+pitch)

The example changes pitch in real-time, but you can change the switches to impose a delay.

---

