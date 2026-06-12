---
title: "Blue Snowball - JACK set up"
date: 2008-12-03
forum: Multimedia Software
---

### Post by hmandmpsaunders on 2008-12-03
I have got the Blue Snowball USB microphone working in Ubuntu Studio. There are a number of posts on the difficulty of doing this. I am happy to share my setup. Let me know what info I should post.

Malcolm

---

### Post by markbuntu on 2008-12-03
Just post a clear explanation of how you did it, step by step if possible. Post it right here.
I will add a link in my guide.

---

### Post by chongzi35 on 2008-12-03
Through conduit **[cast steel valves](http://www.valvesupplier.net/cast-steel-gate-valves.htm)** are designed for oil & gas pipeline service. Featured with double block and bleed function, the [cast steel valve]("http://www.valvesupplier.net/cast-steel-gate-valves.htm") is suitable for bi-directional flow isolation.

---

### Post by hmandmpsaunders on 2008-12-04
Here are my audio settings in Ubuntu Studio 7.10. 

Blue Snowball serial no S-N088540 (package also has no 76-088540 Apple Part # TF238LL/A) plugged into USB at front of DELL VOSTRO 400. Output - onboard soundcard.

Gnome ALSA mixer settings

REALTEK ALC888

  PCM max
  Front max
  Line max
  Other faders 0
  No capture checkboxes ticked

USB Mixer
  Mic 70%
  Rec checkbox ticked

Start /user/bin/qjackctl

Use Jack control GUI to give parameters below. Here are the messages on starting JACK.

/usr/bin/jackd -R -P10 -dalsa -r22050 -p256 -n4 -D -Chw:0 -Phw:2 -s -S -i1 -o2
14:42:47.855 JACK was started with PID=5917 (0x171d).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 22050
creating alsa driver ... hw:2|hw:0|256|4|22050|1|2|nomon|swmeter|soft-mode|16bit
control device hw:2
configuring for 22050Hz, period = 256 frames, buffer = 4 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 4 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 4 periods for playback
playback and capture sample rates do not match (44100 vs. 22050)
14:42:48.866 Server configuration saved to "/home/malcolm/.jackdrc".
14:42:48.868 Statistics reset.
14:42:49.018 Client activated.

Run Patchage

Display shows input alsa_pcm capture_1 (the Snowball USB mic) and outputs alsa_pcm playback_1 and 2.

JACK enabled applications can now be started and configured to use the Snowball mic input. I have not tinkered with the JACK settings to achieve best latency. 

I hope this info is useful.

Malcolm

---

### Post by michaelomichael on 2008-12-27
Hi,

Malcolm - thanks so much for taking the time to post your settings.  I've just got a Snowball USB mic myself and spent many hours trying to get it to work properly with JACK, so I'm going to add my own setup details and troubleshooting details here too. 

I had assumed that the main problem would be that my soundcard natively runs at 48000 Hz whereas the output of the Snowball is 44100 Hz.  I used the 'arecord' and 'aplay' command-line tools to record and playback the microphone input which showed that at least ALSA was able to handle the signal, so I had some confidence that it could be made to work with JACK.

When I tried configuring JACK to use the USB audio input I got a *lot* of xruns, and connecting capture_1 to playback_1 sounded pretty bad.  I was trying a bunch of different options with /usr/bin/jackd on the command-line and the results varied between 'really slow and echo-y' and 'horrific noise'.

Malcolm's suggestion of calling jackd with the '-r 22500' option put me on the right track for sorting out the slowness.  I needed to run jackd at *half* the samplerate of my built-in sound card.  I suspect that his sound card natively ran at 44100 Hz because my own mic now sounded *almost* in pitch, but was still about a semitone too low.  Attempts to change the rate to 24000 Hz in jackd were ignored; for some reason it was always choosing the nearest value that was a factor of 44100 (i.e. it chose 22500 instead of 24000).

Finally, I went back to messing around with a [~/.asoundrc]("http://alsa.opensrc.org/.asoundrc") file and had some luck.  I added an entry that looks like this:
```
pcm.snowball48k {
    type plug
    slave {
        pcm "hw:1,0"
        format S16
        channels 1
        rate 48000 
    }
}
```

Setting the 'rate' parameter in the .asoundrc file seemed to do the trick.  Now, I tried starting jackd with the following parameters and it used the 24000 samplerate value instead of changing it to 22500!:
```
jackd -R -P10 -dalsa -r24000 -D -Csnowball48k -i1
```

I connected the capture_1 input to the playback_1 output and heard the sound from the mic coming through my headphones loud and clear, with no xruns and no echo.  :)

For convenience, I also configured qjackctl to use the same parameters (note: the '-i1' sets the number of input channels to 1).

This is the output I get when running the above jackd command:
```
$ jackd -R -P10 -dalsa -r24000 -D -Csnowball48k -i1
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 24000
creating alsa driver ... hw:0|snowball48k|1024|2|24000|1|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 24000Hz, period = 1024 frames (42.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
playback and capture sample rates do not match (48000 vs. 24000)

```

Incidentally, the issue with the noise was happening because I had been trying the '-S' option (force 16-bit) when starting jackd and it would sometimes assume that the byte-order of my input signal was big-endian instead of little-endian, so the sound values were all out-of-whack.  Omitting the -S option cleared that up, although it irked me that there didn't seem to be any way to instruct jackd as to whether you wanted to use a big- or little-endian format...

I hope that this info is of use to others trying to use their Snowball mics with ubuntu!

Michael

---

### Post by Lee_Stricklin on 2009-06-05
Bump

I'm a bit lost on how to set this up which kind of funny because been using Ubuntu as my primary OS for a year now. The current version of Ubuntu that I have running is 64 bit 9.04. Any help would be appreciated.

---

