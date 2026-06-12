---
title: "Wine, Steam, and Pulseaudio"
date: 2010-01-11
forum: Multimedia Software
---

### Post by phuxed on 2010-01-11
So, here's the issue.

I like to play source engine games on Steam. I also like to play them with friends, and we usually talk to each other on ventrilo, or in this case, I would be using mangler to talk to them.

The problem here is this:

- I can't get many/most steam games to run correctly with pulseaudio installed, they will crash for various reasons

my solution for this, which was recommended to me by winehq was to remove pulseaudio and reinstall the old gnome-sound-properties alsa configuration files from jaunty. I did this, and now I can play steam games without much issue.

now, the new issue is:

- Mangler, ventrilo, and many other wine apps that use sound require pulseaudio to work at all

I can play the game, but I can't use vent at the same time, unless I reinstall pulseaudio, which will brick the games.

What I'm wanting to know, is, is a configuration possible where wine does not use pulseaudio whatsoever, thereby allowing the games to run unhindered, while pulseaudio controls mangler, so I can still talk?

And before anyone asks, voice in steam does not work either. this is a known issue with wine, to my knowledge.

---

### Post by Yellow Pasque on 2010-01-11
What you are asking for sounds impossible. If pulseaudio is running, it won't allow direct access to ALSA devices.

---

### Post by VertexPusher on 2010-01-12
> **phuxed said:**
> Mangler, ventrilo, and many other wine apps that use sound require pulseaudio to work at all
No, they don't. Windows applications have no idea what PulseAudio is; they need MME, DirectSound or ASIO. They don't care which sound system WINE is using because they can't see it anyway.

---

### Post by High Roller on 2010-01-18
The SVN version of Mangler now supports ALSA directly.

---

