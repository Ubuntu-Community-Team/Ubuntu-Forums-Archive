---
title: "Creative Soundblaster X-FI Fatality Finally working! almost :)"
date: 2009-07-26
forum: Multimedia Software
---

### Post by Taus on 2009-07-26
Hi all,

i've been struggling for ages with my sound blaster x-fi card, and finally i got sound from the spdif channel! yeey - i'm so excited that I can't get this huge smile off my face.

Anyways - i am left with a very small problem which i'm sure is easy to resolve if you know how to do it.

when i open my music files in Rythmbox everything plays nicely. But Rythmbox seems to be the only program that plays trough the right device.

in preferences -> sound i have chosen "Creative ALSA Driver X-Fi IEC958 Non-audio (ALSA)" everywhere. When i click test i hear the sound.

i also configured VLC to use that device which now also can play sound and dvd movies.

my question is if there is a way to set all apps to use that device by default so i won't need to look for config files in every application i install?

any help or point in the right direction will be very much appreciated.
Thanks for reading and thanks for your time.

cheers
Taus

---

### Post by terry_gardener on 2009-07-26
you could try and install pulseaudio device chooser and select the correct device in there. 

i have to do this on my nephews pc as it defaults to the wrong device.

---

### Post by Taus on 2009-07-26
Wow quick reply :)

just tried installing pulse audio device chooser, but apparently i'm not using pulseaudio so I can't even choose a device in there. dang. But thanks for the suggestion! :)

---

### Post by Taus on 2009-07-26
i found out that rythmbox uses this device: 

```
halaudiosink udi=/org/freedesktop/Hal/devices/pci_1102_5_sound_card_0_alsa_playback_4
```

now i just need to make it default for all apps somehow.

---

### Post by Taus on 2009-07-26
if anyone else should have the same problem. i think i figured it out by editing the .asoundrc file...

not sure if this is the best solution but at least it works:

```

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
# </home/judas/.asoundrc.asoundconf>

pcm.!default {
    type plug
    slave.pcm "ossmix"
}

pcm.ossmix {
    type dmix
    ipc_key 1024
    slave {
    pcm "hw:0,4"
       #rate 8000
       rate 44100 # we want to play CDs only
    }
    bindings {
        0 0
        1 1
    }
}
# OSS via aoss should d(mix)stroyed:
pcm.dsp0 {
    type plug
    slave.pcm "ossmix"
}



# Xine doesn't use the "default" device for S/PDIF but this:
pcm.!iec958 {
type plug
slave.pcm "hw:0,4"
}

ctl.!iec958 {
type hw
card 0
}


```

---

