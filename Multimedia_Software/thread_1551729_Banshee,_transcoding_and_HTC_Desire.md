---
title: "Banshee, transcoding and HTC Desire"
date: 2010-08-12
forum: Multimedia Software
---

### Post by reesje on 2010-08-12
Hi all,

I just installed Banshee, and so far I find the user interface nice and the media player works quite well.

At least it does unless I want to put music on my Desire.

Banshee detects the phone and I am also able to put music on the phone. It is just that it just copies the files to the device rather than transcoding them and copy them to the phone. So an 256kbps MP3 is still a 256kbps MP3 file after syncing it, even though I have specified Banshee to use another format (ogg or MP3@128kbps). I have set the format that I want in the settings menu accessible by right clicking the device.

I have installed the gstreamer lame plugin to have the MP3 option.

Anyway does anybody have a clue as to what I should do to fix this?

BR,
René

---

### Post by reesje on 2010-08-15
Hi again,

Just tried a few things to see if I could get it to work, but no luck :-(

What I am trying to do is to transcode the music I put on my phone to a lower bitrate to conserve space. I set the desired coding format for the phone by right clicking it in banshee, then I can select among others, ogg or mp3. No matter which format I choose, the music is just copied to the device rather than being converted, so even if I try an 256kbps mp3 file and select ogg coding, the music stays in 256kbps mp3.

I do get an interesting message in the console if I start banshee with the "--debug" option:
```
[5 Debug 21:06:54.036] Starting
[5 Debug 21:06:54.255] Initialized MediaProfileManager: 0,212978
[5 Debug 21:06:54.291] GStreamer pipeline does not run: audioconvert ! novellaacenc bitrate=128000 profile=2 outputformat=0 ! novellqtmux
[5 Debug 21:06:54.326] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[5 Debug 21:06:54.343] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[5 Debug 21:06:54.615] Copying Metadata to File Since Sync time >= Updated Time
[5 Debug 21:06:55.904] Finished - Tilføjer 1 af 1 til HTC Android Phone
```
Does anybody of you gurus have any suggestion as to how to fix this?

Is this a banshee problem or a gstreamer problem?

Thanks in advance.
BR,
René

---

