---
title: "New Ubuntu install Using Motu M4 as  interface"
date: 2024-09-16
forum: Multimedia Software
---

### Post by Dirk_Ouellette on 2024-09-16
I just installed  Ubuntu 24.04.1 LTS after dealing with Manjaro, because my Motu M4 worked out of the box on Manjaro. I don't like Manjaro, so can someone point me to connecting my M4 so I can use Reaper on Ubuntu? Thanks.

---

### Post by bobunderwood99 on 2024-09-16
Are you using the Pro Audio profile? I'd install the PulseAudio Volume Control (pavucontrol) to find out.

---

### Post by Dirk_Ouellette on 2024-09-20
Thank you bobunderswwod99.  I'm not quite sure what happened, but after I;   {    $ sudo apt install jackd2 qjackctl pulseaudio-module-jack a2jmidid;,}    everything began working like a hot damn! Whooee!

---

### Post by bobunderwood99 on 2024-09-20
You should know that by installing jackd2 you're not really using Pipewire anymore. Your computer will act more like a legacy ALSA/JACK/PulseAudio system.

---

