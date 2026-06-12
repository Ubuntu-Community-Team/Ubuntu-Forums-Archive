---
title: "Bit-perfect audio on Ubuntu, USB DAC"
date: 2012-02-07
forum: Multimedia Software
---

### Post by Walther -FI- on 2012-02-07
Hi,

I am becoming an audiophile, slowly, step by step.

I am considering buying an external digital-analog converter (DAC) to feed my studio headphones (AKG K271 mkII) with 24bit 192kHz/96kHz audio.
After reading some reviews and taking a moment to think about the portability, I think I'm going for [ _this_]("http://www.thomann.de/fi/esi_dr_dac_nano.htm").

This should improve my music listening experience, as currently I am limited to the onboard audio.
However, I have read about problems people have had setting up their USB DAC's on Ubuntu forums, e.g. [ _here_]("http://ubuntuforums.org/showthread.php?t=1628787").

My questions are:
- How well does Ubuntu support USB DAC's?
- Is Ubuntu capable of bit-perfect output? (skipping the onboard re-sampling)
- Will the performance of ALSA, JACK or OSS be comparable to ASIO or WASAPI? (the Windows driver equivalents I have heard good things of)
- Are there any other things I should consider before buying the USB DAC, as I am using Ubuntu only - no fallback possibility to Windows

---

### Post by wilbertnl on 2012-02-08
> **Walther -FI- said:**
> - How well does Ubuntu support USB DAC's?
- Is Ubuntu capable of bit-perfect output? (skipping the onboard re-sampling)
- Will the performance of ALSA, JACK or OSS be comparable to ASIO or WASAPI? (the Windows driver equivalents I have heard good things of)
- Are there any other things I should consider before buying the USB DAC, as I am using Ubuntu only - no fallback possibility to Windows
Hello Walter,
Any Linux or FreeBSD distro supports the Universal Audio Class (UAC), foolproof like plugging a monitor into a VGA port.

