---
title: "Sync Problem when recording audio to midi playback"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by Firefox79 on 2006-09-14
Hi all!

I'd like to record my song ideas (played on a guitar) and complete the song with MIDI instruments. So, when I record I'd like to play along with the MIDI playback (Just simple Drum, Bass and Keyboard loops).

So, I set up my "studio" according to the ubuntu studio preparation page (Yes, I compiled a realtime-patched kernel). I gave Rosegarden a try, and it works flawlesssly for the MIDI Part, audio recording itself works also fine. BUT when I record audio with MIDI Playback, the audio is recorded with a noticable delay/latency to the MIDI. Jackd has a latency below 3ms.
Can someone help me to record in sync?
Is my soundcard (see below) the problem? I also have a delay in my monitoring when having capture enabled for playback in the alsamixer.

My harware setup is as follows:
Soundcard: built-in Intel ICH5
CPU: Intel Pentium4 3GHz
RAM: 2GB

Thanx for your help!

---

### Post by zettberlin on 2006-09-15
> **Firefox79 said:**
> 
Is my soundcard (see below) the problem? I also have a delay in my monitoring when having capture enabled for playback in the alsamixer.


This points indeed to the soundchip. Maybe another test: What about connecting alsa_pcm_in directly to alsa_pcm_out in qjackctl?

---

### Post by Firefox79 on 2006-09-19
> **zettberlin said:**
> This points indeed to the soundchip. Maybe another test: What about connecting alsa_pcm_in directly to alsa_pcm_out in qjackctl?

I will try that! Thanks.

In case I have to buy a new audio interface: Since my Shuttle XPC Barebone (SS30G2) does not offer a lot of space, I think of trying an USB audio interface, like the M-Audio FastTrack USB. But an M-Audio Delta 44 might also fit.
Does anyone have experience with usb interfaces in ubuntu & jack? Ist the performace of the usb interface equivalent to a pci interface?

Greetings

Firefox

---

### Post by Firefox79 on 2006-09-30
Hi again.

I tried, tweaked a lot, until I bought the Edirol UA-25 USB Audio Interface to come by my Problem (pretty good device). To my surprise, it didn't solve the problem :mad: Curiously I still had the Latency, even with HW-Monitoring from the UA-25, which simply is impossible :confused: So I plugged in my headphones and then the Latency was completely gone :D 
Who would have guessed, that my HiFi device, where I route the Output to, has a Latency of around 200msec for the Line input ](*,) 
But now I can start being productive with my simple Ubuntu Studio, finally :mrgreen: 

Thanks for your help and Greetings

---

### Post by paul cooke on 2006-10-03
> **Firefox79 said:**
> Hi again.

[...]

Who would have guessed, that my HiFi device, where I route the Output to, has a Latency of around 200msec for the Line input ](*,)

doesn't surprise me... makes things far simpler to simply have an a to d converter on the analogue input(s) and do software mixing and equalisation before doing final amplification on the d to a output... especially if the "HI-FI" has digital inputs for handling the digital sound outputs from things like home theater systems.

Most people don't notice a very slight delay between the character's lips moving and the actual sound... and if everything in the chain is digital, then there's going to be a very small delay.

---

