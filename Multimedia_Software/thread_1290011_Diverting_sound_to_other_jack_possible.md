---
title: "Diverting sound to other jack possible?"
date: 2009-10-13
forum: Multimedia Software
---

### Post by varun5049 on 2009-10-13
my default sound output jack has some problem due to which the left channel output is rendered mute..
Is it possible to divert my audio output to the other jack of my sound card?
if so, how?

---

### Post by markbuntu on 2009-10-13
If you are using pulseaudio you can use the module module-remap-sink to remap the output to another jack, like from the front speaker jack to the rear speaker jack. You can read about that here.

[http://www.pulseaudio.org/wiki/Modules](http://www.pulseaudio.org/wiki/Modules)

---

