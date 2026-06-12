---
title: "no more control over PCM volume"
date: 2008-12-07
forum: Multimedia Software
---

### Post by scarf on 2008-12-07
ubuntu 8.10 with all updates installed

the speaker icon in the panel (my volume control) does not have all my controls (tracks) anymore, when i double-click on it.

it says the device is "Analog Devices AD1981B (OSS Mixer)" and that is the only device i can choose.  in preferences, i have everything checked, but there are only 2 playback tracks, "PCM-2" and "In-gain", the rest of the tracks show up under recording.

what i need is "PCM" control.  i would also like control back over the other tracks, like microphone, headphone, cd, phone, aux, etc.... those are all gone.

if i open up a terminal and type "alsamixer -Dhw" it will open up a volume control which has the controls like i was used to, including "PCM".  i can turn up the PCM volume and hear things better.

AlsaMixer v1.0.17
Card: Intel 2801DB-ICH4
Chip: Analog Devices AD1981B

when i turn up/down the PCM-2 volume in the volume control GUI, it seems to correspond to the "headphone" control in the terminal (alsamixer -Dhw), as the volume moves at the same time.

so, that is good and i can easily adjust my headphone volume, but still i do not have any control over the speaker volume, unless i open up a terminal and use "alsamixer -Dhw"

if i open up my "sound preferences", i have tried setting the playback devices to "Intel 81801DB-ICH4 with AD1981B Intel 81801DB-ICH4 (ALSA)".  (there are some other choices, which i have all tried, including "Autodetect", "Intel 81801DB-ICH4 with AD1981B Intel 81801DB-ICH4 - IEC958 (ALSA)", "Intel 81801DB-ICH4 with AD1981B Intel 81801DB-ICH4 (OSS)" (there are 3 copies of that choice), and "OSS - Open Sound System").    however, the "device" under "default mixer tracks" cannot be changed (only choice is "Analog Devices AD1981B (OSS Mixer)" like i see in my volume control applet).

i think i need my device to be ALSA (since, when i use "alsamixer -Dhw" that is where the track controls i want are) but the only device choice in "sound preferences" ends with "(OSS Mixer)" ......

how to get back my volume tracks control in the graphical applet?

---

### Post by scarf on 2008-12-10
bump

---

### Post by scarf on 2008-12-16
sorry, bump!

---

### Post by frankleeee on 2008-12-16
Did you open volume control-preference tick on pcm to add it to the control or tick in pcm below the oss drop down in the right click on preferences on the icon.

---

### Post by scarf on 2008-12-17
thanks, but i have already tried that.

in volume control preferences, everything is ticked:

```
PCM-2      Playback
In-gain    Playback
Volume     Recording
Line-in    Recording
Microphone Recording
CD         Recording
Line-1     Recording
Phone-in   Recording
Phone-out  Recording
Video      Recording
```

as you can see, i only have control over two playback tracks, and PCM is no where to be found.  the same list of tracks show up in the right-click preferences on the icon.

in the "oss drop down" there is no other device i can select.


playback tracks i have control over in the "alsamixer -Dhw" terminal application:

Master, Master Mono, Headphone, Headphone Jack sense, PCM, Line, Line Jack sense, CD,  Mic, Mic Boost, Mic Select, Phone, Aux, Mono Out select, External Amplifier, Stereo Mic.

---

### Post by scarf on 2009-02-05
:confused:

---

### Post by scarf on 2009-02-22
the controls are finally back again.  i guess some updates fixed the problem.

i now have my choice again to select "Analog Devices AD1981B (OSS Mixer)" or "Intel 82801DB-ICH4 (Alsa mixer)" as the device.

---

