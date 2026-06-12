---
title: "No center channel"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by CulleyS on 2007-10-21
Okay, I am giving up trying to figure this out on my own and will ask for help.  I can't get 5.1 surround sound to work, but sometimes hear sound through the center channel and sub (so I know they're plugged in and working).  When I boot up, I hear sound through the center channel.  When I run "speaker-test -c6 -twav" the center channel does not come through.

I went into Alsamixer and pushed up the volume for every single item in there.

"asoundconf list" reports only 1 soundcard for my machine:
Audigy2

I added the following to "~/.asoundrc"

#########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want. 


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}
######################################################

Still, not 5.1 surround.

I'm running Gutsy Gibbon and Audigy 2 zs sound card. 

lspci shows this:

01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

aplay -l shows this

  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My main problem is, when I use VLC and select 5.1 from audio devices, I get no center channel.  

Has anybody been able to get 5.1 surround working in Ubuntu with an Audigy2 series sound card?

Thanks in advance.

---

### Post by CulleyS on 2007-10-21
I'd like to add that when I boot into Windows XP and use VLC and select the "5.1" option from audio devices, it does work correctly.  So, I'm fairly sure it's an ALSA driver issue. :)

Any other tests I can run?

---

### Post by xjgnsdof on 2007-10-21
I concur. The surround sound on my set up (Audiy SE and 5.1 Logitech speakers) works perfectly in XP. In Ubuntu (Gusty), I only get sound from the front two speakers.

---

### Post by CulleyS on 2007-10-22
I believe I have the same speakers, or at least in the same line.  I have sound running from the "receiver" (just a display plugged into the sub) via an optical cable into my sound card.

---

### Post by xjgnsdof on 2007-10-22
I have a similar thread running, and someone posted a link to the unofficial Feisty Fawn guide on Wikipedia. The solution there takes a few seconds to implement. Here it is for your convenience:[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_and_test_surround-sound_speakers_.285.1_and_others.29_with_ALSA]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_and_test_surround-sound_speakers_.285.1_and_others.29_with_ALSA")

---

