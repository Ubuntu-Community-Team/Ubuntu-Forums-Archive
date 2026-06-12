---
title: "no sound from mpd"
date: 2010-11-17
forum: Multimedia Software
---

### Post by bobdobbs on 2010-11-17
Hi all.

I recently re-installed my system with the latest ubuntu.
I decided to install mpd and gmpc. I get the most out of my music collection with these tools.

Initially I could start mpd, but couldn't play any files. gmpc would report "problem opening audio device"

After looking at some old posts I edited my mpd.conf file. The audio_output section now looks like this:

```

audio_output {
        type "pulse"
        name "My Pulse Output"
# server "localhost" # optional
# sink "alsa_output" # optional
}
```

Now I can play files. But I get no sound. In gmpc the volume is up. I get sound from rhythmbox and my browser, but nothing from gmpc.

What could be happening here, and how do I fix it?

---

### Post by bobdobbs on 2010-11-27
bump

---

### Post by bobdobbs on 2010-12-01
bump

---

### Post by lidex on 2010-12-02
Not sure. Did you pull that info from here:
[http://mpd.wikia.com/wiki/PulseAudio](http://mpd.wikia.com/wiki/PulseAudio)

---

