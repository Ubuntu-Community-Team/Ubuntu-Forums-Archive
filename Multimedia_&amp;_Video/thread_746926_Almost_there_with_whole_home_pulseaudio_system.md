---
title: "Almost there with whole home pulseaudio system"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by brw02005 on 2008-04-06
Ok got pulse audio working great. Just followed the instructions

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Went into sound and video >> PulseAudio Preferences and selected enable multicast RTP sender with loopback.

I then opened up PulseAudio Device Chooser and selected the RTP multicast as the sinc.

I then set up pulse audio on my notebook went into sound and video >> PulseAudio Preferences enable recieve multicast RTP

I then selected the multicast as a source

good to go with completely synched music streaming on both sets of speakers.  Make sure your speakers have no delay before they output or it will not be synched.  This will also never work over wireless or at least at a quality I like.  You can unicast from one PC to another over wireless but multicasting did not work for me.

I was thinking of setting up a script to use for my HTPC to create a whole audio system that will change zones and such on the fly.  I was thinking of just using ssh but was wonding if there was a cleaner way to just use the pulse audio system directly.  I realize that first I am going to have to restart any audio program after the configuration is changed since most cannot handle that on the fly but I'm pretty sure I can get this to work.

---

### Post by chayzer on 2008-05-10
Sounds like you're going for the same setup as me.. did you ever find a descent way to 'switch zones'? I guess you could say..

Maybe I should get an RFID chip implanted into my skull and have my music follow me around...

---

