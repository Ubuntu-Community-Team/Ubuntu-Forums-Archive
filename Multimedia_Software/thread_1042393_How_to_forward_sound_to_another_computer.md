---
title: "How to forward sound to another computer?"
date: 2009-01-17
forum: Multimedia Software
---

### Post by kwilliam on 2009-01-17
I've got a laptop with Kubuntu and a desktop with Mythbuntu running MythTV. The speakers on the MythTV box are much nicer sounding than the laptop's, so occasionally I will remote into the Mythbuntu box to play music (from say, Pandora or Imeem). However, I can't play any music from my laptop's hard drive that way. Is there a way I can simply forward sound from my Kubuntu laptop to the Mythbuntu box? I'm told Esound can do that, so presumably PulseAudio can do that, but I'm not even sure that Kubuntu 8.10 uses PulseAudio. When I test the PulseAudio output device in System Settings > Multimedia, a box pops up saying PulseAudio failed and it's falling back on HDA Intel. "dpkg -l | grep pulse" returns only one package, libpulse0. And sound works flawlessly on my laptop (including flash), so I don't want to start installing random PulseAudio things without knowing what I'm doing. Same question applies to Mythbuntu - I don't know if it uses PulseAudio or not. If I got PulseAudio working on both of them, how would I go about getting my laptop to play through the Mythbuntu box's speakers?

---

### Post by kwilliam on 2009-01-28
I guess forwarding sound isn't as popular as I thought. Bump?

---

### Post by markbuntu on 2009-01-28
Pulseaudio comes with built in multicast rtp send and receive functions. You just need to turn it on in the Configure Local Sound Server/PulseAudio Preferences and set it up.

[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio)

---

