---
title: "[SOLVED] MPlayer/Xine - No Audio"
date: 2007-10-25
forum: Mythbuntu
---

### Post by dmfrey on 2007-10-25
I have been having trouble getting Mplayer and Xine play audio.  Video plays fine in each.  I am using the spdif output on my AV-710 card.

MPlayer
tried setting -ao alsa:device=<device> and -ac for ac3 passthrough

xine
tried setting pass through for the speaker configuration.  Tried setting alsa or oss as the driver

I have performed these in the past and they worked without issue.

Thanks for any help.

Dan

---

### Post by dmfrey on 2007-10-31
This issue was solved by adding an asound.conf file to /etc

```
pcm.envy_spdifdmix {
type dmix
ipc_key 1337
slave {
pcm "hw:0,1"
format S32_LE
rate 44100
}
}

pcm.envy_spdif {
type plug
slave {
pcm envy_spdifdmix
}
}

pcm.!default {
type plug
slave {
pcm envy_spdifdmix
}
}

# For ogle
#
pcm.!spdif {
type plug
slave {
pcm "hw:0,1"
format S32_LE
}
}

# For mplayer ao (mplayer -ac hwac3 -ao alsa1x:mplayer)
# For vlc, use mplayer as alsa device
#
pcm.!iec958 {
type plug
slave {
pcm "hw:0,1"
format S32_LE
}
}

pcm.mplayer {
type plug
slave {
pcm "hw:0,1"
format S32_LE
}
}


```

---

### Post by BjBlaster on 2009-03-01
Thanks it works a treat!

---

