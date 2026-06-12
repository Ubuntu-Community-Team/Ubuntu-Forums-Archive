---
title: "channels ok... errrrr not really. but they are ok."
date: 2011-01-18
forum: Multimedia Software
---

### Post by hlb on 2011-01-18
hi

1201nl with nvidia ION hdmi mapping in alsa seemingly ok on nvidia 0:3  here (tested with speaker-test, everything in the right place),

but if i play any 5.1 file with mplayer with alsa nvidia 0:3 configured,  vlc or movie-player, what i get is the "chatty channel" on the  surround-left and not on the center, and nothing on the surround-right.

what could be the reason?

ty a lot

```

/etc/asound.conf
pcm.!hdmi-remap {
  type asym
  playback.pcm {
  type plug
  slave.pcm "hdmi"
}
}

pcm.!hdmi {
  type route
  slave.pcm "hw:0,3"
  ttable  {
    0.0= 1
    1.1= 1
    2.4= 1
    3.5= 1
    4.2= 1
    5.3= 1
  }
}

```

---

### Post by hlb on 2011-01-19
bump, no suggestions?

I might add that i checked for the existence of a wrong .asoundrc in $HOME, but it wasn't there.

ty a lot

---

