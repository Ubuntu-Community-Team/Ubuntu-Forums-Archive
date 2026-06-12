---
title: "96 kHz SPDIF out on  HDA audio from realtek"
date: 2009-12-17
forum: Multimedia Software
---

### Post by Ubuntaqua on 2009-12-17
Hello all,

I am working on my HTPC / hi-fi server on a fresh Karmic using a zotac ION board (atom, nvidia 9400 for HD video through vdpau...). It has a smallish ALC662 from realtek sound card, HDA intel spec.

This card (described [here]("http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=37&Level=5&Conn=4&ProdID=144") ) is capable of 96kHz output on 24 bit samples for all digital/analog output. 

Currently, everything works fine at 48 kHz.
This is "wrong" in the sense that most audio I hear is FLAC, encoded from CDs, wich mean 44.1kHz. I also have a smaller collection of FLAC encoded in 24 bits/96 or 192 kHz (yes, there are legal downloads sellers for that sort of high quality material). 

So having a 96kHz would be a great bump in sound quality (the hi-fi setup deserves it).

So how do I get to output at 96 ?

First, there's no "advanded" config tab anywhere in the GUIs that I could find to set the sample rate / size in an Ubuntu way. Instead I dug into /etc/pulse/daemon.conf

This conf file is straightforward enough that setting the sample size to 24 bits was very easy and is ok.
However setting the sample rate to 96000 makes the output sound like a VHF radio in a storm : almost only noise, a little signal in the background.

I looked everyhere for days without finding an answer, applying all relevent howtos and advice i could find. I even tinkered (a lot) with the config files in /usr/share/alsa ... which earned me a complete reinstall.
I also played with other conf files in /etc/pulse/, to no avail.

