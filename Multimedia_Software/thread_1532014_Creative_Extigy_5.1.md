---
title: "Creative Extigy 5.1"
date: 2010-07-15
forum: Multimedia Software
---

### Post by MikeWanDo on 2010-07-15
Let me start by saying I'm using a fairly vanilla 64-bit Lucid (at least in terms of audio). I recently got an extigy USB sound card (mainly so I could get surround from my 360 and PC at the same time and it's about the only card that will decode the AC3).

Ubuntu finds it just fine and I can see it from system>preferences>sound. In the hardware tab I can select it and choose from a variety of profiles, which includes analog surround 5.1 output + analog stereo input. With this profile selected there is a constant buzz and audio quality is awful, garbled and crackly. I checked alsamixer and everything seems fine. This [http://alsa.opensrc.org/index.php/Sound_Blaster_Extigy_%28Howto%29](http://alsa.opensrc.org/index.php/Sound_Blaster_Extigy_%28Howto%29) was a little unclear about some things but confirmed that the "channel routing mode select" in alsamixer should be 100 for the 5.1 setup I have. Nothing makes the buzzing go away except changing the audio profile to analog stereo duplex, which then allows flawless playback, but only through the front right & left speakers.

As a note, the card decodes the 5.1 AC3 from my 360 just fine and that plays back fine regardless of profile (i.e. plays back through all speakers even when the analog stereo duplex profile is selected).

Is there anyway for me to get 5.1 audio playback from media players in Ubuntu with this card?

---

### Post by gtippitt on 2012-12-19
The Extigy won't work with 5.1 since PulseAudio replaced OSS in Ubuntu distro.  

For more info, see link below:

[http://ubuntuforums.org/showthread.php?t=1322828]("http://ubuntuforums.org/showthread.php?t=1322828")

---

