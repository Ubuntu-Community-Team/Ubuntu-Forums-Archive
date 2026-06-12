---
title: "No MIDI in or out of Rosegarden"
date: 2014-05-28
forum: Multimedia Software
---

### Post by andy_wainwright on 2014-05-28
Have just taken the plunge and switched to Linux (Ubuntu 12.4, 64 bit / DreamStudio distro) for music production after using commercial Windows/Mac software for the last 20 years. After a lot of trial and error with help from forums like this I have got Ardour 3, JACK, Hydrogen all working through an EMU 0404 card both audio and MIDI. In addition my USB MIDI interfaces both work, including an Origin 25 Keyboard in both these apps, which will work together fine.

However on installing Rosegarden, even though the MIDI ports all show up in preferences, I can neither get MIDI in or out of the program.

In JackControl connections, the ALSA settings show the MIDI and Rosegarden in ports, but unlike the other apps I cannot connect the two. Jack does report an ALSA configuration change and no errors, but the lines will not show up. On doing this it doesn't show a "no entry" sign as you would get when you cannot physically connect devices, but just doesn't connect.

Does anyone have any suggestions on how to fix this. All other apps support both audio and MIDI not problem. I'd love to use this package as Ardour's MIDI facilities are still essentially in beta stage and fairly limited and most of my work involves MIDI progamming.

I'm impressed generally at the power provided by the Jack system and would like to make more use of it. Can you help?

---

### Post by andy_wainwright on 2014-05-28
[B]This seems to sort some of the issue out. It's an Alsa to Jack bridge program.

a2jmidid -e[/B]

---

