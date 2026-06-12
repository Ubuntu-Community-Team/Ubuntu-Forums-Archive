---
title: "Mute/Change volume per application by sound mixer"
date: 2009-07-27
forum: Multimedia Software
---

### Post by ghost_zero on 2009-07-27
Hi,

actually it isn't that much of a problem but with Vista Microsoft did add one one thing that sometimes really comes in handy and that is that you are able to mute/change volume of certain apps through the sound mixer.
Therefore though the app itself doesn't allow you to mute the sound, you can do so by using the sound mixer.

Is there something equivalent for Jaunty?

---

### Post by martinbaselier on 2009-07-27
It's not possible with just alsa.(the standard sound driver) The OSS sound mixer has this option and it's the option wich uses the least memory and cpu. (see my signature for info). It should also be possible with pulseaudio, somehow.

---

### Post by ghost_zero on 2009-07-27
I thought OSS was more or less "abandoned" because it was released as closed source for a while or something like this?
Is it back as open-source now?

Regarding PulseAudio: How would this be done with PulseAudio because I believe my soundcard might not work under OSS (yet)
I have a ASUS Xonar D2X and that one isn't listed in the supported hardware section ( [http://www.opensound.com/osshw.html](http://www.opensound.com/osshw.html) ) but maybe it is supported and just not listed.

Btw.: In any case I think Ubuntu should give an easier way to choose OSS v4 instead of ALSA - I mean it isn't that hard but still not so easy as switching e.g. between PulseAudio and ALSA.

---

### Post by igorzwx on 2009-07-27
The best way is to have several Ubuntu 9.04 installed
in multiple boot.

There is Ubuntu documentation.

about OSS4 read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

you can find there (with search) a guide for pulseaudio too

---

### Post by ghost_zero on 2009-07-28
For Pulse-Audio I just had to install the pavucontrol to be able to adjust the volume accordingly.
So that one was definitely the fastest way to do this as I was using PulseAudio as Default already.

---

### Post by igorzwx on 2009-07-28
try both, of course.

---

### Post by ghost_zero on 2009-07-29
I might try OSSv4 too but not currently as it requires more time to change to OSSv4 which I currently don't have or don't want to use for this.
But really an option to easier change between this two would be great. At least at the Ubuntu installation there should be such an option. Best would be even after installation.

---

### Post by biopfeo on 2009-08-22
you should try Earcandy, which can even fade in/out volume when switching apps.
read more below, with installation guide:

[http://ubuntumanual.org/posts/235/earcandy-is-the-next-cool-thing-you-want-in-linux-if-you-are-a-media-buff](http://ubuntumanual.org/posts/235/earcandy-is-the-next-cool-thing-you-want-in-linux-if-you-are-a-media-buff)

---

