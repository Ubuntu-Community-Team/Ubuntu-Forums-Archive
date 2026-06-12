---
title: "Headphone Jack Not Working; Speakers Fine (Ubuntu 12.04 LTS)"
date: 2014-05-05
forum: Multimedia Software
---

### Post by Jesse_Kozub on 2014-05-05
For the past few months the audio has worked fine, but today the headphone jack is not registering with the system. I have tried ALSA Mixer and Pavucontrol, and neither worked. I saw one thread on here where people used the command ```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
``` to get driver data so that others may help. I have this data available, all I need is someone who is willing to help me through this. I should also note that I am a n00b at Ubuntu still, so forgive me if I don't understand certain terms or instructions.

Here's the data: [http://www.alsa-project.org/db/?f=c92a4954329e6b6ebe4691c41799e1db28b16a34](http://www.alsa-project.org/db/?f=c92a4954329e6b6ebe4691c41799e1db28b16a34)

Thanks in advance

---

### Post by ronb19495 on 2014-05-05
try plugging headphone in then reboot to see if they work
I am having same problem with sound card have to reboot to make alsamixer see sound card

---

### Post by Jesse_Kozub on 2014-05-06
> **ronb19495 said:**
> try plugging headphone in then reboot to see if they work
I am having same problem with sound card have to reboot to make alsamixer see sound card

No luck there, I'm afraid. I'm still hearing the sound come out of the speakers, but not the headphones.

---

### Post by Jesse_Kozub on 2014-05-06
Unfortunately, I have just learned that it is in fact a hardware issue, not a software one. I will need to get the laptop taken apart and resoldered in order for the jack to stay in place.

---

