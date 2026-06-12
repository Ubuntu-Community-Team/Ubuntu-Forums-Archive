---
title: "Just Playing guitar"
date: 2008-01-05
forum: Multimedia Production
---

### Post by Geronimo on 2008-01-05
I just want to play my electric guitar with Ubuntu and maybe trying different amp like "Guitar Rig on Windows". Is possible? I tryed different program like Ardour, Rosegarden (but tell me that the timing is too low), and Muse but they are too difficult for me.
Can anyone help me?
Thanks

---

### Post by theacoustician on 2008-01-05
> **Geronimo said:**
> I just want to play my electric guitar with Ubuntu and maybe trying different amp like "Guitar Rig on Windows". Is possible? I tryed different program like Ardour, Rosegarden (but tell me that the timing is too low), and Muse but they are too difficult for me.
Can anyone help me?
Thanks
If you're getting timing errors, that might be a signal to move to the real time kernel.  You should get Ubuntu Studio a go.  IT'll set that up for you and preinstall just about every music program you would want.

---

### Post by haksas on 2008-01-05
Hi,
If you are looking for a realtime guitar FX then "creox" is just fine and you don't need a realtime kernel for that,
If this could help U

---

### Post by Geronimo on 2008-01-05
I tryed creox but it give me an error, if I launch it by command line when I do Play it give me error and on the terminal "JACK tmpdir identified as [/dev/shm]". I tryed to launch Ardour (because of I seems to launch Jack correctly) then creox, now It don't give me any error (on the terminal SSE2 detected) but I can't ear sound. 
Where I have to attach the guitar? On the Line imput or in the Microphone imput? Where can I select the input port (line in or back microphone or front microphone) and the output port?
I use the optical out on the soundcard. Maybe this is the problem?

---

### Post by Zimmer on 2008-01-05
Signal level is more likely to be a problem..
Usually one needs an interface preamp unit of some description to get a strong enough signal to the sound card.
For example: Line 6 PodXt and the Pod family, or maybe even a simple DI (Direct Injection)box  (we use one at church to lift the guitar signal to mic level and send to a PA system.)

Personally, I have only ever connected my guitar to Ubuntu using the Line6 PodXT live and recorded it with Audacity. I have never tried to plug it directly into the soundcard..

---

### Post by Geronimo on 2008-01-05
I bought (I hope arrive tomorrow) an M-Audio Jamlab, you think that is compatible with Ubuntu.
So without a preamp I can ear nothing?

---

### Post by haksas on 2008-01-05
Hi again,
The creox error is familiar,
all you have to do is to run jack server (or deamon) by doing this :
Presse alt+F2 then type :
jackd -d alsa -d hw:0 & creox,
this should run creox as well,
that's it, no need to run ardour unless U work with.

On the other hand : Better to use the rear inputs of your sound card because thy are selected by default : usually mic 1 is rear and mic 2 is on the front, so use the alsa mixer to swith between them or stay on mic1. line input also should work.
for the output : it depends on your system amplifier, if you use a digital home cinema (e.g) then the SPDIF or coaxial output is fine, otherwise use the line output to connect to your amp or the amplified speakers.
Enjoy!.

---

### Post by haksas on 2008-01-05
I agree with Zimmer, a signal boosting or a preamp is always solicited for a good sound quality, that why I recommend you to use mic input rather than the line input because the mic one has a boot signal option in the alsa mixer that could be very useful, of course a preamp box is much better and provide a real sound, but just in case you don't own one.
Yours!

---

### Post by Geronimo on 2008-01-06
Many thanks, now the I can ear the guitar, connected to the rear mic, using Mic Boost and the volume of the guitar at max. But creox do nothing, I tryed to modify something in the setting but nothing happen.
When I launch Jack this is the output:

ivan@ivan-ubu64:~$ jackd -d alsa -d hw:0 & creox
[1] 22284
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
kbuildsycoca running...
DCOP Cleaning up dead connections.


**** alsa_pcm: xrun of at least 0.037 msecs

JACK tmpdir identified as [/dev/shm]
SSE2 detected


**** alsa_pcm: xrun of at least 0.017 msecs

JACK tmpdir identified as [/dev/shm]
SSE2 detected


**** alsa_pcm: xrun of at least 0.016 msecs

JACK tmpdir identified as [/dev/shm]
SSE2 detected


**** alsa_pcm: xrun of at least 0.017 msecs



**** alsa_pcm: xrun of at least 0.013 msecs

........

Why creox don't do anything?
Thanks

---

### Post by haksas on 2008-01-06
Dear fellow,
I don't think you did press the play icon,
In creox just press the space bar on the keyboard, or the icon next to the floppy one.
If ti still doesn't give nothing, check in the menu -effector-options, then make sure you got the right inputs and outputs for alsa.
Enjoy!

---

