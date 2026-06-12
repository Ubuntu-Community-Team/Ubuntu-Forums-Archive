---
title: "No Center or Surround Sound on Hardy using Audigy 2 on PulceAudio with Digital Output"
date: 2008-09-28
forum: Multimedia Software
---

### Post by Mysticle31 on 2008-09-28
When I first installed this installation of hardy I remember going though and scouring the forums until I found [this]("http://ubuntuforums.org/showthread.php?t=795525") thread which allowed me to make 5.1 sound work.  I watched a couple movies and loved it.  I havn't watched a movie in a couple months, as I last recall surround sound via analog jacks was working perfectly.  

Just recently I changed speakers and added a Denon Receiver to power them an provide Dolby ProLogic IIx for Music.  I'm using the Coaxial connection of my Audigy 2.  No channels besides front left and front right work!

I've tried the comprehensive guide, which didn't talk much about surround sound.  I've tried editing ~/.pulse/default.pa and adding > load-module module-alsa-sink device_id=0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe

I've tried playing in asoundrc.

I still see only two channels in the PulceAudo Volume meter and speaker-test only outputs on font left and front right.  The other channels are dead.

Thoughts? Advice? Suggestions? --shoot it?

---

### Post by markbuntu on 2008-09-28
Digital Output is not generally recognized by Pulseaudio so it needs to be setup in the alsa mixer or in the application like in Mplayer or vlc where there are options to direct the sound output in stereo or surround to the digital output. vlc also has a dolby digital option.

There is a discussion here about pulseaudio and secondary devices like digital sound:

[http://www.pulseaudio.org/ticket/139](http://www.pulseaudio.org/ticket/139)

There is also this from alsa:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

---

