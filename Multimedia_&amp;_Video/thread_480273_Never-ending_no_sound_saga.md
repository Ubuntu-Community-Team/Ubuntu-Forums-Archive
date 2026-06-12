---
title: "Never-ending no sound saga"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by johntkucz on 2007-06-21
I have a mx3701 gateway, ATI SB450 sound (sound card?)

 tried this "fix" 
options snd-hda-intel probe_mask=8 model=3stack

with the same HDA-Intel sound card, with the same modem "ambiguity"

card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0

but upon reboot ended up with aplay -l
222: no devices found error

so I undid that and am still stuck! Help

---

### Post by johntkucz on 2007-06-21
By the way, I'm running Feisty Fawn 7.04. Do I have to download and install additional alsa-drivers?

---

### Post by johntkucz on 2007-06-21
okay,
from the main trouble-shooting document
I tried

    *

      Add the following line to the file, replacing '3stack' with your model (see below)

options snd-hda-intel model=3stack

replacing 3stack with 'ref', which I think is my model number.  
Now in alsamixer there's a third bar 
Master, PCM, and now LFE (and an IEC958)

Any insights onto those for SigmaTel Stac9200 soundchips?

Thanks a ton.

---

### Post by johntkucz on 2007-06-21
The alsamixer always boots with Master and LFE muted.  I unmute them, pres 'esc', but upon each new reboot, they're muted! Any suggestions? Thanks.

---

### Post by johntkucz on 2007-06-21
HEllo?? This is incredibly infuriating!

---

### Post by Gremlinzzz on 2007-06-21
did you try the ubuntu feisty guide under sound? [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Gremlinzzz on 2007-06-21
Dont know if theres a answer but ya might want to look at these sites
[http://www.google.com/search?hl=en&q=ATI+SB450+sound&btnG=Google+Search](http://www.google.com/search?hl=en&q=ATI+SB450+sound&btnG=Google+Search)

---

### Post by Gremlinzzz on 2007-06-21
One post says that updating the ALSA drive fixed his problem
[http://ubuntuforums.org/showthread.php?p=2798055#post2798055](http://ubuntuforums.org/showthread.php?p=2798055#post2798055)

---

