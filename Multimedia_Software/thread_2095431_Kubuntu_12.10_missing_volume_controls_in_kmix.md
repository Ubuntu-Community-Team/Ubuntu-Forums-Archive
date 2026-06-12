---
title: "Kubuntu 12.10 missing volume controls in kmix"
date: 2012-12-16
forum: Multimedia Software
---

### Post by Arcturus691 on 2012-12-16
Hello,
I am having an issue with kubuntu 12.10 and kmix.  Kmix only shows one volume control under the playback devices. 

I would like to make the rear speakers the same volume as the front ones and adjust the microphone volume. 

Phonon only shows one device: SB Live! EMU10k1 Analog Stereo.  When I looked at instructions for Phonon it looked like there should be many other devices listed there.  I have done many google and forum searches but was unable to find anyone else with this issue.
  
My system is an AMD 64 X2 4400+ with an nvidia nforce4 MB
and a Soundblaster live 5.1 MP3
linux 3.2.0-34-generic
This was a fresh install of kubuntu 12.10

Things I have tried: 
rebooting
stopping/restarting pulseaudio
mv the .pulse audio to .pulseOLD
checked logs (no error)

---

### Post by Yellow Pasque on 2012-12-16
kmix will probably only show you the pulseaudio volume rather than giving you control over all of the low-level stuff. That's why I like qasmixer in KDE environments (it's in Debian repo, not sure about buntu's).

---

### Post by Arcturus691 on 2012-12-18
Thanks, QasMixer looks like it has the settings I was looking for.   This should be included with KDE IMHO as there is nothing in KDE that currently has the same level of functionality.

---

