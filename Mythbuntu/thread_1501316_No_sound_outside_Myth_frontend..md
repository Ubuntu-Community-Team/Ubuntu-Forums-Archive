---
title: "No sound outside Myth frontend."
date: 2010-06-04
forum: Mythbuntu
---

### Post by pobbel on 2010-06-04
Hi,

I have Mythbuntu 9.10 working fully, and I am quit happy with it.

Everything "Myth" is working fine including sound (SPDIF), however if I want to use any applications outside of the myth frontend, I have no sound.  For example I have no sound in firefox or mplayer, I have not been able to get any sound from anything outside of myth.

How do I go about fault finding this issue?
What sort of things should I be checking?

I have done some searches and found plenty of general sound issues when setting up myth, but this is not quite the issue I have.

Any pointers would be great.
I am sure it will be something simple.

Cheers,

Paul

---

### Post by pobbel on 2010-06-04
A little further investigation has found that I am getting analog audio from the front headphone jack only.

Where can I change the settings for ubuntu to send the audio to the SPDIF output for these other applications, or is this an application by application setting?

Cheers,

Paul

---

### Post by pobbel on 2010-06-04
I managed to get this sorted.

I realised that the default audio was not the digital output and because Myth was set up to use digital it worked fine with digital out.  I was able to get all my other applications to use digital out by default, by following the steps in this link. 

[http://alsa.opensrc.org/index.php/DigitalOut#Set_digital_out_as_default](http://alsa.opensrc.org/index.php/DigitalOut#Set_digital_out_as_default)

---

