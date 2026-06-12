---
title: "Recommend a MIDI interface &amp; sound card (multitrack recording etc with Rosegarden)"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by Wormsie on 2007-01-03
Hi!

I got bored with ALSA not working in my Ubuntu and decided to get a new soundcard. Because M-Audio Delta 44 seems to be well supported I'm going to get one of those. But it doesn't have MIDI. Do the M-Audio USB midi interfaces work? My guess is "no". So what kind of a MIDI system would work with Linux? I only need one midi in and one midi out.

Thanks!

---

### Post by sgx on 2007-01-04
Hi! Get mAudio 24/96 pci card, works great across all main distros, I play vst through
Yamaha synth, has your needed midi, analog, and digital i/0 for max. $99. Also great for ogg/mp3 Dvd
and game soundtracks! No fears, mate!

---

### Post by Wormsie on 2007-01-04
Good idead - do you mean the [Delta Audiophile](http://www.m-audio.com/products/en_us/Audiophile2496-main.html)? You're right, it would suit my needs well.

---

### Post by sgx on 2007-01-04
Yes, just don't get the newer Delta 24/192 model, unless you can overwhelmingly verify it is working in alsa...it wasn't last year...or last week, or last decade...
etc...

---

### Post by Patrick K on 2007-01-05
> **sgx said:**
> Hi! Get mAudio 24/96 pci card, works great across all main distros, I play vst through
Yamaha synth, has your needed midi, analog, and digital i/0 for max. $99. Also great for ogg/mp3 Dvd
and game soundtracks! No fears, mate!I have the Audiophile 2496 card, too, but haven't been able to get it to work with Audacity (I using Edgy). Although, it seems to work fine with the Ubuntu supplied apps. Have you tried recording with it? It is a great card and works excellent in windows but like I said, I can't get playback or record in Audacity.

Any help is appreciated.

---

### Post by sgx on 2007-01-06
> **Patrick K said:**
> I have the Audiophile 2496 card, too, but haven't been able to get it to work with Audacity (I using Edgy). Although, it seems to work fine with the Ubuntu supplied apps. Have you tried recording with it? It is a great card and works excellent in windows but like I said, I can't get playback or record in Audacity.

Any help is appreciated.
Are  you using envy24control? This is  the config utility...offering near total control of all ins/outs and settings
also install and open qjackctl, and to the right of  the 'Interface' box, you see >
click on >  and it will name the two titles of your card, and info about them is in your manual: ICE 1712  Multi, and M Audio Audiophile 
24/96' Maybe the opposite one needs chosen as devdsp in some dialogue...After installing and configuring with envy24control,Try loading a song from a music cd, or a 16bit .wav file and play them back...if   that fails, try the alsamixer app, as sometimes that has more accurate read on the needed volumes...hope this helps...post more precise details of tests/error messages etc...
as needed...also, if  you have motherboard soundchip, turn it off in bios setup...then proceed with tests...also install alsaoss, in case audacity is functioning under oss instead of alsa ( plus it helps all apps using oss to get absorbed by alsa
Hope this helps!

---

### Post by SuperDindon on 2007-01-06
> **sgx said:**
> Yes, just don't get the newer Delta 24/192 model, unless you can overwhelmingly verify it is working in alsa...it wasn't last year...or last week, or last decade...
etc...
..but it is already supported by ALSA 1.0.14rc1 and will be supported by Ubuntu (Feisty?) soon :-$

---

### Post by cylon359 on 2007-01-07
I have one of the M-Audio USB MidiSPORT 2x2 devices, and it works well (although I'm having an issue with udev).  You need to get the firmware from usb-midi-fw.sourceforge.net

---

### Post by Patrick K on 2007-01-07
> **sgx said:**
> Are  you using envy24control? This is  the config utility...offering near total control of all ins/outs and settings
also install and open qjackctl, and to the right of  the 'Interface' box, you see >
click on >  and it will name the two titles of your card, and info about them is in your manual: ICE 1712  Multi, and M Audio Audiophile 
24/96' Maybe the opposite one needs chosen as devdsp in some dialogue...After installing and configuring with envy24control,Try loading a song from a music cd, or a 16bit .wav file and play them back...if   that fails, try the alsamixer app, as sometimes that has more accurate read on the needed volumes...hope this helps...post more precise details of tests/error messages etc...
as needed...also, if  you have motherboard soundchip, turn it off in bios setup...then proceed with tests...also install alsaoss, in case audacity is functioning under oss instead of alsa ( plus it helps all apps using oss to get absorbed by alsa
Hope this helps!

I don't know that envy24control is on my system but I did get the Delta 2496 card working with Audacity. I had to disable the AC97 onboard device in the BIOS. Which is a bit of a problem since I use the MIDI part of it. With windows they coexisted fine. I'm thinking that maybe editing the sound conf file (I don't know the name of it, maybe it's the envy24control) and pointing the ALSA drivers to the MAudio card might work. Currently, I think it points to the first device found, which probably is the onboard device. 

Also, the volume control in Audacity doesn't work. I have to us the DAC sliders (which are not linked) in the alsamixer, which is a bit of a problem. The card's output goes to a high power stereo amp that has blownout (at 112db) some very expensive speakers in the past. I'd like to avoid that in the future.

---

### Post by markedman on 2007-01-09
Another vote for Maudio Audiophile 2496... I use it for multitrack recording with Ardour and it works incredibly.

---

### Post by sgx on 2007-01-09
...you might as well use the midi i/o on your Delta card, and then set up a row of multiple desktops for mixer, audacity, jackd, qjackctl, and fx setups
like creox and ecamegapedal...glad you got it working!

---

### Post by jondecker76 on 2007-03-02
I too am looking for the best sound card I can afford. Right now I'd like to stay in the $300-$600 range..

Currently, i still use windows, FL Studio and Cubase with an Emu 1820m, and it kills me that the 1820m dock is not supported under linux. The sound card is amazing with brilliant sound. It really is a shame that the 1820m isn't supported!

What could I replace this with to work well with linux?

I would like a card with midi in/out, at least 1 XLR (hopefully 2) and at least 4 in 4 out... Seems to be a tough order to fill, does anyone have any suggestions???

---

