---
title: "SPDIF out not using dmix"
date: 2009-10-22
forum: Multimedia Software
---

### Post by tylernm on 2009-10-22
Hi there,

I am trying to use optical out on my AD1988B (hda-intel) audio chipset to play all audio on my pc on Ubuntu 9.04.  I have audio working but only one application can play sound at a time over spdif.  I'm not using and /etc/asound.conf or ~/.asoundrc.  I'm using the newer alsa version 1.0.21.  Any ideas:guitar:

Also it seems that when I use an audio player like songbird to play a file and subsequently open firefox to play something on youtube(flashplayer) firefox outputs audio to my analog outputs although I have specified digital out in gstreamer-properties.

Furthermore if I set my output device to analog out dmix works properly to play multiple audio streams simultaneously, so it seems spdif out is the problem.

Thanks.

---

### Post by tylernm on 2009-10-22
Solved this after trying random fixes.  But the following worked for me.

I followed these instructions to disable pulse audio

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/")
Following this guide may not be necessary

Next I put "options snd-hda-intel model=6stack-dig" at the bottom of my /etc/alsa-base.conf file.

Then I made an .asoundrc with the follwoing text ```



pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,1"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 44100		#44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
   type hw
   card 0
   device 1
}
pcm.dsp {
    type plug
    slave.pcm "dmixer"     # use our new PCM here
}
ctl.mixer {
    type hw
    card 0
}


```

 "hw:0,1" is my spdif out device.  Hope this helps someone.

---

### Post by InterceptorX on 2010-05-01
I'm having the same problem but your fix isn't working for me. You still check these forums by chance?

I'm trying to setup SPDIF over HDMI with a P5E Deluxe and a GTS 250.

---

### Post by InterceptorX on 2010-05-02
Seems that If you plug the TOSLINK cable into the port on the motherboard to the audio receiver, then back from the TV to the audio receiver, it will work.

This was on 10.04.

---

### Post by Lyude on 2010-12-21
I can't believe it... someone actually managed to get this to work. I may have left Ubuntu quite a while ago, but this thread has made me so happy ;_;.
(For anyone wondering, this worked on arch too)

---

### Post by cheako on 2012-06-02
I just tested this and it's not a real solution for surround sound:

ALSA lib pcm_direct.c:1490:(_snd_pcm_direct_get_slave_ipc_offset) Invalid type 'a52' for slave PCM
ALSA lib pcm_direct.c:1490:(_snd_pcm_direct_get_slave_ipc_offset) Invalid type 'asym' for slave PCM

Lost of things that should work don't.  I was also unable to get "hw:#,#" to work, 0,1 should be my spdif.

aplay: set_params:1059: Broken configuration for this PCM: no configurations available
To fix this, setting the rate to 48000 helped.  However it just had one issue after another and I just gave up.

---

