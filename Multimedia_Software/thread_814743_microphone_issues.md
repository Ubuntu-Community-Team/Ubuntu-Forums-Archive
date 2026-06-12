---
title: "microphone issues"
date: 2008-06-01
forum: Multimedia Software
---

### Post by werries on 2008-06-01
Skype doesn't work with microphone. that was my clue.

So I tried using the standard gnome-sound-recorder.
I record, and then stop. When i try to play, this pops up as a message "Internal GStreamer error: state change failed.  Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer."
and then terminal says
```
ERROR: Internal GStreamer error: state change failed.  Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer.
DEBUG MESSAGE: gstswitchsink.c(176): gst_switch_commit_new_kid (): /playbin/abin/sink:
Failed to set state on new child.
```
and when i hit "close" on the error, this shows in terminal
```
(gnome-sound-recorder:8028): GStreamer-CRITICAL **: 
Trying to dispose element fakesink, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.
```
I don't know if i just haven't set it up right, but no sound is coming.

---

### Post by werries on 2008-06-02
bump?

---

### Post by werries on 2008-06-03
alright it doesnt give me the error anymore.
but it still doesnt actually play sound. it will record, and then when i stop and hit play, it goes through the file, no errors, and simply doesnt make any noise. also, my webcam seems to work in cheese but not camorama. camorama says it cant connect to /dev/video0, and cheese does, even though my default cam is set as /dev/video0 and works in cheese via that camera, considering i have no other webcam

---

### Post by werries on 2008-06-04
bump after another 24 hour wait.

---

### Post by werries on 2008-06-08
three day wait.
it really sucks not being able to use the microphone on my built-in webcam.

---

### Post by werries on 2008-06-15
bump! does anyone know anything about properly getting the webcam/microphone to connect? maybe its a setting? :(

---

### Post by Isaacgallegos on 2009-08-13
I found that it's very hard to get a response for help on this forum.

---

### Post by Isaacgallegos on 2009-08-16
bump

---

