---
title: "ATI TV Wonder 600 USB 2.0 no sound"
date: 2009-11-17
forum: Multimedia Software
---

### Post by gismcieri on 2009-11-17
Hi All,

  I have been dabbling in ubuntu for the last few months and I have everything I need working except for my TV card sound.  I have researched and researched and have tried everything I can think of.  Any ideas what I am missing?  Here in the info that I have.

I am running 9.10 64bit Desktop.

sox -r 48000 -c 2 -t ossdsp --type alsa /dev/dsp1 -t alsa default

Here is the error i get from that ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp1
sox FAIL formats: can't open input  `/dev/dsp1': snd_pcm_open error: No such file or directory

I have tried various other combinations for the command and still get the same error.


cat /proc/asound/devices 
 2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0- 0]: hardware dependent
  9: [ 0]   : control
 10: [ 1- 0]: digital audio capture
 11: [ 1]   : control


cat /proc/asound/oss/devices
 0: [0- 0]: mixer
  1:       : sequencer
  3: [0- 0]: digital audio
  4: [0- 0]: digital audio
  8:       : sequencer
 12: [0- 1]: digital audio
 16: [1- 0]: mixer
 19: [1- 0]: digital audio
 20: [1- 0]: digital audio

lsmod | grep snd
snd_usb_audio         102976  0 
snd_usb_lib            19648  1 snd_usb_audio
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  6 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  7 snd_usb_audio,em28xx_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  26 snd_usb_audio,em28xx_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm


ls /dev/dsp*
/dev/dsp  /dev/dsp1

Please let me know if you need any other info.  I am a still a newb so please tell me how to run it also.

Thanks,
Matt

---

### Post by twhitney on 2009-11-24
I have the same exact issue, your same command does the same on my system too. I'm trying to follow directions listed here: [http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB#Analog_Audio_Issue](http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB#Analog_Audio_Issue) under Audio Issues.... 

Anybody have any ideas? /dev/dsp /dev/dsp1 both are there.

Any help is appreciated.

Tyler

---

