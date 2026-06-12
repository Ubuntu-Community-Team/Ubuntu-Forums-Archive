---
title: "Creative Audigy NX 2 (USB Soundcard) DTS / AC3 Output"
date: 2014-08-18
forum: Multimedia Software
---

### Post by Struthio on 2014-08-18
hello,

I looked almost everywhere and couldn't make it work, maybe someone on this forum can help.

I have Logitech Z-5500 speakers which are capable od playing DTS and AC3 stream through SPDIF / TOSLINK. To allow Digital output from Notebook PC I want to use Creative Audigy NX 2 - USB Connected sound card (currently connected by TOSLINK).  

As far as normal sounds from system / applications (Stereo stream) everything work fine. Speakers correctly recognize PCM stream and play sound. Problem is with passthrough of ex. DTS stream. Speakers do not recognize that this is DTS and all I hear is a lot of static (speakers display shows PCM 2/0).

I found on some site that this is caused by Audigy internal function of raising rate to 48000 and becouse of that, it is messing information from original DTS/AC3 stream. (Can anbody confirm that?)

But even if above is true, then is there any way to force ex. ALSA to produce stream that will go unmodified through NX 2 to speakres (ex. some combination of A52/DCA ALSA plugins) ?

---

