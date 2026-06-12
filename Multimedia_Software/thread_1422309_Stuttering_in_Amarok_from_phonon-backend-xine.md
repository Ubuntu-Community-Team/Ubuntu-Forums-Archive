---
title: "Stuttering in Amarok from phonon-backend-xine"
date: 2010-03-05
forum: Multimedia Software
---

### Post by Yako no Kai on 2010-03-05
In Karmic's Amarok 2.2, when you pause and then play, the sound usually stutters a few times before it starts playing smoothly.  I originally thought this was a pulseaudio issue, as stuttering problems have been reported with pulse, but that wouldn't explain why sound is fine in mplayer, audacious, vlc, dragon player, and virtualbox.  Only amarok has this problem.

I found the cause of the problem: phonon-backend-xine.  These steps will get rid of the stuttering problem:

1. Install phonon-backend-mplayer.  You can get it from Rog131's PPA: [https://launchpad.net/~samrog131/+archive/ppa/+packages](https://launchpad.net/~samrog131/+archive/ppa/+packages)

2. In Multimedia and Sound Configuration, which you can reach through amarok's Playback settings, on the Backend tab, click the arrows to move mplayer up above xine.

3. Quit and restart amarok.

There are some tradeoffs for good sound.  Amarok seems to have some bugs when the sound backend is not xine, and bookmarks and OSD are broken when this backend is playing the sound.  When you quit Amarok, it can't bookmark your place so it doesn't restart from where you last were, and after the track changes once, the OSD when you hover over the tray icon only says "Amarok - No track playing."  You have to open Amarok to find that info.

Now for my question.  Are there any settings I can access for phonon-backend-xine that could fix the stuttering issue?  The problems with the mplayer backend are minor compared with xine's bad sound, but I would like nice sound, OSD, and bookmarking.  Yeah, I'm asking the world.

---

### Post by xcoldfyrex on 2010-11-21
I had the same problem. I found that setting 
```
resample-method = ffmpeg
```
in /etc/pulse/daemon.conf fixed it and it works perfectly

---

### Post by akameswaran on 2010-12-20
did you fix the setting to resample-method = ffmpeg?
What was the original setting?

---

### Post by Yako no Kai on 2011-01-04
I tried it and on some restarts, it seemed better.  But sometimes (perhaps depending on the MP3, as one test album had problems and the other didn't), playback would be totally mangled, starting and stopping continually until I paused and restarted again.  My login sound was also sometimes bad with the xine backend.  I restored the default setting, "resample-method = speex-float-1", and the mplayer backend.

Amarok isn't a big concern for me any longer.  The terrible sound, especially on mp3s encoded for gapless playback, plus the continual worsening of the UI moved me to a better player: foobar2000 in wine.  No integration with KDE, so keyboard shortcuts have bad performance when the system is under load, but otherwise everything is better.

---

### Post by Zorael on 2011-01-06
I've never had any real issues with Amarok sound and Xine, except for Xine cutting off the last few seconds of FLAC playback at the end of the last song in the playlist.

Asking the developers, it seems the order of preference for Phonon backends is still unclear, but the hardcoded order (if no configuration file available) resolves to GStreamer > VLC > Xine. See the comments at [this blog post](http://apachelog.wordpress.com/2011/01/05/phonon-loves-codecs/).

I don't know where the mplayer one fits into all this, though. Both the [VLC](ppa://phonon-backend-vlc) one and the [GStreamer](ppa://phonon-backend-gstreamer) one is available in maverick repositories, though they might be a bit old at this point. The Kubuntu beta ppa (**ppa:kubuntu-ppa/beta**) has an updated phonon-backend-gstreamer.

---

### Post by Yako no Kai on 2011-01-11
> **Zorael said:**
> I don't know where the mplayer one fits into all this, though. Both the [VLC](ppa://phonon-backend-vlc) one and the [GStreamer](ppa://phonon-backend-gstreamer) one is available in maverick repositories, though they might be a bit old at this point. The Kubuntu beta ppa (**ppa:kubuntu-ppa/beta**) has an updated phonon-backend-gstreamer.

On 9.10 (no idea when I'll get the time to upgrade to 10.10) the VLC backend had no packages but there was an mplayer package. These days, there seems to be an i386 build in this PPA: [https://launchpad.net/~samrog131/+archive/ppa/+build/2082149](https://launchpad.net/~samrog131/+archive/ppa/+build/2082149). I'll probably need to give the VLC backend a try, although the problem with mplayer's SSA handling with VDPAU enabled makes it difficult to convince myself to upgrade (stops self before going too off topic).

---

