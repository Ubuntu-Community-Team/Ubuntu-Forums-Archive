---
title: "Sound skipping since upgrade to Hardy Heron"
date: 2008-04-24
forum: Multimedia Software
---

### Post by JamesTee on 2008-04-24
Playing in Amarok using the Xine backend PulseAudio, every minute or so the sound skips. It used to work fine in Gutsy under the old ALSA driver. I'm using a SigmaTel STAC9200.

Is there anything I can do about this?

---

### Post by JamesTee on 2008-04-24
Hm, seems to be a known bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/190754](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/190754)

What a pain shipping something that many people have problems with... looks like I'm just going to have to shutdown Pulseaudio on load. Load of crap.

---

### Post by Delenir on 2008-05-08
I'm sort of getting the same thing, except it's really the whole system that will skip. Once in a while, especially while playing back multimedia, everything will skip for about 5-10 seconds. Sound will skip, video will speed ahead to try and catch up to it, and the system itself runs choppy. This is regardless of what program I'm using (Firefox with flash video, rythmbox for audio, vlc for video, etc.) and can happen without audio playback but not as often. it's worst of all when streaming content.

Edit: When I try to keep an eye on the system monitor to see what app is draining CPU usage when it spikes, it's actually the gnome-system-monitor itself that starts guzzling up CPU usage...

---

### Post by zero_koop on 2008-05-12
It didn't help me completely, but this link may help you guys:
[http://ubuntuforums.org/showthread.php?t=766860&highlight=sound+skips]("http://ubuntuforums.org/showthread.php?t=766860&highlight=sound+skips")

---

### Post by Ghosty.be on 2008-08-13
see also:
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/222597](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/222597)

---

