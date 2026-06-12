---
title: "No center channel or LFE"
date: 2009-07-15
forum: Multimedia Software
---

### Post by chemtyra on 2009-07-15
Hello everyone,
I am a relative newcomer to Linux. I am fairly familiar with computers and command lines.
I am running Ubuntu 9.04
I have an AN8-SLI premium MB with onboard Realtek AC97 5.1 audio. 
I have configured Pulseaudio daemon.conf to default to 6 channels. 
I am now able to hear the correct channels through the front and rear channels. 
No sound is coming from either the center channel or LFE.
When I view the Pulseaudio volume meter, it indicates a normal lvl for the center channel and no lvl for the LFE. However no sound comes out of either speakers.
Any help will be greatly appreciated.

---

### Post by chemtyra on 2009-07-16
Bump

---

### Post by dano1 on 2009-07-18
try editing pulse daemon:

disable-lfe-remixing = no

hth, danny

---