### Post by Geronimo on 2008-01-06
I pressed the play icon. No sound. I tryed different setup on the effector option (I have alsa_pcm:capture_1 and alsa_pcm:capture_2 on Imput Channel Connection and alsa_pcm:playback_1 to _8 on the Output) but no sound.
I tryed also different setting on the Volume control of Ubuntu, but no sound.
I also installed Ubuntu Studio and tryed to run creox (after Jack) and still no sound.
Maybe something stupid stuff.
Any help from the biginning. I use the guitar connected in the microphone in on the rear of the computer on the audio device, and an optical out from the sound card to an external amplifer.
Thanks

---

### Post by Zimmer on 2008-01-06
> **haksas said:**
> I agree with Zimmer, a signal boosting or a preamp is always solicited for a good sound quality, that why I recommend you to use mic input rather than the line input because the mic one has a boot signal option in the alsa mixer that could be very useful, of course a preamp box is much better and provide a real sound, but just in case you don't own one.
Yours!

Well, I tried out the direct method of guitar to Line In (adapter plug req'd) and recorded using Audacity.
Result  OK

Tried the DI box via the mic input and although I got a 'fatter' input signal I also got a background interference . 
So it could be a case of trial and error depending on the Soundcard and setup.

I must also say that when  the Line6 XT live was plugged into the Line input, there was no interference there...

---

### Post by Geronimo on 2008-01-07
Ok I tryed to connect my guitar in the line in in the back. I regulate the volume control until I eared sound. I can ear the guitar sound but creox doesen't do any effect, don't do anything.
Another problem, every some second I ear a tap (strange sound from the computer), the Jack Messages tell:

*** alsa_pcm: xrun of at least 0.015 msecs
20:16:15.824 XRUN callback (155).
load = 0.1680 max usecs: 37.000, spare = 23182.000
load = 0.1701 max usecs: 40.000, spare = 23179.000
load = 0.1970 max usecs: 52.000, spare = 23167.000

Is normal. Using the line in the sound is more clean than the mic in, no rumor in background. But that annoying sound...

Please how to use a sound processor to modify the sound of my guitar in real time.
Thanks

---

### Post by eric71 on 2008-01-08
I've had better luck with Jack Rack than Creox. You can use it to load LADSPA effects and play live.  The CAPS LADSPA effects package has some very good amp and cabinet simulations. Should all be available through synaptic. After installing, just use QjackCtl to start Jack, run Jack Rack and add the effects you want. You'll have to make sure through the "connections" dialog in QJackCtl that everything is connected, i.e. soundcar in to Jack Rack to soundcard out.

---

### Post by MaxVK on 2008-01-11
Hi eric71, I wonder if you could be kind enough to explain the setup of QJackCtl in a little more detail. I have everything installed but I cant seem to get the connections to work out. There an awful lot of controls and settings, and Im just not sure whats supposed to be connected or where!

Cheers

Max

---

### Post by MaxVK on 2008-01-11
Uh, scratch that thanks - I worked it out, but I don't think Jack Rack is going to work out for me.

---

### Post by pkslot on 2008-01-12
Maybe you should try installing patchage. Its a visual tool for connecting audiosoftware.

just run

```
sudo apt-get install patchage
```

and you should be able to connect what ever audiotools you like.

---

### Post by alx010 on 2008-01-13
Hmm,,,,just noticed that there's a Linux version of the  Jesusonic guitar processor.

[http://www.jesusonic.com/soft.php](http://www.jesusonic.com/soft.php)

---

### Post by MaxVK on 2008-01-13
It looks good, but its a preview release. I'm not sure Id trust it.

> **alx010 said:**
> Hmm,,,,just noticed that there's a Linux version of the  Jesusonic guitar processor.

[http://www.jesusonic.com/soft.php](http://www.jesusonic.com/soft.php)

---

### Post by eric71 on 2008-01-14
> **MaxVK said:**
> Hi eric71, I wonder if you could be kind enough to explain the setup of QJackCtl in a little more detail. I have everything installed but I cant seem to get the connections to work out. There an awful lot of controls and settings, and Im just not sure whats supposed to be connected or where!

Cheers

Max

Sorry I was so slow in replying. This is a pretty good place to start for the settings:

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

There's some good screenshots at QJackCtl's website that might help with the "connections" dialog:

[http://qjackctl.sourceforge.net/image/qjackctlConnectionsForm1.png](http://qjackctl.sourceforge.net/image/qjackctlConnectionsForm1.png)

I think Jack Rack should appear somewhat like Qsynth in this picture. You'll want the alsa_pcm input ports connected to Jack Rack and Jack Rack connected to the alsa_pcm output ports.

---

### Post by MaxVK on 2008-01-14
Holy Heck! It looks like the back of my PC desk! ;)

Thanks - Ill give it a go!

---

