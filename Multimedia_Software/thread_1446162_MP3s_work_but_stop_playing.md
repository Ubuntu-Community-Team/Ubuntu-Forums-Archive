---
title: "MP3s work but stop playing"
date: 2010-04-03
forum: Multimedia Software
---

### Post by chris3030 on 2010-04-03
Hello,

I am having an mp3 problem for which I can't seem to find any solution to.  My mp3s will work but will cut out before the song is over.  Everything will be working fine until the sound suddenly stops and the progress bar will run thru the rest of the song quite fast and will do this for the next subsequent songs.  For the record, this happens on rhythmbox, amarok, VLC and also the movie player app.

I have installed the gstreamer plugins as well as the restricted extras packages.  I am currently using Karmic but it should be noted that I have used Gutsy and Hardy in the past with ZERO problems regarding mp3 playback.

I have used ubuntu in the past and I really like it. I have recently come back to it and I really enjoy Karmic, however not being able to listen to music is a dealbreaker for me. Please help me, I don't want to keep booting crappy Windows just to be able to listen to music :(

---

### Post by lidex on 2010-04-03
Give this a run-through and report back:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by chris3030 on 2010-04-03
Thank you for your help.  MP3 playback now works however there are a lot of hiccups in the playback, sounding very much like a CD thats skipping.  Is there anything I can tweak to correct this?

---

### Post by lidex on 2010-04-03
Are these files on local disk or external/network?

Maybe this:
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")
GStreamer Applications ¶

Applications using the modern GStreamer media framework such as Rhythmbox or Totem can make use of the PulseAudio through gst-pulse, the PulseAudio plugin for GStreamer in gst-plugins-good. After installing it, you have to enable it as default audio sink and source for all GNOME applications by changing the GConf keys /system/gstreamer/0.10/default/audiosink and /system/gstreamer/0.10/default/audiosrc:

gconftool -t string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool -t string --set /system/gstreamer/0.10/default/audiosrc pulsesrc

Alternatively, you can make these changes with the GUI tool gstreamer-properties.

The GStreamer plugin wraps playback, recording and the mixer interface.

---

### Post by chris3030 on 2010-04-04
> **lidex said:**
> Are these files on local disk or external/network?

Maybe this:
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")
GStreamer Applications ¶

Applications using the modern GStreamer media framework such as Rhythmbox or Totem can make use of the PulseAudio through gst-pulse, the PulseAudio plugin for GStreamer in gst-plugins-good. After installing it, you have to enable it as default audio sink and source for all GNOME applications by changing the GConf keys /system/gstreamer/0.10/default/audiosink and /system/gstreamer/0.10/default/audiosrc:

gconftool -t string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool -t string --set /system/gstreamer/0.10/default/audiosrc pulsesrc

Alternatively, you can make these changes with the GUI tool gstreamer-properties.

The GStreamer plugin wraps playback, recording and the mixer interface.

These files are on a local disk.  I already had the pulseaudio but I played around with it and changed the default sink, server and source to default.  This has helped a little bit as I now have good playback for a limited period of time before it starts randomly skipping and pausing.  There is obviously some sort of problem that I need to narrow down.  My system has relatively decent specs so I don't think that is the problem.  Here are the particulars of my system:

3.33ghz processor, 2GB of RAM
NVIDIA GeForce 7500 Video Card
C-Media CM8738 Sound Card (I don't think this is a driver issue as it identifies my card correctly in system>preferences>sound)

It may or may not be worth noting that I also run windows XP (on a completely separate hard drive) and there is zero sound/playback problems.

For what its worth, I have had no playback problems with Gutsy and Hardy in the past.  I am an advanced windows user but a novice ubuntu user and it is my educated guess that either something isn't configured correctly or theres some difference in karmic thats not playing nice with my computer.  Any further help would be appreciated, this is driving me up the wall :(

---

### Post by lidex on 2010-04-04
Try this PA guide and see how your apps respond:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

