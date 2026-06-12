---
title: "BUTWHY: pulseaudio"
date: 2008-09-25
forum: Multimedia Software
---

### Post by v.cecchetto on 2008-09-25
:)

A lot of long howto... try to summarize what i learned. Hope to help someone.

Starting from low level... hardware.

Please help me correct what i misunderstood. Thx.

1. Device-driver: ALSA DRIVER  

2. Sound-server: PULSEAUDIO

3. Audio-filter: GSTREAMER

------------------------------------------------------

3. What is an audio filter?

> is a piece of software that takes a sound file, elaborate it and give you back another sound file modified (es.: to convert from wav to mp3)

> GSTREAMER are mainly a collection of audio filters

> you can apply a filter to a sound, and after another filter and so on... (es.: wav > mp3 > ogg)

> LADSPA are other audio filters that you can use "togheter" with GSTREAMER

[http://gnomejournal.org/article/58/fun-with-gstreamer-audio-effects](http://gnomejournal.org/article/58/fun-with-gstreamer-audio-effects)

2. What is a sound server?

> Is a server... think about server on internet. Pulseaudio is a server that own the sound card on your computer. If an application wanna play on that sound card have to ask to pulseaudio. So every application have to use a pulseaudio-plugin to communicate with the pulseaudio central server.

> Pulseaudio replace the old ESD sound server.

> The correct way to speak is: an application send an audio stream to pulseaudio. Pulseaudio takes many audiostreams from vary applications and play on your sound card, without conflict. If two application try to play sound without pulseaudio they can conflict, difficult to tell who win. Perhaps the first application that gain the access to the card. With pulseaudio all the audiostreams can be mixed togheter and sent to the card.

> pulseaudio can also send the mixed stream of sound on lan or internet, to another pc. Naturally on this new pc you have to install another pulseaudio server. 

[http://mirror.linux.org.au/pub/linux.conf.au/2007/video/talks/211.pdf](http://mirror.linux.org.au/pub/linux.conf.au/2007/video/talks/211.pdf)

[http://mirror.linux.org.au/pub/linux.conf.au/2007/video/talks/211.ogg](http://mirror.linux.org.au/pub/linux.conf.au/2007/video/talks/211.ogg)

3. What is a device driver? 

> A piece of software that permit an application (VLC) to talk to an hardware device (SOUND-CARD)

[http://en.wikipedia.org/wiki/Device_driver](http://en.wikipedia.org/wiki/Device_driver)

> ALSA is a collection of driver for a lot of different sound-card

> OSS is another collection of device driver

[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System) 

> OSS is old, ALSA is new, ALSA is better, use ALSA ok? :)

------------------------------------------------------------------

Some points remains:

> pulseaudio is not a device driver, you need ALSA

> without a device driver (in case ALSA) your computer cannot play sound on your sound card

> if you have ALSA you have all you need...

> ...better if with ALSA you use also GSTREAMER and pulseaudio, no?

> ALSA is not only a collection of driver, in ALSA project you find also a sound server dmix

[http://alsa.opensrc.org/DmixPlugin](http://alsa.opensrc.org/DmixPlugin)

> pulseaudio replace dmix

> you can use LADSPA filters without GSTREAMER directly with an ALSA-plugin

[http://alsa.opensrc.org/index.php/Ladspa_(plugin)](http://alsa.opensrc.org/index.php/Ladspa_(plugin))

> Not all programs have support for GSTREAMER

> Not all programs have support for pulseaudio

> Some old programs still using OSS and not ALSA

> ... so on! 

[http://www.linux.com/feature/119926](http://www.linux.com/feature/119926)

That'all. 
:KS

---

### Post by markbuntu on 2008-09-25
What you say is true for the most part but, ALSA and OSS are also sound servers as well as device drivers and, while their device driver parts generally work quite well, their sound server parts seem somewhat lacking for many people for the things they would like to do with their computers these days.  

The biggest problem with Pulse Audio today is ignorance. If people would take a little time ( maybe an hour at the most) to figure it out and maybe read the FAQs they will find it makes a lot of things much easier. Once set up properly pulseaudio is easier to use and supports more applications than alsa or oss. There is even a pulse-jack sink that you can use to send OSS and ALSA and Pulseaudio applications at the same time to jack.

Gtreamer is a whole other thing. Gstreamer provides a compatibility layer to play the many formats not inherently supported by applications or sound servers or their device drivers. This makes the application writers job a thousand times easier as they do not have to worry about writing support into their applications for all the  codecs which are proprietary and which they may not be granted access to.

Gstreamer and PulseAudio are the future, get with it, unless you prefer spending a lot of time mucking about in terminal to get your applications to do just what you want.

---

### Post by v.cecchetto on 2008-09-26
> **markbuntu said:**
> What you say is true for the most part but, ALSA and OSS are also sound servers ... There is even a pulse-jack sink that you can use to send OSS and ALSA and Pulseaudio applications at the same time to jack.

Thx for the replay. I didn't know about these features.

> **markbuntu said:**
> Gtreamer is a whole other thing. Gstreamer provides a compatibility layer to play the many formats not inherently supported by applications or sound servers or their device drivers. This makes the application writers job a thousand times easier as they do not have to worry about writing support into their applications for all the  codecs which are proprietary and which they may not be granted access to.


Yes. I think the most explicit way to figure it out is an image.

[http://www.buzztard.org/images/c/cb/Bt-edit-0.0.1-03.png](http://www.buzztard.org/images/c/cb/Bt-edit-0.0.1-03.png)

It shows a lot of audio streams (line with arrows) that comes from different sources (pink boxes) pass throw a chain of filter in sequence (the green boxes, here is where GSTREAMER do is part) and end to a unique so called sink, the master (blue box). The master can be an other application or a hardware device that play the sound.   

> **markbuntu said:**
> 
Gstreamer and PulseAudio are the future, get with it, unless you prefer spending a lot of time mucking about in terminal to get your applications to do just what you want.

In fact GSTREAMER and pulseaudio let the sound system to be decoupled in different modules. With different modules doing different jobs, perhaps you loose something in performance but you gain a clear and more powerful way to do the things.

---

