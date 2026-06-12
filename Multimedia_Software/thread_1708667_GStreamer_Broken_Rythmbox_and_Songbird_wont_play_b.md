---
title: "GStreamer Broken Rythmbox and Songbird wont play but Audacious Does"
date: 2011-03-17
forum: Multimedia Software
---

### Post by kanazky on 2011-03-17
My Rythmbox and SongBird when I click a mp3 the fan goes into over drive and the mp3 song play timer goes up in three's and doesn't play any audio. But I can play the mp3 files in Audacious.

I have gstreamer installed and I can do gstreamer-properties and its setup right for alsa...

Whats going on with Songbird and Rythmbox?

---

### Post by Yellow Pasque on 2011-03-17
Unless you've removed pulseaudio, set your gstreamer to play directly to it rather than alsa (which will just get mixed into pulseaudio through its alsa plugin anyway). At any rate, the later versions of gstreamer-properties don't actually provide a GUI option for the gconf key rhythmbox uses (/system/gstreamer/0.10/default/musicaudiosink). I'm not sure if Songbird uses that too or the more generic audiosink. (Run gconf-editor to see/edit these keys).

As for what's going on, terminal output might be helpful.

---

### Post by kanazky on 2011-03-17
Thats the weird part, when I use songbird through terminal it doesnt play an error.

The time bar skips by 3
Computer goes super slow
and the Fan goes into High Mode

musicaudiosink = autoaudiosink
audiosink = alsasink

---

