---
title: "Can't get souind out of Rosegarden / Jack / Fluidsynth"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by davemar on 2007-06-21
I'm trying to get sound out of Rosegarden, but to no avail. I aiming on going down the soft-synth route as I've got no MIDI kit and don't want to be soundcard dependent for MIDO. So far I've done these things:

1) Installed Rosegarden, it starts up fine.
2) Installed the low-latency version of the kernel, and followed the timer resolution instructions on the UBS preparation page. This removed the problem with the low resolution timer which Rosegarden moans about.
3) Installed jack and qjack.
4) Installed fluidsynth and qsynth and downloaded a soundfont.

I had some problems getting qjackctl going without too many XURs, even though I've still got some. I couldn't get it to with with the realtime flag set; so had to use it without. 
When I try playing one of the demo music files that come with Rosegarden I see the green light flashing on qsynth suggesting it's getting MIDI data from Rosegarden, but still get no sound.

Is there anything I can do? 
It would be useful to isolate rosegarden, qsynth and qjackctl to see whether each of them is working correctly. Is there anyway I use jack with something else to ensure it is capable of producing sound?
Can it use something other that rosegarden to drive qsynth to test whether that is producing audio signals from a MIDI stream?

---

### Post by davemar on 2007-06-22
Hmmm, no answers so far...

Anyway, I've tried to nail things down a bit and started off on seeing what qsynth was doing. I downloaded pmidi as it seems to be pretty much the most basic way of playing midi files. I got that running into qsynth, who's output was going straight to alsa (no jackd used here). I now hear some audio at last, but it's not good. I get loads of buffer overrun errors from qsynth, and the sound is very choppy. I'd like to get this working smoothly first before tackling jackd. What can be the cause of these overruns and how do I deal with them?

---

### Post by fredj on 2007-06-22
Before you start with jack you should first have your sound working perfectly e.g when playing mp3 or wav
files etc.

Ok start by running qjackctl and start jack. Open the status window and see if you are getting lots of xruns.
If you are then you need to 1. stop jack 2. open the setup window and alter the frames and periods to give a
larger latency. If you are just using the ordinary kernel then you may have to set it quite high e.g 25msec or
more. Experiment until you get a setting that gets rid of the xruns. It is these overruns that cause the choppy
sound. (note it is only xruns that occur when you are playing sound that matters. The odd occasional xrun
when starting or stopping programs is unimportant)

If you want a simple way to test jack then playing a stereo audio wav or mp3 file in audacity will do. Use the
preferences item on audacity's edit menu to make sure that it is running through jack. When you have all this
sorted out then you may decide that you would like to reduce that latency figure since 5msec should be a
minimum aim but to achieve this you will have to install the Real Time kernel (look in the multimedia production
forum for that).

---

### Post by davemar on 2007-06-25
If I run Audacity on it's own the sound is perfect. But I tried playing it through jack and I still get no sound, regardless of all the tweaking I do; and still lots of xruns.
I followed the guide for jack which connects the virtual piano to it, and that doesn't work either.
I went back to trying to deal with qsynth/fluidsynth on it's own and if I make the buffer size 2048 that is the closest I get to good sound, it is nearly there but still glitches sometimes. If I make it any larger I get no sound.
Surely with low latency kernal I shouldn't be having these problems?

---

### Post by davemar on 2007-06-26
I decided to install the real-time kernel, and finally I have sound coming from Rosegarden! Unfortunately, it is pretty rough and some of the example music files get stuck notes and are pretty choppy. Even with the real-time kernel I still needed to use 1024 buffer size in qjackctl, which seems far to large a latency for should be the real-time kernel. Is there anything else I should adjust or set with the kernel or elsewhere to get this latency down to something more sensible?

At least I know I've got my rosegarden, qsynth and qjackctl connects all correct now. 

Or is my PC just too slow? It's a 1.05GHz Duron, so not leading-edge but surely still adequate?

---

### Post by rutom on 2007-12-15
I have just managed to get fluidsynth work with jack, so I decided to share my experience. Now I describe how to connect my MIDI keyboard to my laptop with integrated Intel HDA soundcard.

This is a block diagram how the sound goes from my keyboard to the speakers:

MIDI keyboard -- Midi/USB converter (EZ-MU) -- Fluidsynth -- Sound

The the trick is that you have to use the JACK over ALSA to get the satisfying result. This way the MIDI data comes from the MIDI/USB and with the help of ALSA I connect this MIDI output into the input port of the FluidSynth. Then the fluidsynth output is connected to ALSA via JACK.
JACK is needed because if the fluidsynth connects directly to ALSA then there is a big delay between pressing a button on the keyboard and when you hear the sound.

1,
First you have to start the JACK daemon.
>jackd -dalsa -dhw:0,0 -r44100 -p512 -n4 &

Some people claim that the realtime (low-latency) kernel is needed, to decrease latency, but I use standard kernel, and this settings for jack gives me 46 ms delay which is quite satisfactory. If you have a faster machine then you can decrease the -p and -n parameters to get lower latency, but for me it is OK. I can't hear the delay.

the -dalsa -dhw:0,0 means jack shall use ALSA (not OSS) and shall use the hw:0,0 soundcard which is the integrated soundcard of my laptop.

2,
Then you can start the FluidSynth:

>fluidsynth -ajack [soundfont.sf2]

This means that the sytheser shall send the synthesed sound to jack (and not to alsa directly). The second parameter is the soundfont (the file which contains the instruments sounds)

Fluidsynt has a command line interface where you can load another soundfonts and you can list the instruments in the soundfont.

3,
Finally we shall connect the USB midi interface to the fluidsynth:
The available midi ports:
>pmidi -l
 Port     Client name                       Port name
 14:0     Midi Through                      Midi Through Port-0
 20:0     E-MU XMidi1X1                     E-MU XMidi1X1 MIDI 1
128:0     FLUID Synth (6483)                Synth input port (6483:0)

Connect:
>aconnect 20:0 128:0

as you can see the 20:0 USB midi port was connected the input of fluidSynth 128:0

Now connect the audio output of fluidSynth to ALSA audio output:

List the available channels:
>jack_lsp 
JACK tmpdir identified as [/dev/shm]
alsa_pcm:capture_1
alsa_pcm:capture_2
alsa_pcm:playback_1
alsa_pcm:playback_2
fluidsynth:left
fluidsynth:right

>jack_connect fluidsynth:left alsa_pcm:playback_1
JACK tmpdir identified as [/dev/shm]
engine sample rate: 44100

>jack_connect fluidsynth:right alsa_pcm:playback_2
JACK tmpdir identified as [/dev/shm]
engine sample rate: 44100

Now you shall be able to use the keyboard. If you want to use rosegarden the probably you should not connect the midi interface of the USBMidi to the fluidsynth, but it is enough to connect the fluidsynth to ALSA.

If you don't like typing so much then you can use qjackctl to start the jack daemon and make the connections. But of course the fluidsynth must be started manually... As far as I know there are graphical frontends for fluidsynth, too.

---

