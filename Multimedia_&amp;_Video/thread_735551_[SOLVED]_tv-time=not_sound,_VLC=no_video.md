---
title: "[SOLVED] tv-time=not sound, VLC=no video"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by virx on 2008-03-25
I have reached to funny situation during getting sound to work with ASUS Hybrid P7131 (SAA7134 chip) - in TV-time I can change volumebar value but have no sound, but in VLC I can get sound and no video.

TV card has not such feature to connect its audio output to sound card line-in.

Only solution for "normally" watching TV is starting VLC Capture device:
video device name: /dev/video0 - that is correct
audio device name:  /dev/dsp1 - that must be correct
sample rate 32000: higher causes noise
frequency: correct from cable company website

I can hear audio (don't know if it is correct channel audio), but no video at all. Next step is to open TV-time and after changing channel, I can hear channel audio. Now I can change channels from TV-time and change volume level from VLC ;) Finding that solution took few times kernel+modules compiling and accidentally discovered that my TV-tuner can make sound. 

Any ideas how to get sound to TV-time or video to VLC?

---

### Post by virx on 2008-03-26
Nevermind after writing this topic I checked my TV-card again and it has an audio output connector - a little smaller than CD analog audio connector on sound card, but a little knife work and CD audio cable fits there and now I have sound in TV-time out-of the box...

Just in case somebody with same card but without audio output (I read about them when looking for solution) then for me getting sound out without cable was possible with those guides: Most important is to compile saa7134-alsa module:

[http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134) - getting "Philips SAA7134 DMA audio support" you must include ALSA as module before - look next link
[http://www.gentoo.org/doc/en/alsa-guide.xml](http://www.gentoo.org/doc/en/alsa-guide.xml) - getting /dev/dsp and /dev/mixer device you must include   
<M> Sequencer support
   (Old style /dev/mixer* and /dev/dsp* support. Recommended.)

---

### Post by bve on 2008-06-04
Thanks for the tip on the audio connector, I had suspected that's what it was, now TVTime is enjoyable to use.

Do you have any hints on getting your remote to work?

---

### Post by virx on 2008-06-09
Sorry, for me it worked out of the box.

---

