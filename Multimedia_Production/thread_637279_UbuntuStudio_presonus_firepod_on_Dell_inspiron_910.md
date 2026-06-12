---
title: "UbuntuStudio presonus firepod on Dell inspiron 9100 laptop"
date: 2007-12-10
forum: Multimedia Production
---

### Post by hardinkm on 2007-12-10
I am new to UbuntuStudio. I have done lots of recording on Windows with proTools. I just purchased a Presonus Firepod.

I have the firepod plugged into the laptop through a mini-firewire input. The firepod is powered up and the top right LED is lit up red.

 I open up the QT Jack Control Interface and go into setup and used the following settings based on several forums:

Driver: freebob
Realtime (checked)
priority 70
Frames/period 32
sa. rate 44100
periods.buffer 3
port max 256
timeout 500
interface default (my options are default, hw0, hw1)
audio duplex
input latency 0
output latency 0

I am not certain what I need to have the server path set as (my options are Jackstart, jackd-realtime, /usr/bin/jackd, jackd)

I have read many posts on here and still cannot figure out how to get this device working.

Is there a good step by step routine someone can provide me to get the firepod working in ardour?

Also, how do I view if the Firepod is recognized?

Any information would be great.

Thanks a ton.

---

### Post by Stochastic on 2007-12-10
Hi hardinkm and welcome to ubuntu.  
To get the presonus setup, you'll need to do the following (you may also need to install some firewire sound drivers [freebob or ffado] and some libraries if you don't have them installed - see [http://ubuntuforums.org/showthread.php?t=522738](http://ubuntuforums.org/showthread.php?t=522738)):
-open terminal
-type: cd /etc/udev/rules.d/
-type: sudo nano 40-permissions.rules
-find the line that has KERNEL=="raw1394",          GROUP="disk", MODE="0666"
-edit that to say GROUP="audio"
-save exit.
This will give any user that has audio permissions the ability to access the firewire raw devices (something that's needed for the audio card to work).  From there it's just a matter of starting it with the right settings.
I've got a firepod myself and everytime I start it I do the following: 
-boot up the computer with the firepod plugged in and turned on (red light on) this step could possibly be avoided with a hardware refresh (or hot pluggable setting) somehow but I'm not sure how to do that
-open a terminal and type: jackd -R -d freebob (optional other arguments include '-r 96000' or '-P 70' or --help for more)
You should see the red light turn blue (this is a sign that the soundcard is now synced with the computer) and get an output on the command line of: ```
jackd -R -d freebob
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
Freebob using Firewire port 0, node -1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.

```

I then open either qjackctl or patchage and connect to whatever software I'm running.

I have found that if jack shuts down on you or if you need to restart jack for any reason, you may also need to power down and back up your firepod (no reboot of the comp necessary).

I'd recommend Ardour, Rezound, Jokosher, Hydrogen, PD, and many more.  check out  a nice big list of software at [http://apps.linuxaudio.org/](http://apps.linuxaudio.org/)

---

### Post by hardinkm on 2007-12-10
Thanks a million. That did the trick. the LED on the firepod turned blue. I opened up jack control and connected into ardour and recorded my acoustic and saw the waveform record on the track.

I have one last problem. I am trying to play back the audio and am not sure how people typically listen back to their recording.  Should I plug my headphones into the headphone out of the firepod? If so, how do I map when ardour is playing back the recording to that headphone output?

---

### Post by Stochastic on 2007-12-11
Well I monitor my recordings two ways: through an amp and studio monitors out of the 1&2 outputs on the back of the presonus, or through headphones from the front of the card.  Either way I hook the master output of ardour to the 1&2 outputs of the firepod.  If you're listening through headphones you will want to watch the Mixer nob just beside the headphone jack (if it's turned all the way to the left you'll only hear the incoming channels, if it's all the way to the right you'll only hear the left/right playback).

---

