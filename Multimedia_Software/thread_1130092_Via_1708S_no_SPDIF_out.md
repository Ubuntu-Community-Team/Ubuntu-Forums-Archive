---
title: "Via 1708S no S/PDIF out"
date: 2009-04-19
forum: Multimedia Software
---

### Post by gus_zernial on 2009-04-19
I posted this before and got no response - hoping someone might
have relevant experience. I have an ASUS M4A78T-E motherboard system running Kubuntu Jaunty 9.04 with a custom 2.6.28.9 kernel. I am getting sound out the Line Out/Speaker Out jacks, but no sound through the Toslink S/PDIF Out jack.

This motherboard has 7.1 channel HD Audio out using Via VT1708S chip,
(plus HDMI out). This is a dual-boot system and everything, including S/PDIF out, works fine with WinXP.

But on Linux, aplay -L doesn't show the S/PDIF channel, see below. And no S/PDIF slider shows in alsa mixer.

I'm running alsa driver, library and utilities version 1.0.19. The correct sound modules appear to be loaded - see lsmod output below.
I've tried various "model=" options for snd_hda_intel, see modprobe output below, and none that I've tried activate the S/PDIF out.

Has anyone gotten this to work?

$ aplay -L
default:CARD=SB
    HDA ATI SB, VT1708S Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=HDMI
    Default Audio Device
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

$ lsmod | grep snd
snd_hda_codec_atihdmi    11776  1
snd_hda_codec_via      36356  1
snd_hda_intel          33736  3
snd_hda_codec          76928  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              15492  1 snd_hda_codec
snd_pcm_oss            45984  0
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83076  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            39424  0
snd_seq_midi_event     15360  1 snd_seq_oss
snd_seq                57584  4 snd_seq_oss,snd_seq_midi_event
snd_timer              29448  2 snd_pcm,snd_seq
snd_seq_device         15500  2 snd_seq_oss,snd_seq
snd                    66724  16 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              15456  1 snd
snd_page_alloc         17160  2 snd_hda_intel,snd_pcm

$ modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p'
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: model=6stack-digout

---

### Post by one51 on 2009-05-04
I had a similar problem with an M4A78 Pro.  Seems there is a bug in Asus' implementation of the VT1708S chip.

Found someone here: [http://news.gmane.org/gmane.linux.alsa.devel](http://news.gmane.org/gmane.linux.alsa.devel)
who had hacked the source for the Alsa version to get it working.  I think he was asking for a mod in Alsa to get it working for that MB.  Post name is "spdif/iec958 outputs at VT1708S not recognized" (not sure how to do a direct link).

I ran the Alsa upgrade script from [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
...And did the "download only" option, then modified the source, then installed.  I had to grep for the proper file using the clues from the source mod above.

The digital audio worked!... ONCE.  I turned the system on again (a few days later) and it somehow didn't work.  I've tried everything and still stuck.  In fact I disabled Pulseaudio, now am much closer to a working system (and no pops or clicks in the analog audio).  But it's frustrating me to h*ll that digital seems to be there, in all the setup options, but somehow doesn't work even though it once did (and I changed nothing since then).  GRR

Good luck, let me know if you get it working and I might take an image of your HD  ;-)

---

### Post by The Sam on 2009-06-13
The toslink should be an S/PDIF pass-through. When using S/PDIF pass-through, the sound card does not process or alter the digital signal in any way (hence the term "pass-through") so the would be no volume slider for the S/PDIF output. 

Turn on the IEC958 output on your mixer and make sure  the IEC958 loopback is off and you should get output.

Your mobo also has an S/PDIF header you could use. You don't even need a sound card to do this, just a 35 cent cable and an adapter card (Asus makes one with coax and toslink for about five bucks). 

If all else fails you can buy yourself a cheap sound card with S/PDIF and install that. The analog quality of the card is unimportant because all the card is doing is passing data in the form of .5v pulses on coax or light pulses on toslink. Turtle beach makes a card called a Riviera that you can pick up for about $25 that I have used in Kubuntu 9.04 based HTPC's.

---

### Post by one51 on 2009-06-16
Interesting to know.  Maybe I can play with the IEC958 checkboxes, there are 3 not-well-described ones (but I've tried every combination 10x already).  Maybe one is loopback.

I'm still hoping that someday the built-in stuff will work.  I'm trying to live on a budget at the moment so don't want to buy several $25 cards (replace built-in sound and video).  That was the reason I bought an integrated mobo in the first place, but the Linux drivers and Asus BIOS just have too many glitches.  Maybe the next Alsa will have a hard patch for this (motherboard BIOS) sound bug.

---

