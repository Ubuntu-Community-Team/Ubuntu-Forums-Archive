---
title: "Choosing a sound output in Clementine"
date: 2012-02-07
forum: Multimedia Software
---

### Post by ivanhelguera on 2012-02-07
Hello, 
I would like Clementine to play through a different audio card then the main audio does - a USB Behringer connected to the hifi equipment, while the system sounds go to the computer speakers.  guess the situation would be similar for other players.
I can stipulate an output, in Preferences -> Playback -> Gstreamer Audio Engine -> output device, but i do not not how to tell the name of the card. 
I use Pulseaudio (I guess).

---

### Post by ivanhelguera on 2012-02-20
Bump?

---

### Post by oldos2er on 2012-02-20
Have you tried using pavucontrol? It's not installed by default so you'd need to run ```
sudo apt-get install pavucontrol
```

---

### Post by Yellow Pasque on 2012-02-21
> Have you tried using pavucontrol?
That will route all of the sound through the chosen device, though (no?).

You choose Pulseaudio, and for the device, you use the name of your headset given by this command (you need pulseaudio-utils package for the command to work):
```
pactl list short sinks
```

---

