---
title: "pchdtv 5500 No Sound 11.10/11.04 64bit"
date: 2011-10-23
forum: Mythbuntu
---

### Post by g8keepR on 2011-10-23
Hello,

I'm running ubuntu 11.10 64bit and have a pchdtv 5500 card that I use with mythtv, along with my HD Homerun.

For whatever reason, I cannot get sound while using this card.  I see it in pulse audio, it is receiving audio.  I can use the built in Sound Record app , click record and I get audio fine.

In mythtv I have it set to capture from ALSA:default ( also tried ALSA:pulse) and nothing ...

The modules also seem to be loaded fine :


dmesg:
[    8.657628] cx2388x alsa driver version 0.0.8 loaded
[    8.657881] cx88_audio 0000:03:07.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.659240] cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected], frontend(s): 1
[    8.659242] cx88[0]: TV tuner type 64, Radio tuner type -1
[    8.660679] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[    8.661048] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
...
[    9.488282] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[    9.488427] cx8800 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.488434] cx88[0]/0: found at 0000:03:07.0, rev: 5, irq: 21, latency: 32, mmio: 0xfa000000
[    9.491061] cx88[0]/0: registered device video1 [v4l2]
[    9.491083] cx88[0]/0: registered device vbi0
[    9.491400] cx88[0]/2: cx2388x 8802 Driver Manager
[    9.491409] cx88-mpeg driver manager 0000:03:07.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.491417] cx88[0]/2: found at 0000:03:07.2, rev: 5, irq: 21, latency: 32, mmio: 0xf8000000


The only thing I can see in the terminal where I run 'mythfrontend' is a lot of ALSA, Error: WriteAudio: buffer underrun' messages.

My setup ran fine when I was on 10.04 and 10.10 (32bit), but since I made the move to Natty 64 bit (fresh install ) and my update today to 11.10, it's not functioning correctly for some reason.

Any ideas?

---

### Post by g8keepR on 2011-10-23
I should also note, I'm using - 2:0.24.0+fixes.20110908

---

### Post by g8keepR on 2011-10-23
2 more bits of info :

1) one the digital side - the card works fine ( with sound )

2) when I do a 'lsmod' I see the module is loaded:

lsmod | grep snd 
snd_usb_audio         118064  2 
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96755  4 snd_usb_audio,cx88_alsa,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  28 snd_usb_audio,snd_usbmidi_lib,cx88_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

---

### Post by g8keepR on 2011-10-23
One final update for the day, I just updated to 2:0.24.1+fixes.20111019.27447  ... still having the same issue

---

### Post by klc5555 on 2011-10-24
It's been a very long time since I've set up and used the analog half of one of these cards. Myth 0.20.2, I think. But as I recall, the analog side of these cards tends to dump audio to an analog  /dev/ node that is other than alsa:default. Your analog card may have defaulted to a device node that your machine is not set up for.

If you go into the backend setup for the analog half of this card (under Capture Cards), you should have a drop-down menu with a range of potential analog /dev/ nodes for the audio of the analog half of the card to go to, e.g. /dev/dsp , /dev/dsp1, etc. Or other similar. If you have a range of /dev/ possibilities for the sound device for this analog card, try the lot of them and see if one works for you.

---

### Post by g8keepR on 2011-10-24
Yes, I remember it used to have /dev/dsp in an earlier version.  Unfortunately, I have neither the device /dev/dsp, nor any other options besides ALSA:default in the mythtv-setup.

---

### Post by g8keepR on 2011-10-28
bump.

---

### Post by g8keepR on 2011-11-02
I've also tried ALSA:pulse.  I can see ( in the Sound Settings -> Input ) that the input is picking up audio, but it's not coming from my speakers.

---

### Post by g8keepR on 2011-11-05
Ok, I finally solved my problem.  I went into mythtv-setup under the capture card and set the sound input to ALSA:hw,1.0 and it worked!

---

### Post by smuggly on 2012-01-15
Are You Using The  ATI Propietary Drivers Per Chance?

---

### Post by g8keepR on 2012-01-21
No, I am not ( nvidia drivers )

---

