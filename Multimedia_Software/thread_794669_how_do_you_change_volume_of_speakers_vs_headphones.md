---
title: "how do you change volume of speakers vs headphones?"
date: 2008-05-14
forum: Multimedia Software
---

### Post by kl324 on 2008-05-14
Right now I have two "speakers" plugged in: 1 set that came with my dell, and some headphones on the front jack. The headphones are at the right volume but the speakers I have to turn the dial all the way to hear it at all. Is there some way I can make the speakers louder without making the headphones louder?

---

### Post by Islington on 2008-05-14
Are you using pulse audio? if so try this [http://tombuntu.com/index.php/2008/04/10/adjust-volume-of-individual-applications-with-pulseaudio/](http://tombuntu.com/index.php/2008/04/10/adjust-volume-of-individual-applications-with-pulseaudio/)

it would be under output tab.

---

### Post by kl324 on 2008-05-14
Hm, I got pavucontrol like he said, but there seems to be only 1 output device: ALSA PCM on front:0 (ALC662 Analog) via DMA
This is odd, because I just checked and both the speakers and headphones are working.

---

### Post by Islington on 2008-05-15
only 1 hardware output device? check the show: box at the bottom right.

---

### Post by kl324 on 2008-05-15
Yup, just one.
is it possible I need drivers or something?

---

### Post by Stochastic on 2008-05-15
Pulse Audio is just a soft layer that will be sending to your alsa drivers.  Try doing ```
sudo apt-get install alsamixer
``` then running alsamixer and manually raising the volumes of whichever channel you have your speakers plugged into.

---

### Post by kl324 on 2008-05-15
All the channels on alsamixer raise the volume of the headphones and speakers in unison. However, there is a headphone channel - with no volumebar and stuck at 0. The headphone switch on the gui frontend is on though...

---

### Post by cariboo on 2008-05-15
The reason the headphone and speakers both go up in volume  when raising the volume level is that they are essentially the same output. Check you sound card for extra outputs if you want to have different volume levels for speakers and headphone.

Jim

---

