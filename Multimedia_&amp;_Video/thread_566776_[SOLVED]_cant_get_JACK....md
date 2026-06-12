---
title: "[SOLVED] cant get JACK..."
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by kornation on 2007-10-03
Gday!

I downloaded a few programs from the add/remove for music creation and dj use, one of them im really intrested in is the internet dj console, but i cant get it to work..

The error that comes up each time is ...
> 
The JACK sound server needs to be running in order to run IDJC.
In order to manually start it try something like:

		$ jackd -d alsa -r 44100 -p 2048

If you would like JACK to start automatically when you start IDJC try this:

	echo "/usr/bin/jackd -d alsa -r 44100" >~/.jackdrc

If you have already done this it is possible another application or non-JACK sound server is using the sound card.

Possible remedies would be to close the other audio app or configure the sound server to go into suspend mode after a brief amount of idle time.

I have been to [http://jackaudio.org](http://jackaudio.org) and it says...

> Binaries: please use your distribution's package manager (apt-get, yum, synaptic etc.)

i am a ubuntu/linux newbie - i have used the command line before to download and install grafics drivers but how do i install jack this way?

---

### Post by peabody on 2007-10-03
I believe the package you want to install is jackd.

I think you may have to disable esd under the sound preferences to launch jack.  I'm no jack expert, you'll probably have to google for command line invocations.

---

### Post by kornation on 2007-10-03
i searched google again - and found this....

> sudo apt-get install jackd qjackctl libqt3-headers libqt3-mt-dev libsamplerate0-dev libmad0-dev libaudiofile-dev libmpeg3-dev libid3-3.8.3-dev ladspa-sdk swh-plugins tap-plugins libxml2-dev lame libjack-dev libogg-dev libvorbis-dev

which fixed my problem!

while not directly fixing my problem you did show the way to finding the answer (google 'jackd command line install') - thank you

---

