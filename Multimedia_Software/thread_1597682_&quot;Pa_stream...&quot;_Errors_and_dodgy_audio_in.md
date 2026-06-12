---
title: "&quot;Pa_stream...&quot; Errors and dodgy audio in Ubuntu 10.10 Movie Player"
date: 2010-10-15
forum: Multimedia Software
---

### Post by Telescopic Trout on 2010-10-15
Has anyone else had any problems with playing video files in Movie Player? I have just installed Ubuntu 10.10 (so its a clean install) and when I go to play any video file the sound and video go out of sync and start to skip back and forth after a few seconds playing. In most instances it eventually crashes and gives the following two errors:

"Pa_stream_cork()failed: Connection Terminated"

"Pa_stream_writable_size()failed: Connection Terminated"

I did a quick search on the web last night and didn't find much but I did see mention of it being a problem with the pulse audio which kind of makes sense since I have the same issue (except the app doesn't crash and return me with these erros) with the Rythmbox Music Player.

Any suggestions? I have tried updating the packages but there is no improvement, and if it helps the movies are .avi files...

---

### Post by kerry_s on 2010-10-15
uninstall "gstreamer0.10-pulseaudio", that causes pulseaudio to crash,they haven't fixed it since 10.04

---

### Post by StephenDavison on 2010-10-16
I'm having the same problem on my MSI Wind U100 for a podcast I listen to in Rhythmbox.  I thought it might be gstreamer because VLC has no problem.  This is one of two problems keeping me on 10.04.

---

### Post by Telescopic Trout on 2010-11-03
Kerry_S, thanks for the reply and sorry for the delay. A combination of crap ISPs and power cuts mean I dance around like a lunatic whenever my connection is back up. (As if to spite me my electricity went again half way through writing this...)

I actually found a post in another link ([http://ubuntuforums.org/showthread.php?t=1592120](http://ubuntuforums.org/showthread.php?t=1592120)) a little before your reply where the they had edited one line in the pulse audio file in the following location - /etc/pulse/default.pa This worked for me and solved the problems I had with my various video and audio players. If you're interested have a look through the link I would love to know how this worked.

---

### Post by anothermikemiller on 2010-11-11
> **kerry_s said:**
> uninstall "gstreamer0.10-pulseaudio", that causes pulseaudio to crash,they haven't fixed it since 10.04

Ubuntu-Desktop depends on this so you might want to through a warning out next time that this is just a transitional package and is safe to remove.

Worked for me. I would assume that switching to the xine backend would work too.

```
sudo apt-get install totem-xine
```

Anyone try to find or compile an updated pulse plugin for gstreamer?

The link in the previous post is for people having stuttering video and sound using any media player, i.e. vlc, smplayer, etc.

---

### Post by Yellow Pasque on 2010-11-11
> uninstall "gstreamer0.10-pulseaudio", that causes pulseaudio to crash,they haven't fixed it since 10.04
Before uninstalling that package, it might be beneficial to just change the gstreamer sinks to alsa (make sure gstreamer0.10-alsa is installed) to see if it fixes the issue. If the problems continue, it's probably a more general issue with pulse than the gstreamer-pulse interface.
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink alsasink
```

> Anyone try to find or compile an updated pulse plugin for gstreamer?
Latest stable gstreamer is found here: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

> I would assume that switching to the xine backend would work too.
totem-xine was abandoned a few years ago, and the package is just a dummy package that points to totem-gstreamer. Of course, there are other xine-based players to try (though the KDE folks also seem to be moving away from xine, favoring vlc backend for Phonon and Qt/Nokia favoring gstreamer for the new qtmultimedia API).

---

### Post by e_james on 2011-01-14
Linux Mint 10 doesn't use ubuntu-desktop and I have found that removing the gstreamer pulseaudio plugin seems to solve the problem with no noticeable downside.

I am no expert in audio and video; I only know what works and doesn't work for me, but I think I have got a bit closer to pinpointing the source of the problem. I made several very short video clips with divx 5 for the video and different audio streams. Using mp3, aac or ac3 audio, if the sampling rate is 22050 the clip plays OK, if the rate is 24000 then the playback fails using Totem movie player and produces the above mentioned error message. 

To the best of my limited knowledge, PAL derived video normally uses an audio sampling rate of 48000 or 24000. If the rate is 44100 or 22050 then there may be problems with audio / video synchronising. I suspect that somewhere in the current gstreamer / pulseaudio / fluendo system there is an assumption that only sampling rates of 44100 or 22050 are valid, or some bug with the same effect.

---

### Post by burdebc on 2011-03-26
I had a similar issue spring up totally at random.  I was watching some videos last night and they worked fine, but today those exact same videos wouldn't play(with no changes to the system, I am pretty sure I didn't even update anything).  I was getting pa_stream_cork() failed and pa_stream_ writable_size() failed.  I simply uninstalled and reinstalled pulseaudio in synaptic and my videos started playing again.  I didn't pay attention to what was removed and installed along with pulseaudio, but a lot more was uninstalled than was installed.  Maybe the answer lies there somewhere.  If this happens again I will report back with more complete info.

---

### Post by Picado on 2011-04-08
Folks,

I had this problem. I tried to remove and re-stall the gstreamer0.10 and no such luck.
Then I decided to use VLC to play dvds and works great, so far no bugs.

---

