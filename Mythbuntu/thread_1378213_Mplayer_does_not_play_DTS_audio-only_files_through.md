---
title: "Mplayer does not play DTS audio-only files through HDMI"
date: 2010-01-11
forum: Mythbuntu
---

### Post by cremersdh on 2010-01-11
I got my Mythbuntu (9.04) system completely set up and have almost everything working as it should. I am using a Nvidia ION set (Asus AT3N7A-I)

I just can _not_ seem to play back DTS *_audio-only_* files over hdmi with mplayer. DTS video-files however are playing without any problem and support the DTS totally.

If I use aplay instead of mplayer I can also play my DTS audio-only files. So it must be technically possible, but I just can't figure out why mplayer does not play the file.

The DTS audio-only files are .wav files

I use Alsa 1.0.21 and aplay -l shows:
  **** List of PLAYBACK Hardware Devices ****
  card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
    Subdevices: 2/2
    Subdevice #0: subdevice #0
    Subdevice #1: subdevice #1
  card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
    Subdevices: 1/1
    Subdevice #0: subdevice #0
  card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
    Subdevices: 1/1
    Subdevice #0: subdevice #0


My /etc/asound.conf looks like this (straight forward)
pcm.!default {
       type hw
       card 0
       device 3
}
ctl.!default {
   type hw
   card 0
}

If I use mplayer I get the following error:

mythtv> mplayer -ao alsa:device=default -ac hwdts,hwac3, Norrlanda.wav

Playing Norrlanda.wav.
Cache fill:  0.00% (0 bytes)   
Audio only file format detected.
==========================================================================
Forced audio codec: hwdts
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to DTS, 1411200 bps, 44100 Hz
AUDIO: 44100 Hz, 2 ch, ac3, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [hwdts] afm: hwac3 (DTS through S/PDIF)
==========================================================================
[AO_ALSA] alsa-lib: conf.c:4600:(snd_config_expand) Unknown parameters AES0=6
[AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default:AES0=6
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
[format] Sample format big-endian AC3 not yet supported 
Couldn't find matching filter/ao format!
Audio: no sound
Video: no video

The file I try this with can be found [here]("http://www.sr.se/laddahem/multikanal/dts/norrlanda.zip")

**_Does anyone know what the problem is ?_** And what is the meaning of the message "Sample format big-endian AC3 not yet supported". The file itself is just a "Signed 16 bit Little Endian, Rate 44100 Hz, Stereo" file as aplay shows:

 aplay Norrlanda.wav 
   Playing WAVE 'Norrlanda.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

---

### Post by sailor420 on 2010-07-02
Did you ever get this figured out? I'm having a very similar problem...

---

