---
title: "Pulseaudio- LADSPA - dj_eq"
date: 2010-04-13
forum: Multimedia Software
---

### Post by Oliv' on 2010-04-13
Hello,

&#304;'m trying to use the PulseAudio LADSPA plugins... 
So &#304; dutifully installed pulsaudio-equalizer.
&#304;t works fine.
So &#304; decided to try to use some other plugins with pacmd, mainly the dj_eq one. &#304;mpossible to load it. Or any other one by the way. The only one which &#304; can load is mbeq (by the way if I google LADSPA the only example &#304; can find is mbeq):
load-module module-ladspa-sink sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0
 
One try &#304; made :
load-module module-ladspa-sink sink_name=ladspa_out_djeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=dj_eq_1901 label=dj_eq control=0.0,3.0,0.0

&#304;f somebody has an idea...

Oliv'

---

### Post by alejandre on 2010-04-15
Hello,

Try label=dj_eq_mono

---

