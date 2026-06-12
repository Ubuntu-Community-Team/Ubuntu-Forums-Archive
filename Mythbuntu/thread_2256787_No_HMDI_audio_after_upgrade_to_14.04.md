---
title: "No HMDI audio after upgrade to 14.04"
date: 2014-12-14
forum: Mythbuntu
---

### Post by Denis_Papathanasio on 2014-12-14
I experienced many of the same problems Paul Rubin described here: [http://orinanobworld.blogspot.com/2014/08/mythbuntu-upgrade-from-hell.html](http://orinanobworld.blogspot.com/2014/08/mythbuntu-upgrade-from-hell.html)

But even after resolving all the other issues, I cannot get digital sound via HDMI (analog does work, though).

Here's a snapshot of my alsa data: [http://www.alsa-project.org/db/?f=5853563c300e39bea5fbdde8d53e1c63511da36d](http://www.alsa-project.org/db/?f=5853563c300e39bea5fbdde8d53e1c63511da36d)

Any help would be appreciated!

---

### Post by Denis_Papathanasio on 2014-12-31
This is now working; fixing it was a pain, but here are the steps, in case anyone else has the same problem.

First, I installed the alsa-daily ppa:

```

  sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
  sudo apt-get update
  sudo apt-get install oem-audio-hda-daily-dkms
```

Then, I used alsamixer which showed an alternative to the default IXP (analog) output.

There were four "S/PDIF" settings (S/PDIF, S/PDIF1, S/PDIF2, S/PDIF3)  all of which were muted (set to "MM"), which I enabled (setting to "00")  by typing "m" while scrolling through them.

Next, I ran this:

```

  aplay -L | more
```

which (finally) showed the NVidia HDMI card among the list of possibilities:

```

plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
```
  
Next, I tried each by trial and error:

```

  aplay -D plughw:CARD=NVidia,DEV=3 /usr/share/sounds/alsa/Front_Center.wav
  aplay -D plughw:CARD=NVidia,DEV=7 /usr/share/sounds/alsa/Front_Center.wav
  aplay -D plughw:CARD=NVidia,DEV=8 /usr/share/sounds/alsa/Front_Center.wav
  aplay -D plughw:CARD=NVidia,DEV=9 /usr/share/sounds/alsa/Front_Center.wav
```

For me, this combination was the only one that worked:

 ```
plughw:CARD=NVidia,DEV=7
``` 

So back in the MythFrontend application, I went to **Setup** -> **Audio** and in the **Audio output device** input field, I scrolled until I found ```
plughw:CARD=NVidia,DEV=7
```

Success!

What I still don't understand, though, is why pavucontrol shows just "Built-in Audio".

Before upgrading, the same exact hardware and proprietary nvidia driver  (331) showed up as a distinct "HDMI Audio" option in pavucontrol.

I could just pick that, and not have to mess around with aplay or changing the preferred audio device in the MythFrontend app.

---

