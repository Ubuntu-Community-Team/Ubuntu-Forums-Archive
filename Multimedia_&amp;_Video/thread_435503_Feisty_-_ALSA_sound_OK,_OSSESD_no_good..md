---
title: "Feisty - ALSA sound OK, OSS/ESD no good."
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Eckhart on 2007-05-07
Greetings,
  I recently installed Feisty onto my desktop here, to find that sound from Flash in Firefox wasn't working - However, sound in XMMS and Rhythmbox does work.  System sounds such as the logon/off sounds don't play, either.  

I use a HeadRoom Total BitHead through USB as an external sound card/DAC - In windows it used default USB Audio drivers, and here it seems to do the same, too.

When I switch sound in XMMS over to OSS from ALSA, it fails to play as well.  VLC sound started coming through after I refreshed the ALSA device listing and selected the correct device, however it wasn't the default on the list even though I set it to be default for ALSA.  Movie Player and Firefox alike don't give me sound - Movie Player itself reports "Could Not Open Resource for Writing".  I have the FIREFOX_DSP set to "aoss".

The device is all set up correctly in System>Preferences>Sound, with it being in every box short of Capture, and having it as (ALSA Mixer) selected in the mixer box.  However, sounds from the Sounds tab do not play when the Play buttons are pushed, nor can I hear them elsewhere.

Hence, I figure this problem boils down to OSS or ESD.  I'm posting because I seem to have hit a dead-end on my own research both here and on Google regarding this problem.  Anyone have any ideas, and willing to help a Linux n00b?

Be gentle.
 - Eckhart

Edit; It seems my USB Audio is mapped to /dev/dsp1 while my microphone is /dev/dsp0 for some reason - When I specify /dev/dsp1 and /dev/mixer1 in XMMS it works where as it doesn't with the defaults - How do I change the defaults over in OSS? O.oa


Solution for anyone having this problem;
I changed /etc/asound.conf to;
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:1,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}


The problem was at the pcm "hw:1,0" line, it used to read 0,0.

---

