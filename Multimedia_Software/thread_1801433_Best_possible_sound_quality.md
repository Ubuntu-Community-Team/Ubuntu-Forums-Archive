---
title: "Best possible sound quality"
date: 2011-07-10
forum: Multimedia Software
---

### Post by Sorensiim on 2011-07-10
I've been upgrading my listening setup at my desktop computer so now I *just* need to figure out how to get the best possible sound from it :D

My sound card is an Asus Xonar DS, connected via toslink to my DAC, a "Pop Pulse Super Pro 707" (gotta love the names given to Chinese hifi!) which is capable of handling up to 24bit/192KHz which is also the upper limit of the sound card. The DAC then feeds my amp which drives my speakers and headphones. 

I've been looking at /etc/pulse/daemon.conf and been tinkering with the settings as per the [manpage here]("http://linux.die.net/man/5/pulse-daemon.conf"). Most of that tinkering, however, has ended in either no sound, a daemon that won't start or horrible hissing and static instead of sweet music.

Is there a great (noob-friendly) guide for configuring the Pulseaudio daemon for the best possible sound?

---

### Post by snapback77 on 2011-07-10
I think you will eventually end up with MPD and some client, Sonata, GMPC, etc. MPD, Sonata, GMPC and others are available in 10.10 Ubuntu Software center or you can install via terminal: sudo apt-get install MPD.  Same for Sonata.  Nothing less will satisfy you.

---

### Post by Sorensiim on 2011-07-11
So I got MPD set up and configured, pointed it to my music, set it up for pulseaudio and it plays my music alright... Unless I use anything else for playback, ie. opening a file in VLC. From then on, no sound in any MPD clients. Seems like they don't like Pulseaudio.

Is there any way to have bit perfect audio in Ubuntu?

---

### Post by Sorensiim on 2011-07-12
Screw MPD, I found a better (for me) solution :)

Clementine, my favorite music manager can actually be set up bypass Pulseaudio and access the hardware directly through ALSA. Just set the GStreamer sound engine (in Clementine Preferences) to use Audio sink (ALSA) and set the "Output device" to the (ALSA) hardware address you want. For me, my ASUS Sound card is unit 0 and the digital output of that card is output 1. So I just need to enter "hw:0,1" as my output device. Now my DAC is being fed 16/44.1 when I play those files and 24/192 when I play that. No resampling in Clementine anymore!

---

### Post by daniel227 on 2011-11-19
hei sorensiim,
i stumbled upon your answer recently...

i have changed from windows to linux at the same time as changing from one old laptop to another. i have definitely noticed that sound quality isn't so good now, especially bass seems to be rather poor (i have it turned up fully on my active speakers - they are still the same as with the old setup - but still i'm setting up my eq for more :-).

i'm wondering if this is due to the sound card or linux.

i have now a SiS ac'97 sound controller on an amilo, before that i used an equally old compaq.

it seems that apart from alsa i have jack installed, but as you suggested i set up clementine to go straight to alsa.

i can't notice a difference either way.

what about pulse audio, does it improve sound quality?

another question is about clementine which you inspired me to use. i quite like it, but it doesn't seem to have too many features? not many things can be adjusted in the preferences, there don't seem to be any keyboard shortcuts, no plugins...?
i'm not criticizing a project in development, just asking if i'm missing something!

greetings,

daniel

---

### Post by tartalo on 2011-11-19
> **daniel227 said:**
> what about pulse audio, does it improve sound quality?

PulseAudio relies on ALSA or OSS for the output, I don't see how an extra software layer can improve sound quality, in fact in the past there have been many complains about latency:
[http://rudd-o.com/en/linux-and-free-software/how-pulseaudio-works/imageshttp://rudd-o.com/en/linux-and-free-software/how-pulseaudio-works](http://rudd-o.com/en/linux-and-free-software/how-pulseaudio-works/imageshttp://rudd-o.com/en/linux-and-free-software/how-pulseaudio-works).

If sound output seems weak try turning up the volumes in alsa-mixer (command line)

---

### Post by daniel227 on 2011-11-19
> **tartalo said:**
> PulseAudio relies on ALSA or OSS for the output, I don't see how an extra software layer can improve sound quality, in fact in the past there have been many complains about latency:

yes, i thought so... 

> **tartalo said:**
> If sound output seems weak try turning up the volumes in alsa-mixer (command line)

yes, it can do miracles sometimes cant it... :guitar:

... still i hope to find out more about clementine...

---

