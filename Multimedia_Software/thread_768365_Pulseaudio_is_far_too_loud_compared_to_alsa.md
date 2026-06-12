---
title: "Pulseaudio is far too loud compared to alsa"
date: 2008-04-26
forum: Multimedia Software
---

### Post by PatrickMay16 on 2008-04-26
I updated to Hardy (8.04).

Programs using Pulseaudio are very very loud, much louder than programs using alsa. I can change an individual stream's volume with pavucontrol (why on earth is this not installed by default?), but it gets reset back to 100% if the program changes from stereo to mono. 

Is there any way of changing Pulseaudio's default stream volume level? I want it so that every pulseaudio program will start with it's stream's volume set to 25% or something.

Thanks for the help.

---

### Post by PatrickMay16 on 2008-04-26
Bump.

---

### Post by Frischtransporte on 2008-04-26
del this post plz
sry^

---

### Post by billybag on 2008-06-15
I have the exact OPPOSITE problem!!! PulseAudio is way tooo quiet!

i have my laptop hooked up to my home stereo and i have to turn the volume on my stereo to MAX and it still isnt loud enough!!!!

i am probeblay being too quick to judge. but PulseAudio really ******* sucks. i have had nothing but problems ever since is tarted using Hardy

---

### Post by Aruhn on 2008-06-15
And for me was PulseAudio an comfortable solution for my external Soundcard - with Alsa had I problems, with PulseAudio none and it's not to quiet and not to loud. 

Maybe the /etc/pulse/daemon.conf file can help? :confused:

---

### Post by loyd86 on 2008-09-28
I have the same problem. Seems much quieter, or just the fact that its got too much range. I have to stay at about 80% -100%, Because if I go down to 40% I can trun the gain on my speakers up and will get almost nothing, but thin I go to 95% and it is just way to loud.

---

### Post by markbuntu on 2008-09-28
You can adjust the volume for the indidivual streams and the output devices in the PA Volume Control. It is the combination of these that determines the range that the controls will work over. A lot of applications also have thier own volume controls and eqs. You need to set these up individually to get consistent volumes.

If the default volume is giving you problems, you can edit your etc/pulse/default/pa and comment out this line so it looks like this:

```

#load-module module-volume-restore

```

This will stop PulseAudio from loading default volume levels when it starts up. It may make things better, it may make the startup sounds be at maximum volume and blow up your speakers.

---

