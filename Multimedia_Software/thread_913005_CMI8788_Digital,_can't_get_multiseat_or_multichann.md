---
title: "CMI8788 Digital, can't get multiseat or multichannel"
date: 2008-09-07
forum: Multimedia Software
---

### Post by jbalentine on 2008-09-07
I have a HT Omega Claro Plus sound card, using the Digital Outputs to a receiver.  I have tried several settings to get output to work 'the way I would like it to' which means at minimum 5.1, with stereo upmixing, and multiplexing across multiple users for a multi-seat setup.  What I have had luck with was 5.1 upmixing through the use of the a52 plugin for alsa, unfortunately I can not get multiplexing going when I set things up like this. Here is the .asoundrc I used..

> 
# For a52 encoding
pcm.a52encode {
    type a52
}

# To upmix stereo to 6 channels.
pcm.!default "stereoupmix"
pcm.stereoupmix {
	type upmix
	slave.pcm "a52encode"
	channels 6
}


So when I try to setup for multiplexing by using the PulseAudio sound server I only get 2 channel output.  Also, only one user can have output at a time.  This is loading pulseaudio using --system in my rc.local startup file.

So that leaves me with a few questions; 
How can I setup sound for a multi-seat configuration, where multiple users logged in can all get sound playback simultaneously?  

How can I get PulseAudio to upmix 2 channel sound to 5.1 or 7.1 channel sound, or atleast play 7.1 or 5.1 when it should instead of 2 channel all the time?

Are there better alternatives to PulseAudio for sound servers?

---

