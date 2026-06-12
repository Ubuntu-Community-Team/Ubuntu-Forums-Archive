---
title: "TIP: Fun with ALSA (multiple streams, no sound servers)"
date: 2008-12-01
forum: Multimedia Software
---

### Post by MonkeeSage on 2008-12-01
If you have a full duplex audio card, this tip will show you how to play two different audio samples at the same time, without using any sound servers (e.g., pulseaudio, jack, esd).

First we need to see if your card supports two (or more) DACs. Usually a card will have one chip with a combined DAC for playback and ADC for capture, and one with just a DAC for playback. To see if you have (at least) two DACs, run the following command:

```

cat /proc/asound/devices

```

On my box, with an old SB Live!, I get the following output:

```

  2:        : timer
  3: [ 0- 0]: raw midi
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
  8:        : sequencer

```

Lines 4-5 are the parts of interest. They tell us that on device "0," channels "1" and "0" support audio playback. That's just what we need (if there are more than one device, or more than two channels that support playback, that's fine--just change the device and channel numbers given below *per mutatis mutandis*).

Now you can do all kinds of fun things with dmix, virtual devices and mapping output channels, but just to KISS (mainly because I'm simple and stupid), we'll just focus on the case where you want to play two audio streams concurrently from applications which let you select the ALSA device and channel. In that case you can simply point one application at hw:0,0 and the other at hw:0,1--and viola!--you have two audio streams playing at the same time with ALSA, without any sound servers! Simple, eh?

For example, if you open two terminal windows (or tabs), and run this command in one:

```

mplayer -ao alsa:device=hw=0.0 foo.wav

```

...and this from the other:

```

mplayer -ao alsa:device=hw=0.1 bar.wav

```

...you should hear both foo.wav and bar.wav playing at the same time. Spiffy. :)

There is a caveat here: you can only play as many concurrent streams as you have DACs on your soundboard(s), and there is no per channel volume control (unless of course the application publishing the stream supports software mixing--many don't, though mplayer does through the -softvol command line switch).

But we can go a bit further, and even get a little bit fancy: we can run a sound server on either of the playback channels, and still have a channel free for direct alsa output. By default (i.e., if the config files haven't been hacked to cater a specific sound server like pulseaudio or jack or what-have-you), the ALSA devices "default" and "hw:0" should try to use the first channel (i.e., "hw:0,0"). This means that we can set up the sound server on the second channel ("hw:0,1"), and anything that specifically tries to use the sound server will be able to, as usual--but anything specifically trying to use ALSA's default device will be able to as well (most apps that use ALSA either let you configure the device / channel or hardcode "default" or "hw:0"). At the same time! So you could have four pulseaudio streams open, and still get a nice raw ALSA stream. Fun!

----

To set this up with pulseaudio, you need to do the following:

```

mkdir ~/.pulse
sudo cp /etc/pulse/default.pa ~/.pulse/default.pa
sudo chown $USER:$(groups | awk '{print $1}') ~/.pulse/default.pa

```

Then you need to edit ~/.pulse/default.pa (e.g., with gedit), and change the following line:

```

#load-module module-alsa-sink

```

...to:

```

load-module module-alsa-sink device=hw:0,1

```

And change the following lines:

```

.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

```

...to:

```

#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

```

Now restart the pulseaudio daemon:

```

pulseaudio -k ; pulseaudio -D

```

And *presto, chango*, you should have a sound server running on the second channel and a free default channel. Confirm with something like the following commands (again, from two terminals or tabs):

```

mplayer -ao alsa foo.wav

```

```

mplayer -ao pulse bar.wav

```

If you can hear both sounds, you get the win for great justice, and you can throw in another command just to show off:

```

mplayer -ao pulse baz.wav

```

----

To set this up with jack, you need to do the following:

Wherever you run jackd from, add thw following switch to the parameters: "-dhw:0,1". Or if you use qjackctl, enter Setup, choose "alsa" as the driver and enter "hw:0,1" as the interface. Restart jackd, and there you have it. Confirm with something like the following commands (again, from two terminals or tabs):

```

mplayer -ao alsa foo.wav

```

```

mplayer -ao jack bar.wav

```

----

To set this up with esd, you need to do the following:

Jump in your time machine. Travel back to 2002. Install GTK+-1.2...the rest is left as an exercise for the reader. :P

---

### Post by MonkeeSage on 2008-12-02
Bump (for many funs).

---

### Post by jellystones on 2011-01-15
Thanks, I love informative posts like this.

---

