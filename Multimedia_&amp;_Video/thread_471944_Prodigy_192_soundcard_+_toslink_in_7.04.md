---
title: "Prodigy 192 soundcard + toslink in 7.04"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by pedee on 2007-06-12
I am new to linux, but installed Ubuntu on my computer, I use it primerly for playing music.

My problem is that i cannot get my AudioTrak Prodigy 192 soundcard to function. I would like to use the optical output. I've trawled google for an answer, and found that my alsa driver should be up for the task. Never the less, I do not understand just how... I also found a digital out wiki for alsa ( [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) ), but it when I tried to play some music in XMMS, I got an error message. When I use the default setting, the analog out on the card works, but the sound is pitched a bit high (playback is too fast).

Now, you experts, does anybody have any idea as how to solve this? If so, please remember that I'm new at linux :)

Pedee

---

### Post by pedee on 2007-06-16
I tried using *aplay -l* to identify my soundcards, and i got the following:

> **** List of PLAYBACK Hardware Devices ****
card 0: A192 [Audiotrak Prodigy 192], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: A192 [Audiotrak Prodigy 192], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: A192 [Audiotrak Prodigy 192], device 2: ICE1724 Surrounds [ICE1724 Surround PCM]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: V8233A [VIA 8233A], device 0: VIA 8233A [VIA 8233A]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Now, using *aplay -D hw:0,0 /home/esben/SURROUNDTEST_DD_640.wav* i get an error:

> Playing WAVE '/home/esben/SURROUNDTEST_DD_640.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:904: Sample format non available

After searching a bit i found that using the 'plug' option could help. 
*aplay -D plughw:0,0 /home/esben/SURROUNDTEST_DD_640.wav*

I got the wav playing in my earphones, and the console output looks great:

> Playing WAVE '/home/esben/SURROUNDTEST_DD_640.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

Okay, this is the analog output, but at least the soundcard works. 

I now want to use the digital output, so i tried *aplay -D plughw:**0,1** /home/esben/SURROUNDTEST_DD_640.wav*, and get the same result as before:

> Playing WAVE '/home/esben/SURROUNDTEST_DD_640.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

So apparently the sound is playing. Only problem is that it's not. No sound is comming out of the speakers, and i'm using the same setup that worked under WinXP.

Any ideas?

---

### Post by BradwJensen on 2008-03-20
I wish my Toslink output would work better..

Luckly, I can at least get mine to work in Hardy Heron..  I just can't use my Audio up/down on my apple keyboard to control the volume..

The sound also doesn't sound so lossless on linux with this. :(

Did you ever get yours working?

---

