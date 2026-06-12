---
title: "Stuttering Audio in Ibex 8.10"
date: 2009-02-02
forum: Multimedia Software
---

### Post by Scienceman123 on 2009-02-02
When booting under the normal (latest) kernel, any sounds other than the bongos at the login screen are drawn out, choppy and stuttering. This occurs with OSS, PulseAudio and ALSA. Using the Realtime kernel fixes things, but is there a way to fix the sound in the more current kernel?

I am using a Toshiba Satellite A105-S2051 with an Intel Celeron M 1.7 GHz processor, and Realtek ALC681 sound.

EDIT: Problem solved. I changed the Pulseaudio configuration file daemon.conf. The last 2 lines were changed from:

default-fragments = 8
default-fragment-size-msec = 10

to

default-fragments = 25
default-fragment-size-msec = 25.

---

### Post by JoeEndUser on 2009-02-04
Thanks for coming back with the solution. That was helpful.

---

### Post by camo47 on 2009-02-15
Wow! after hours of pulling my hair out, this post helped me fix my issue. If your ever in Baltimore hit me up and I'll buy you a beer!:P 

cam

---

### Post by Steve H on 2009-02-22
> **Scienceman123 said:**
> 
Problem solved. I changed the Pulseaudio configuration file daemon.conf. The last 2 lines were changed from:

default-fragments = 8
default-fragment-size-msec = 10

to

default-fragments = 25
default-fragment-size-msec = 25.

That seems to have worked for me. I've got an M-Audio 2496 which has been giving me grief since I reinstalled Pulse Audio. It seemed to be stuttering when any other application did anything (deluge, firefox etc). I'd tried everything!! Someone else in the forums suggested something similar as you, but values were 8 and 5 respectively, made it worse.

Thanks again, I can relax again when watching films and listening to music.

:D

---

