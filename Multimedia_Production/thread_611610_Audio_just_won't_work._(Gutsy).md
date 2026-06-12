---
title: "Audio just won't work. (Gutsy)"
date: 2007-11-13
forum: Multimedia Production
---

### Post by Jeek on 2007-11-13
I am a new Ubuntu user, and have a Dell Inspiron 1501 with Gutsy installed. Everything works... until I installed the audio portion of Ubuntu Studio to try things out.

I got the JACK driver started (albeit with some Xruns no matter how I change the settings) and Qsynth appears to work when connected to JACK (I have loaded a .sf2 soundfont).

However, when I tried to get some sounds while following the tutorial at [https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections) , things just won't work. I have made the connections between the inputs and outputs as shown there, but when I pressed the keys on the virtual keyboard, ZynAddSubFX gave no response and no sound came out.

The same happened when I run Rosegarden and JACK. I get sound at other circumstances (eg. playing Youtube videos), however.

Your help is greatly appreciated.

Additional question: I downloaded a MIDI file for testing but got no sound from it either. Is that part of the same problem?

---

### Post by Onos on 2007-11-13
I'm more or less in the same situation:

I reformatted and wrote over my old Dapper partition with a fresh install of Gutsy. Following that, I built up my usual favorite applications from the terminal directions on UbuntuGuide (for Gutsy) which included Pulse (so I could "preview" my MP3s by mousing over them) Banshee, VLC, and Helix players, along with some movie transcoding apps (ffmpeg, mencoder, things like that)

Finally, having decided to try out the audio portion of Ubuntu Studio, I grabbed that from aptitude by selected most of the packages listed on the package listing page at [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

I left out the linux-image-lowlatency (was afraid of messing up my kernel) and ardour2-gtk (which seems not to be in the repository at the moment).

And the sound stopped working from there.

DELL Dimension 8100
2GHz, 1GB RAM
nVidia GeForce FX 5500 (video adapter)
Integrated Audio (82801EB ~ ICH5)

---

