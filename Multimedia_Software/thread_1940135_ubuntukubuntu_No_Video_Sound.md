---
title: "ubuntu/kubuntu No Video Sound"
date: 2012-03-13
forum: Multimedia Software
---

### Post by ytene on 2012-03-13
Here's a weird one which may be self-inflicted. 

Downloaded and installed 12.04 64-Bit edition to a Core i7 Quad that has on-board sound on the motherboard and also a Creative Labs SoundBlaster installed, plus an nVidia 480 GPU. After the basic unity installation, OS patching and installation of nVidia's proprietary driver, I then installed the KDE meta-packages and run in KDE. [I do this rather than native kubuntu builds so that when I completely trash KDE I can fall back to Unity to fix things...]

Booting into KDE I can get Rhythmbox to play music from my iTunes library [AC4 format], though that was somewhat fiddly for this release. However, trying to get sound from a K9Copy-Archived DVD would give me picture and no sound.

I went through every possible permutation of KDEs audio setup, proved that my 5.1 speakers were all good, did tail -f of log files, found no issues. I got Rhythmbox music, but no movie audio with any media player I tried [ Totem, vlc, MPlayer, etc].

Went back into Unity and there is a small icon for a speaker in the top right of the display. Clicked, open the setup. Checked settings, saw that the sound setup for my Soundblaster had somehow defaulted to optical output [there is no cable connected]. Fixed.

Went back to KDE and everything works beautifully. 

I guess the lesson here is that when layering Window Managers on top of a base Unity build, it's wise to check all core functionality before additing the additional WMs. We live, we learn...

---