My questions:
- What remaing parts of Alsa (which I don't know well) could mess up the whole stream ? For exemple, is it possible that alsa's dmix is still at play and performs a resampling either before or after Pulseaudio's ?
- Is there a simple realtime way of checking the sample rate of a sound being played in the system ?
- Am I missing something terribly simple and obvious ?

Thank for your help.

More information:
- kernel is stock Karmic i386
- system is correctly updated
- media framework used is gstreamer for music and mplayer for movies

EDIT : more informations and precisions

---

### Post by Ubuntaqua on 2009-12-17
bump, first post edited with details...

---

### Post by myth88 on 2009-12-18
I searched for the same, but couldn't find anything :(

...think I must go back to Windows :(

I love my Linux Box, but without some things I can't survive :D

---

### Post by VertexPusher on 2009-12-18
> **Ubuntaqua said:**
> However setting the sample rate to 96000 makes the output sound like a VHF radio in a storm : almost only noise, a little signal in the background.
To find out whether this is a PulseAudio or ALSA issue, run this command:
```
speaker-test -t wav -c 6 -f S32_LE -r 96000 -D hw:0
```
If this command fails with an error message, it means that the card does not support either 96kHz or the 32bit sample format. In that case, retry with S24_LE, S16_LE or 48000, 44100 until you find a combination that works.

> My questions:
- What remaing parts of Alsa (which I don't know well) could mess up the whole stream ? For exemple, is it possible that alsa's dmix is still at play and performs a resampling either before or after Pulseaudio's ?
PulseAudio connects to hw PCMs by default, i.e. dmix is not used. hw PCMs are the shortest possible way to the sound card. They accept only formats and frequencies natively supported by the card.

> - Is there a simple realtime way of checking the sample rate of a sound being played in the system ?
No, but you should be able to tell the sample rate by listening. If you can't do that, there's no point in running the sound card at 96kHz.

---

### Post by Ubuntaqua on 2009-12-18
Thank you for your answers,

> **VertexPusher said:**
> To find out whether this is a PulseAudio or ALSA issue, run this command:
```
speaker-test -t wav -c 6 -f S32_LE -r 96000 -D hw:0
```
If this command fails with an error message, it means that the card does not support either 96kHz or the 32bit sample format. In that case, retry with S24_LE, S16_LE or 48000, 44100 until you find a combination that works.actually, no. The wav test files themselves are recorded in 48 kHz, so your test at 96kHz very naturally fails with this error:
```
Taux d'Ã©chantillonnage incorrect (48000) pour /usr/share/sounds/alsa/Front_Left.wav  
```Which basically means "incorrect sample rate (48000) for /usr/share/sounds/alsa/Front_Left.wav. However, I will try it with a specially crafted sound file encoded at the proper rate, and get back to you. By the way, I believe spdif digital out cannot output on 6 channels at that rate, I only want stero. so I set "-c 2" as channel number parameters.
If I try a different sample rate unsupported by the card( I tried 8kHz and 38kHz), it indeed fails, like this:
```
Le taux 38000Hz n'est pas disponible pour la lecture : Argument invalide        
Le rÃ©glage des paramÃ¨tres matÃ©riels a Ã©chouÃ© : Argument invalide
```Which I would translate "The 38000hz rate is not available for playing : invalid argument. The hardware parameters setup has failed: Invalid Argument". This is the error I would expect if 96kHz was not accepted by the card. It is inconclusive however as the WAV file check is done later:
```
14:30 drake@falken ~% speaker-test -t wav -c 2 -f S24_LE -r 96000 -D hw:0       

speaker-test 1.0.20                                                             

Le pÃ©riphÃ©rique de lecture est hw:0
Les paramÃ¨tres du flux sont 96000Hz, S16_LE, 2 canaux 
Fichier(s) WAV 
Taux fixÃ© Ã? 96000Hz (demandÃ© 96000Hz) 
Taille du tampon entre 64 et 16384 
Taille de la periode entre 32 et 8192 
Utilisation du tampon maximal 16384
PÃ©riodes = 4 
La durÃ©e de la pÃ©riode Ã? Ã©tÃ© dÃ©finie= 4096
La taille du tampon Ã? Ã©tÃ© dÃ©finie = 16384
Taux d'Ã©chantillonnage incorrect (48000) pour /usr/share/sounds/alsa/Front_Left.wav 
zsh: exit 1     speaker-test -t wav -c 2 -f S24_LE -r 96000 -D hw:0
```
vs.
```
14:34 drake@falken ~% speaker-test -t wav -c 2 -f S24_LE -r 38000 -D hw:0

speaker-test 1.0.20

Le pÃ©riphÃ©rique de lecture est hw:0 
Les paramÃ¨tres du flux sont 38000Hz, S16_LE, 2 canaux
Fichier(s) WAV 
Le taux 38000Hz n'est pas disponible pour la lecture : Argument invalide 
Le rÃ©glage des paramÃ¨tres matÃ©riels a Ã©chouÃ© : Argument invalide 
zsh: exit 1     speaker-test -t wav -c 2 -f S24_LE -r 38000 -D hw:0   
```

This:```
Taux fixÃ© Ã? 96000Hz (demandÃ© 96000Hz) 
```makes me think that my card accepts 96kHz indeed. "Rate set at 96000Hz (asked 96000Hz)"

> **VertexPusher said:**
> PulseAudio connects to hw PCMs by default, i.e. dmix is not used. hw PCMs are the shortest possible way to the sound card. They accept only formats and frequencies natively supported by the card.That is very good to know and a really helpfull information. Thank you.


> **VertexPusher said:**
> No, but you should be able to tell the sample rate by listening. If you can't do that, there's no point in running the sound card at 96kHz.A difference can be heard on CDs ripped in their native form 44.1kHz and "badly" resampled at 48kHz. However, it is impractical to set a 44.1kHz mixer sample rate for music and then a 48kHz for movies. I don't want to have to change depending on usage. So a "good" higher level resampling (96kHz) is a good way to have all my audio a its resepctive best quality, not even considering real 96 kHz FLAC I own.

---

### Post by Ubuntaqua on 2009-12-20
A quick feedback on the tests performed :```
speaker-test -t wav -c 2 -f S32_LE -r 96000 -D hw:0
```tests the analog output and not the digital one. I have to replace hw:0 by default to get sound on the coax spdif out.

Thankfully, what I thought above is verified : by crafting fake "Front_Left/Right.wav" files with a 96kHz sample rate, the test above (analog) is successfull. However, the same test using the spdif still fails. I will try to borrow a high-end external DAC (something like [that]("//http://www.cambridgeaudio.com/set_territory.php?TID=1&Redirect=/summary.php?PID=320")) to verify that my current external DAC is not responsible for this. (unlikely since it works ok at 48kHz, but you never know for sure ...)

By the way, the rate specified in the speaker-test is rather irrelevant since the real rate sent to the sound card is the Pulseaudio mixer rate, which is specified by the default-sample-rate = in /etc/pulse/daemon.conf.

So I'm still out of luck as far as 96khz is concerned. I have no hardware to test the audio over hdmi output, so maybe this one is ok, but I doubt it.


Still looking ...

---

### Post by Ubuntaqua on 2009-12-21
I have confirmation that my external DAC handles 24/96 audio correctly.

If it is a bug / limitation in the driver (snd_hda_*), how/where can I learn/read about it?
If it is a bug in ubuntu, how/where/to whom should I report it ?

Thanks for your help

---

### Post by VertexPusher on 2009-12-21
> **Ubuntaqua said:**
> The wav test files themselves are recorded in 48 kHz, so your test at 96kHz very naturally fails with this error
Oops.

OK, just leave out the "-t wav" option then. Crafting special WAV files is overkill for a quick test like this. The default pink noise test sound works with any sample rate.

---

### Post by Ubuntaqua on 2009-12-21
> **VertexPusher said:**
> Oops.

OK, just leave out the "-t wav" option then. Crafting special WAV files is overkill for a quick test like this. The default pink noise test sound works with any sample rate.

Yes, I also did that seeing what speaker-test was supposed to do. It was ok in analog 96kHz and Ko in digital 96kHz.

---

### Post by Ubuntaqua on 2009-12-22
Allthough it pains me to admit it, I was entirely wrong the whole time. I will mark the thread as solved, since there never was an issue to begin with.

I tested my setup today with [this]("http://www.cambridgeaudio.com/set_territory.php?TID=1&Redirect=/summary.php?PID=320") DAC. It has an extremly convenient feature : LEDs indicating the frequency of the source SPDIF signal.

In /etc/pulse/daemon.conf the following settings were applied:
```
default-sample-format = float32le
default-sample-rate = 48000
```
Then changing the default-sample-rate option to 32000; 44100; 48000; 96000 and doing "pulseaudio -k" after each change to make sure Pulse would start with the correct rate.

Conclusion : this DAC accept everything I can send to it, the correct LED is lit for every sample frequency I tested. My own DAC wasn't working as expected (and wasn't working as advertised).

i'm very sorry for the trouble, and thankfull for the help I got from the community.

Regards,

---