The problem mentioned in the post you refer to are related with the order of loading kernel modules, but you are able to specify which audio card is 0 and which is a higher number. ([http://alsa.opensrc.org/MultipleCards](http://alsa.opensrc.org/MultipleCards))

Your USB DAC will be recognized as a seperate sound card with it's own chipset. Onboard sound will be totally ignored when you select the USB-DAC as sound output, similar to how a wired ethernet card is ignored when you select wifi as your connection.

Bitperfect does depend on the software that you use, Music Player Daemon is a great example that supports feeding a DAC without resampling. The caveat is that it locks your soundcard and desktop sounds like a ding or error won't get a chance to reach the sound card. I suggest that you experiment with different configurations. I also started with the idea that 'bitperfect' was my destination, but after lots of experimenting and frustration (internet radio, for example may sound way better when properly resampled) I got less religious about bitperfection.

When I got my HRT Music Streamer II, I had an experience like cotton was removed from my ears and suddenly sound was crystal clear. I enjoy music much more, regardless of lowres internet radio or highres flac tracks.

Don't forget to enjoy the music!

---

### Post by Walther -FI- on 2012-02-10
Nice to hear it should work foolproof!

Yep, I know there is much more to it than bitperfect - however, it is a good goal (set goals high, and you'll reach at least good if not excellent).

And sure, I do hope that the USB DAC would improve the quality of other audio too, sure most of my audio is in CD quality and Spotify's 320kbps - nowhere near the gold-eared audiophile standards. But that doesn't stop me from enjoying good music and the fact it is played properly with good quality.

I'll order the DAC today and comment here about my experiences when it arrives - there isn't that much information available online about the USB DAC support on Ubuntu / Linux systems.

Thanks for the reply,
Enjoy your music,
-V

---

### Post by wilbertnl on 2012-02-11
> **Walther -FI- said:**
> there isn't that much information available online about the USB DAC support on Ubuntu / Linux systems.


Google for 'audiophile linux' and 'mpd bitperfect'

Here are some sites focused on high end audio quality with computers:
[http://www.computeraudiophile.com/](http://www.computeraudiophile.com/)
[http://opensourceaudiophile.com/](http://opensourceaudiophile.com/)
[http://www.dailyaudiophile.com/](http://www.dailyaudiophile.com/)

Here are forums for audiophile sound based on computersystems:
[http://www.audiocircle.com/](http://www.audiocircle.com/)
[http://www.head-fi.org/f/](http://www.head-fi.org/f/)

I have an Atom based tiny and cheap server connected to my stereo system in the living room and use this software:
[http://mysqueezebox.com/index/Home](http://mysqueezebox.com/index/Home)

Enjoy!

---

### Post by marin123 on 2012-02-11
I don't want to ruin your fun, but I just don't see a point in buying a piece of hardware that you don't need.
You said it yourself that you have either 16 bit wav or 320 kbps mp3. Any onboard sound card is just fine for playing that.
Unless you are a sound engineer/studio producer and you work with sounds recorded at 96 kHz and 24 bit samples, you are fine with what you have already got.
Better if you had invested in quality speakers.
Just for the record, I have Pioneer CDJ 2000 which has builtin (24 bit, 96 kHz) DAC, and I don't see much difference compared to my laptop sound card.

---

### Post by BicyclerBoy on 2012-02-11
I agree
If your source is mp3 & low bit rate then 'bit perfect' has no sensible meaning.

The onboard soundcard iec958 will output 96KHz 24bit (2ch) into an external HT Amp (or DAC) & allow you to HQ resample with pulse or alsa.
So then you could up-sample all audio to 96KHz/24bit & play 192KHz downsampled.

Better yet use HDMI audio or ethernet into HT amp/AVR & have 8 ch 192KHz/24bit & decoding for all HDA formats..

You still need a music player that preserves the data.
Clementine (>=1.0) seems to behave with 192KHz/24bit etc.

---

### Post by wilbertnl on 2012-02-12
> **BicyclerBoy said:**
> The onboard soundcard iec958 will output 96KHz 24bit (2ch) into .. (or DAC)

Sir,
No sound card outputs into any external DAC, since it utilizes its own DAC chip.

---

### Post by BicyclerBoy on 2012-02-12
There are external DACs with IEC958 inputs..
The soundcard IEC958 output is just a digital bitstream.

IEC958 (& toslink especially) are not clock jitter free so receiver reclocking is required.

Consumer IEC958 is a limited to 96KHz/24bit (32bit) 2 ch.

---

### Post by moxill on 2012-02-12
> **marin123 said:**
> 
You said it yourself that you have either 16 bit wav or 320 kbps mp3. Any onboard sound card is just fine for playing that.
Unless you are a sound engineer/studio producer and you work with sounds recorded at 96 kHz and 24 bit samples, you are fine with what you have already got.

Sorry to be blunt, but I really couldn't disagree more.  Analog direct off my built-in sound card (from a board marketed as a high quality multi-media setup) is as rough as a gravel road, the resolution and clarity quite frankly suck for music.  Through even a cheap DAC via optical S/PDIF the sound is noticeably improved, even for V0 mp3.
So, for the OP: there is a little more wind in your sails, keep going, and as the other poster said, don't forget to enjoy the music.  This is a hobby that favors OCD-type behavior, sort of like golf.  Don't get sucked in too deep.

---

### Post by wilbertnl on 2012-02-12
> **BicyclerBoy said:**
> There are external DACs with IEC958 inputs..
The soundcard IEC958 output is just a digital bitstream.

IEC958 (& toslink especially) are not clock jitter free so receiver reclocking is required.

Consumer IEC958 is a limited to 96KHz/24bit (32bit) 2 ch.

BicyclerBoy, I have no doubt that you have expertise in this area, but the OP does not mention IEC958 in the request for information, OP is focused on a USB-DAC.

I have been wondering since reading your and Marin123's replies: why are your personal opinions more important than a straightforward response to the concerns formulated in the first post?

---

### Post by moxill on 2012-02-13
As for 'bit-perfect' just remember this, perfect is an ideal.  USB audio is not an error checking protocol (nor is S/PDIF).  It's nothing to worry about either, a lost bit here and there really doesn't harm audio, just consider the sample rates we are talking about.  An Async. DAC will get you closer than anything else you can do.

Regarding drivers: No need to fear you won't get the best sound out of your Ubuntu rig, windows systems need drivers to deliver higher sample rates (that  you are unlikely to need anyhow), most any modern *NIX install does not require such help from drivers.  Set up correctly it is a simple pass-through, your Ubuntu system will not touch a single bit on its way out the port of choice.   FWIW, I read a post a while back where a guy, after extensive A/B testing various OS's, *claimed* he perceived the best sound from a FreeBSD rig using ALSA.  I haven't built a FreeBSD box in a while and straining to hear 'micro-details', 'air', 'blackness' and other audiophile hyperbole just gives me a headache...not the desired outcome.

Plug it in, tell MPD to use the external DAC sit back with your favorite beverage and enjoy.  If it sounds right, it is right.

---

### Post by eshwar_andhavarapu on 2012-02-16
I am also at the same phase as OP

So, anyone knows if the Asus Xonar U3 works?

---

### Post by wilbertnl on 2012-02-16
> **eshwar_andhavarapu said:**
> So, anyone knows if the Asus Xonar U3 works?

According to AsusTek the chipset in the U3 is _UA100_
(Read: [http://www.asus.com/Multimedia/Audio_Cards/Xonar_U3/#specifications](http://www.asus.com/Multimedia/Audio_Cards/Xonar_U3/#specifications))

According to the Alsa Hardware Matrix the chipset UA100 is supported since ALSA 1.0.21 or kernel 2.6.31
(Read: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus))

---

### Post by eshwar_andhavarapu on 2012-02-16
> **wilbertnl said:**
> According to AsusTek the chipset in the U3 is _UA100_
(Read: [http://www.asus.com/Multimedia/Audio_Cards/Xonar_U3/#specifications](http://www.asus.com/Multimedia/Audio_Cards/Xonar_U3/#specifications))

According to the Alsa Hardware Matrix the chipset UA100 is supported since ALSA 1.0.21 or kernel 2.6.31
(Read: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus))

I saw that part. It was just that even products with the same chipset were supported from different kernels onwards, hence the question!

---

### Post by wilbertnl on 2012-02-16
> **eshwar_andhavarapu said:**
> It was just that even products with the same chipset were supported from different kernels onwards, hence the question!

This list of supported hardware is the result of user input.
If your Asus Xonar U3 works fine and you feel like adding your hardware to the list, then you will likely report your current kernel and alsa release.

You won't take the time to install older kernels to test functionality.

---

