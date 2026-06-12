---
title: "Subwoofer too loud Pulse and Alsa don't help"
date: 2019-10-20
forum: Multimedia Software
---

### Post by corvusluxus on 2019-10-20
Hello all!

This is my first post. I come for help because I have tried everything I've read online and nothing works. I have a Logitech X540 from my Halo 3 days and re used it on my new computer I built. For the first time I connected it with all its inputs (I used to run it only on the stereo green one). I've already managed to make it work on real 5.1 mode but the sub is out of control. Like one of those modified cars rattling their trunks off down the street. I used ubuntu sound settings, alsamixer and pulse to no avail. I can't seem to get a n equalizer either, there are none to download.

I'm running Ubuntu 18.04

Thanks a lot!

---

### Post by #&amp;thj^% on 2019-10-20
Sure there is:
```
sudo apt install pulseaudio-equalizer
```
To start it you'll need to enable a couple of things.


To start the pulseaudio equalizer run:
```

qpaeq
```

If this gives you any error's like:
```

There was an error connecting to pulseaudio,
please make sure you have the pulseaudio dbus module loaded, exiting...
```

then load these two modules using pactl:
```

pactl load-module module-equalizer-sink
pactl load-module module-dbus-protocol
```

If satisfied, to make these changes permanent, edit "**~/.config/pulse/default.pa**" (create it if necessary) and add these lines:
```

load-module module-equalizer-sink
load-module module-dbus-protocol
```
Everything your saying sounds like Volume Levels are to high!

---

### Post by Skaperen on 2019-10-20
or [COLOR=#0000cd][FONT=courier new]_**pavucontrol**_[/FONT][/COLOR] (you might have to install it, too).  it has volume controls for individual output devices and playback sources.

---

### Post by corvusluxus on 2019-10-20
> **1fallen said:**
> Sure there is:
```
sudo apt install pulseaudio-equalizer
```
To start it you'll need to enable a couple of things.


Everything your saying sounds like Volume Levels are to high!

What you mean? It's at 100% without over amplification and master volume at 30% maybe. I did try to install the PA EQ but didn't work, your commands look different, hope they work! Thanks for your quick reply and time, I'll chime in back after trying it.

---

### Post by corvusluxus on 2019-10-20
> **Skaperen said:**
> or [COLOR=#0000cd][FONT=courier new]_**pavucontrol**_[/FONT][/COLOR] (you might have to install it, too).  it has volume controls for individual output devices and playback sources.

I tried pavu but seems like either I did something wrong or haven't got the hang out of it. I open it and can't control anything, I just get some orange bars bouncing with each channels volume when playing media. Thanks a lot!

---

### Post by #&amp;thj^% on 2019-10-20
> **corvusluxus said:**
> What you mean? 
Exactly what it means= "Volume Toooo High,= Noise Distortion".
Don't forget you have Volume controls on the Speakers as well. ;)

---

### Post by corvusluxus on 2019-10-20
> **1fallen said:**
> Exactly what it means= "Volume Toooo High,= Noise Distortion".
Don't forget you have Volume controls on the Speakers as well. ;)

I come from home audio and I find this a bit overwhelming and exciting at the same time, sorry. The way I handle things is always have the source at 100% volume to keep quality and just control the volume at the end either on your receiver or in this case on my X540. It's not even half way up. Never had a problem cranking up the volume on the PC to 100% and managing the end volume on my audio receiver. And I had 4 way speakers with 15" woofers. It's just weird with this thing. What bothers me is that playing around with the controls doesn't change a thing. I'm almost done with my housekeeping and will try the EQ posted above and see how it goes. Thanks again!

---

### Post by corvusluxus on 2019-10-20
By the way, the X540 has a bass knob but it doesn't change a thing either with the 5.1 source from the PC. It only works with 2.0 stereo but then I lose real 5.1 :(. I'll be back ASAP.

---

### Post by #&amp;thj^% on 2019-10-20
Mine are very minor changes with a big sound.(Screenshot)
And for clarity Volume controls are very important in the player as well.
Sound on Linux is superior to any **Stock** OS, there is so much past this little session we are having now.

---

