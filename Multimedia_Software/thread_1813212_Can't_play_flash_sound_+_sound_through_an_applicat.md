---
title: "Can't play flash sound + sound through an application, no control over flash volume."
date: 2011-07-27
forum: Multimedia Software
---

### Post by Ecstatic23 on 2011-07-27
I've been dealing with this problem for months.

I can play 2 different songs simultaneously through totem/vlc/etc,
but I can't hear any audio from an online flash video (tested multiple browsers) unless I close out of the application currently playing audio.
If I'm watching a YouTube video, and it finishes, after I close out of it, any previous notification sounds (from Pidgin, Skype) will play all at once.

Flash volume can only be adjusted from the flash interface itself or from the hardware volume control, not from my keyboard or through any of the options.

Sorry if my English is a bit sloppy, it's late.

Thank you for reading.

---

### Post by CatKiller on 2011-07-27
It's because Flash wants total control over the sound device. You can force it to play nicely by making PulseAudio the default sound device for ALSA.

```
gksudo gedit /etc/asound.conf
```

Put this inside.
```

# enable PulseAudio as ALSA device

pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

# use PulseAudio as default device

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

---

### Post by Ecstatic23 on 2011-07-28
> **CatKiller said:**
> It's because Flash wants total control over the sound device. You can force it to play nicely by making PulseAudio the default sound device for ALSA.

```
gksudo gedit /etc/asound.conf
```

Put this inside.
```

# enable PulseAudio as ALSA device

pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

# use PulseAudio as default device

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

No luck :/

---

### Post by CatKiller on 2011-07-28
> **Ecstatic23 said:**
> No luck :/

Pity. Worked for me.

The only other thing I've got to offer is [this link]("https://wiki.ubuntu.com/PulseAudio#Firefox.2BAC8-Flash_and_PulseAudio").

---

### Post by .... on 2011-07-28
> **Ecstatic23 said:**
> No luck :/
Did you reboot yet?

---

