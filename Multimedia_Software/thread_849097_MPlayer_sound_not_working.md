---
title: "MPlayer sound not working"
date: 2008-07-04
forum: Multimedia Software
---

### Post by impel on 2008-07-04
For the life of me, I cannot get my sound to work with MPlayer. I have previously been using either Totem or VLC to play movies, but I downloaded MPlayer based on what I heard about it.

I am using an old Soundblaster Live card (because onboard sound died on me and I needed a cheap fix). I was actually amazed that Ubuntu picked it up on install.

It is being configured with Alsa mixer yet in MPlayer, if I choose alsa it doesnt work. I've gone through each open and tried it - Restarting MPlayer each time. A few times it screwed MPlayer up and I couldn;t open it without freezing. It finally fixed and I am able to get back in, but I can't get sound to work at all.

I guess I'll be fine with VLC or Totem, but I did like the interface of MPlayer and really would like to use it.

--------------------------

EDIT. I just realized its not that sound doesn't work with MPlayer, it is that my sound ONLY works in Totem.

Sound configured in System>Preferences>Sound is Multichannel. That is the only setting that works correctly.

---

### Post by Archmage on 2008-07-04
Actually if you go in the terminal you can play a file with the following option

```
mplayer File.avi
```

At that output you should see what it is wrong.

And with the following option you can choose the audio-output:

```
mplayer File.avi -vo XXX
```

XXX can be:
Available audio output drivers are:
 
 alsa
 
 ALSA 0.9/1.x audio output driver
 
 noblock
 
 Sets noblock-mode.
 
 device=<device>
 
 Sets the device name. Replace any ’,’ with ’.’ and any ’:’ with ’=’ in the ALSA device name. For hwac3 output via S/PDIF, use an "iec958" or "spdif" device, unless you really know how to set it correctly.
 
 alsa5
 
 ALSA 0.5 audio output driver
 
 oss
 
 OSS audio output driver
 
 <dsp-device>
 
 Sets the audio output device (default: /dev/dsp).
 
 <mixer-device>
 
 Sets the audio mixer device (default: /dev/mixer).
 
 <mixer-channel>
 
 Sets the audio mixer channel (default: pcm).
 
 sdl (SDL only)
 
 highly platform independent SDL (Simple Directmedia Layer) library audio output driver
 
 <driver>
 
 Explicitly choose the SDL audio driver to use (default: let SDL choose).
 
 arts
 
 audio output through the aRts daemon
 
 esd
 
 audio output through the ESD daemon
 
 <server>
 
 Explicitly choose the ESD server to use (default: localhost).
 
 jack
 
 audio output through JACK (Jack Audio Connection Kit)
 
 port=<name>
 
 Connects to the ports with the given name (default: physical ports).
 
 name=<client
 
 Client name that is passed to JACK (default: MPlayer [<PID>]). Useful if you want to have certain connections established automatically.
 
 (no)estimate
 
 Estimate the audio delay, supposed to make the video playback smoother (default: enabled).
 
 nas
 
 audio output through NAS
 
 macosx (Mac OS X only)
 
 native Mac OS X audio output driver
 
 openal
 
 Experimental OpenAL audio output driver
 
 pulse
 
 PulseAudio audio output driver
 
 [<host>][:<output sink>]
 
 Specify the host and optionally output sink to use. An empty <host> string uses a local connection, "localhost" uses network transfer (most likely not what you want).
 
 sgi (SGI only)
 
 native SGI audio output driver
 
 <output device name>
 
 Explicitly choose the output device/interface to use (default: system-wide default). For example, ’Analog Out’ or ’Digital Out’.
 
 sun (Sun only)
 
 native Sun audio output driver
 
 <device>
 
 Explicitly choose the audio device to use (default: /dev/audio).
 
 win32 (Windows only)
 
 native Windows waveout audio output driver
 
 dsound (Windows only)
 
 DirectX DirectSound audio output driver
 
 device=<devicenum>
 
 Sets the device number to use. Playing a file with &#8722;v will show a list of available devices.
 
 dxr2 (also see &#8722;dxr2) (DXR2 only)
 
 Creative DXR2 specific output driver
 
 ivtv (IVTV only)
 
 IVTV specific MPEG audio output driver. Works with &#8722;ac hwmpa only.
 
 v4l2 (requires Linux 2.6.22+ kernel)
 
 Audio output driver for V4L2 cards with hardware MPEG decoder.
 
 mpegpes (DVB only)
 
 Audio output driver for DVB cards that writes the output to an MPEG-PES file if no DVB card is installed.
 
 card=<1&#8722;4>
 
 DVB card to use if more than one card is present. If not specified mplayer will search the first usable card.
 
 file=<filename>
 
 output filename
 
 null
 
 Produces no audio output but maintains video playback speed. Use &#8722;nosound for benchmarking.
 
 pcm
 
 raw PCM/wave file writer audio output
 
 (no)waveheader
 
 Include or do not include the wave header (default: included). When not included, raw PCM will be generated.
 
 file=<filename>
 
 Write the sound to <filename> instead of the default audiodump.wav. If nowaveheader is specified, the default is audiodump.pcm.
 
 fast
 
 Try to dump faster than realtime. Make sure the output does not get truncated (usually with "Too many video packets in buffer" message). It is normal that you get a "Your system is too SLOW to play this!" message.
 
 plugin
 
 plugin audio output driver


Late you can put this in your .mplayer/config to store the setting.

---

### Post by impel on 2008-07-04
Thanks for the response. I will look into that.

EDIT. I just realized its not that sound doesn't work with MPlayer, it is that my sound ONLY works in Totem.

Sound configured in System>Preferences>Sound is Multichannel. That is the only setting that works correctly.

---

