---
title: "Alsa capture sharing"
date: 2008-09-23
forum: Multimedia Software
---

### Post by ishkabob on 2008-09-23
I know with software mixing, it is possible to have multiple programs play to the same hardware output.  But is it possible to have two programs both use the same hardware capture input?

I'm running Ventrilo in Wine, and Enemy Territory Quake Wars.  I can talk fine in Ventrilo and hear fine.  And I can hear everything fine in Quake, but when the program launches I get:

```
-------- ALSA Microphone Init --------
snd_pcm_open SND_PCM_STREAM_CAPTURE 'default' failed: Device or resource busy
WARNING: microphone is diabled
--------------------------------------
```

At first I figured this was a wine problem.  However, if I open two terminals and run arecord from one, and then try to run arecord from another, the second terminal gives me this error:

```
kevin@bronyaur:~$ arecord
arecord: main:546: audio open error: Device or resource busy
```

Which tells me that even if I were using native linux apps, this wouldn't work.  I've followed [**THIS**]("http://meandubuntu.wordpress.com/2008/02/19/sharing-alsa-audio-from-wine/") blog post.  And I'm using the asound.conf that follows this post taken from the blog post.  Any ideas?

```
# ALSA library configuration file
# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/kevin/.asoundrc.asoundconf>
pcm.my_card {
type hw
card 0
device 0
}
pcm.dmixed {
type dmix
ipc_key 1024
slave {
pcm "my_card"
}
}
pcm.dsnooped {
type dsnoop
ipc_key 2048
slave {
pcm "my_card"
}
}
pcm.asymed {
type asym
playback.pcm "dmixed"
capture.pcm "dsnooped"
}
pcm.pasymed {
type plug
slave.pcm "asymed"
}
pcm.dsp0 {
type plug
slave.pcm "asymed"
}
pcm.!default {
type plug
slave.pcm "asymed"
}
pcm.etqw {
type asym
playback.pcm {
type plug
slave.pcm "asymed"
}
capture.pcm {
type plug
slave.pcm "asymed"
}
}
```

---

### Post by ishkabob on 2008-09-23
quick update:

Upon further inspection, this asoundrc doesn't work for me at all.  I think there might be a difference between .asoundrc.asoundconf and just .asoundrc.  Either way, I guess what I'm asking is how do I get arecord working from multiple terminals with my SB Live?

---

### Post by ishkabob on 2008-09-23
I've searched a little bit more, and what I want should be possible with the alsa plugin dsnoop.  The alsa documentation states that most cards are dsnooped by default, but considering the fact that I can't run arecord from multiple terminals with my setup, I don't think my card is dsnooped by default.  If someone can just take a look at my asoundrc and tell me if I've made some glaring error, I'm sure that would fix it.

---

### Post by eye208 on 2008-09-24
Do you use PulseAudio? I'm asking because the solution may look different depending on whether you use PulseAudio or plain ALSA.

---

### Post by ishkabob on 2008-09-24
I use Pulseaudio in as much as that it's enabled by default on my system.  I have, however, heard that wine doesn't play nice with pulseaudio, so I'm all for getting rid of it if that's what you suggest.

---

