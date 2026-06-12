---
title: "Sound randomly working after Dapper Upgrade"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by SergioA on 2006-06-09
Hi there!

THe sound of my system after upgrading to Dapper sometimes works from boot, other times (mostly) doesn't... Everything was fine in 5.10 so I'm a little lost...

Double clicking on the volume icon gives the following information:

a) when sound is working I can see these devices:

    0: VIA 8235 (Alsa mixer)
    1: SAA7134 (Alsa mixer)
    2: Realtek ALC655 rev0 (OSS Mixer)

b) when it's not working:

    0: SAA7134 (Alsa mixer)
    1: VIA 8235 (Alsa mixer) <-- Selected by default
    2: SAA7134 Mixer (OSS Mixer)

    And if I tray to play any sound file I get this error message:

    "Totem could not startup."
    "Could not establish connection to sound server"

It seems that sometimes at boot the system is correctly set up and I can get the sound working, others the configuration is messed up and I've got no sound...

Any advice?

Thanks and Ciao

Sergio

---

### Post by woedend on 2006-06-09
I hate this problem as well...although mine is not exact as yours so you must play with it.  The file is /etc/modprobe.d/alsa-base
There are two options, either add the SAA module to the bottom so that it isn't grabbed by default, or add the VIA module to the section that says is loaded before the rest.  Odd thing is that Via says its loaded before the rest, so I suppose you need to add a line(using the examples at the bottom) to fit your SAA.  Unfortunately, I'm not sure what that module is.
I think this might work, let me know...try adding to the very bottom this:
options saa7134 index=-2

or else 

options saa7134-alsa index=-2

---

### Post by SergioA on 2006-06-09
Hi woedend!

Many thanks for your kind reply ;-)

Now I'm at work, tomorrow I will try to play with your settings and report the results...

Ciao

Sergio

---

### Post by SergioA on 2006-06-10
Here I am,

added "options saa7134-alsa index=-2" as last line in /etc/modprobe.d/alsa-base and it seems that sound is constantly working at boot... at lesat untill now ;-)

Ciao and thanks again

Sergio

---

