---
title: "Sound Juicer: RIPS to Mono, I want Stereo"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by MusicProducer on 2007-08-15
When I rip CD tracks to WAV files with Sound Juicer, the results sound Mono, but I want Stereo. It used to give me stereo; I don't know what caused the change. Help, please.

---

### Post by RomeReactor on 2007-08-15
Hi. Try this: open SoundJuicer, go to "Edit->Preferences->Edit Profiles", highlight "Voice, Lossless", press "Edit" and read the Gstreamer Pipeline:
```
audio/x-raw-int,rate=22050,**channels=1** ! wavenc name=enc
```
if it reads "channels=1", try changing it to 2:
```
audio/x-raw-int,rate=22050,**channels=2** ! wavenc name=enc
```

---

### Post by MusicProducer on 2007-08-15
Your diagnosis is exactly right:

[IMG]http://img179.imageshack.us/img179/5559/screenshoteditingprofilkf4.png[/IMG]

Thank you. But when I try to edit the "GStreamer pipeline" field, I'm unable to move the cursor to that field, apparently due to some bug. When I click on the "Close" button, that doesn't work either; but hitting the Escape key closes the dialog.

?

---

### Post by RomeReactor on 2007-08-15
Just close the previous window, and you'll be able to edit the field and use the close button. That happened to me as well; must be a bug.

---

### Post by MusicProducer on 2007-08-15
> **RomeReactor said:**
> Just close the previous window, and you'll be able to edit the field and use the close button. That happened to me as well; must be a bug.

That worked. I appreciate your help. I'll report the bug.

---

