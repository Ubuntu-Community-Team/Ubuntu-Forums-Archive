---
title: "Burning audio cd's?"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by phy5ik on 2006-11-12
I've used both Serpentine and GnomeBaker. Both don't work. Serpentine didn't ever finish "prepping" the cd's for burning, and neither did GnomeBaker. I started GB about an hour before work, went to work (5 hours) and came home to see that the process had frozen at 93%. And this was for PREPPING the cd. I've never even got to the actual burning part. This kind of frustrates me because I don't understand why it's gotta take so much time to do that ****. This was never a problem with nero, or even the standard cd burners that came with Windows. What the **** is up?](*,)

---

### Post by phy5ik on 2006-11-13
bump?:confused:

---

### Post by warjowuch on 2006-11-13
THis is stupid indeed, m aybe you could try brasero. Maybe the real solution lies in installing certain gstreamer-packages. Try launching it from terminal and see what errors it gives when you make/try to burn an audio-cd

---

### Post by bigd0gg on 2006-11-25
> **warjowuch said:**
> THis is stupid indeed, m aybe you could try brasero. Maybe the real solution lies in installing certain gstreamer-packages. Try launching it from terminal and see what errors it gives when you make/try to burn an audio-cd

I am experiencing the same issues.  I do launch from the terminal and Gnomebaker crashes after 88% on a 21minute CD and Serpentine doesn't do anything.

I appreciate the suggestions to keep trying different programs, but when no programs works it would seem the problem lies somewhere else.  Please help.

---

### Post by cactaur on 2006-11-25
Ok, I'm not that experienced with this, but try running serpentine in the terminal with

```
serpentine -d
```

The -d stands for debug, and it will output all the things that happen. Now try burning your CDs.

---

### Post by pspotts on 2006-11-25
In a pinch, try K3b. I've been using it for a couple of years on various Linux distros -- currently with Xubuntu Edgy -- with great success. 

Pete

---

### Post by bigd0gg on 2006-11-25
K3B doesn't work for me either, it won't even open.

---

### Post by bigd0gg on 2006-11-25
(serpentine:5437): GStreamer-CRITICAL **:
Trying to dispose element capsfilter28, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

This is what happens when I use serpentine -d

---

### Post by bigd0gg on 2006-11-25
When I hit Control-C after the previous error message this is what I got,

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/serpentine/mainwindow.py", line 522, in __on_write_files
    validate_music_list (self.music_list_widget.source, self.application.preferences)
  File "/usr/lib/python2.4/site-packages/serpentine/common.py", line 140, in validate_music_list
    if not preferences.pool.is_available (music["location"]):
  File "/usr/lib/python2.4/site-packages/serpentine/converting.py", line 227, in is_available
    if not on_cache and self.is_local(music) and self.is_wav(unique_id):
  File "/usr/lib/python2.4/site-packages/serpentine/converting.py", line 217, in is_wav
    return operations.syncOperation(is_pcm).id == operations.SUCCESSFUL
  File "/usr/lib/python2.4/site-packages/serpentine/operations.py", line 353, in syncOperation
    mainloop.run ()
KeyboardInterrupt

---

