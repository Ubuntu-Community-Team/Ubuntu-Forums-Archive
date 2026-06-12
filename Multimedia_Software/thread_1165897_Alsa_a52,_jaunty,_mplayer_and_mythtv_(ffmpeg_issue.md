---
title: "Alsa a52, jaunty, mplayer and mythtv (ffmpeg issue)"
date: 2009-05-21
forum: Multimedia Software
---

### Post by bilkusg on 2009-05-21
I'm posting this for two reasons. Firstly, there may be other folks out there who've had the same issue as I have, and secondly, even though I have a workaround to the problem, I'd like to think that there will be a better way to solve this going forward.

The issue: My hifi 6 channel amplifier is connected to my PC by an optical digital connection. It works really well in playing stereo CD quality sound and pre-recorded 6 channel audio using dolby digital. 
However, I also want to be able to listen to discrete 6 channel sound, and neither my soundcard nor my amp has separate analogue connections. So the only choice is to convert the 6 channels into dolby digital ( a52 ) on the fly. I know there's an ALSA a52 plugin which can do just that.

BTW:
I'm not using pulseaudio for any part of this - I've disabled it.

The problems:
1. A52 support has been removed from ubuntu as far as I can tell for patent type reasons. Unfortunately, there appears to be no clean way of getting it back using the package management system ( perhaps someone can correct me if I'm wrong )
2. It's not too hard to download the alsa-plugins source, and the ffmpeg source, and compile and install them manually. If you do that, and set up a .asoundrc appropriately, then programs like aplay work just fine. Success....
3. However, as soon as I try to use mplayer with the same output ( as a test ), I get an error: Cannot find codec engine.
4. If I try to use the device from mythtv, I get a similar error and no sound.

The explanation: ( after much digging )
The reason turns out to be that the alsa devices perform their mapping in user space, and in particular in the address space of the calling process. That means that all the references in the alsa plugin to the ffmpeg libraries are interpreted by the customised copies embedded within mplayer and mythfrontend. Neither of these works properly. In the case of mplayer that's because the jaunty mplayer has A52 disabled. In the case of mythtv it's also because the current mythtv uses an older version of the library and the unique ID of the A52 codec has changed in the meantime.

If you download mplayer and or mythtv and recompile them from source, and change the magic number in the avcodec.h header file to be consistent with the alsa plugin, it then works just fine. However, it's an awful lot of one-off customised hacking just to enable a standard plugin, and clearly not the 'right' answer.

(BTW, the other thing this allows me to do is upmix stereo to 6 channel sound via ALSA. This is the relevant .asoundrc snippet. 


pcm.a52encode6 {
  type a52
  bitrate 448
  card 0
}

pcm.stereoupmix {
  type route
  slave.pcm "a52encode6"
  slave.channels 6
  ttable.0.0 1
  ttable.0.2 1
  ttable.0.4 0
  ttable.0.5 0.2
  ttable.1.1 1
  ttable.1.3 1
  ttable.1.4 0
  ttable.1.5 0.2
}

Then if I tell programs to use ALSA:stereoupmix for output, I get sound on both front and back speakers. (And yes, for any audiophiles out there, I am well aware that the quality suffers somewhat compared to sending the raw CD stream straight out, but sometimes it's room filling noise I'm looking for.)

---

### Post by thieTe4l on 2010-08-30
seemed to stumble in the same problem, although the origninal post is 1.5 years back.

i've donwloaded and set up a52 plugin, configured an upmix device and it works just fine using speaker-test -c 2 -D myDeviceName.

However, mythfrontend gives no sound on the output. The error message is:

ALSA lib pcm_a52.c:704:(_snd_pcm_a52_open) Cannot find codec engine
2010-08-31 01:38:18.117 AudioOutput Error: snd_pcm_open(tvsurround): Invalid argument
2010-08-31 01:38:18.126 AO: Using resampler. From: 44100 to 48000
2010-08-31 01:38:18.142 Opening audio device 'tvsurround'. ch 2(2) sr 48000 (reenc 0)
2010-08-31 01:38:18.142 Opening ALSA audio device 'tvsurround'.
ALSA lib pcm_a52.c:704:(_snd_pcm_a52_open) Cannot find codec engine
2010-08-31 01:38:18.161 AudioOutput Error: snd_pcm_open(tvsurround): Invalid argument
2010-08-31 01:38:18.161 NVP(1): Disabling Audio, reason is: snd_pcm_open(tvsurround): Invalid argument

is there some solution to this by now?

br,
phil

---

