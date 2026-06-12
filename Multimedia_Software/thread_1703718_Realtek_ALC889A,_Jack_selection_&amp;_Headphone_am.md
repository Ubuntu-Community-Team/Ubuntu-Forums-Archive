---
title: "Realtek ALC889A, Jack selection &amp; Headphone amp"
date: 2011-03-09
forum: Multimedia Software
---

### Post by WrxSTI on 2011-03-09
Hello everyone, I'm a new user of Ubuntu and after using Windows for about 11 years am finding myself having to relearn everything, which may not be such a bad thing. I've managed to set up a fairly usable environment, however, I am having some issues with the sound department.

I have a Gigabyte GA-X48-DQ6 with an integrated Realtek ALC889A chip. The thing about this chip is that it has 6 jacks in the back which can be reassigned in the Realtek Windows software to whichever purpose. Setting any of these jacks to the "Headphone" setting activates the in-built headphone amplifier circuit, which is neccessary for my headphones as they have about 56 Ohm resistance. Right now, in Linux I can tell this circuit is not active because the headphones are way too quiet with muffled bass.

I've tried messing around with the sound options in control panel but no matter what I set there nothing really changes (setting to Analog Headphones mutes the "Front" channel and then I get no audio whatsoever), I've also tried messing around with Alsamixer (I set the model to "model=intel-alc889a" as per_ [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto")_ guide) but there are no options for jack remapping or enabling the in-built amp, the only thing I can really do in there is change the volume and mute certain things.

Another thing, under Windows the better players (such as Foobar) had the option of setting output sample rate (44.1 khz, 48 khz) and bit depth, etc. as well as WASAPI mode to block any other sound and give the program control of the sound card (to avoid resampling etc.). In Linux I haven't found any program that has any such options so I am going to -assume- that this is handled by whatever audio engine the program is sending to ( I guess this is ALSA by default?) Must it then be set somewhere in the settings of this audio engine? How can I change which one is used by default and which one is the best and offers some features/settings like the WASAPI mode?

Anyway, I am sorry if this post is somewhat ignorant as I am really, really new to Linux (been using it only 1 day) and am trying to wrap my head around everything. Thanks.

---

### Post by Yellow Pasque on 2011-03-09
Unless you were using something like ASIO or kernel streaming, Windows DirectSound was probably resampling your sound anyway. HD codecs don't have hardware mixers. Anyway, Linux uses Pulseaudio for mixing. You can set the highest quality remixing in /etc/pulse/daemon.conf by editing the resample-method line to look like this
```
resample-method = src-sinc-best-quality
```

> Right now, in Linux I can tell this circuit is not active because the headphones are way too quiet with muffled bass.
Perhaps upgrading ALSA would help. You can install  the linux-alsa-backports package or use the source build script: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

> I set the model to "model=intel-alc889a"
Here's the latest list (I would try 6stack-dig):
```
ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  macmini3	Macmini 3,1
  mba21		Macbook Air 2,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m540r	Clevo M540R (6ch + digital)
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)
```

---

### Post by WrxSTI on 2011-03-10
Well, I've successfully updated ALSA to 1.0.24 but even after trying several of the models on that list, nothing really changes, just a couple of options more or less in Alsamixer. Basically, what I'd like to do is have one of the jacks act as a normal speaker-out (non-amplified) for my speakers and another one where the headphones would be connected and for them the headphone amp would be active. I was able to do this in Windows by setting the green one to "Front speaker" and the black one to "Headphones" for example. I haven't found a way to do this so far :(

BTW, I've noticed Realtek has some Linux drivers on their own website. I tried those, but after installing and restarting all my sound was gone and the only output was "Dummy output". Couldn't fix this without reinstalling Ubuntu.

---

### Post by WrxSTI on 2011-03-10
Anyone have a possible idea on what I could try next? Thanks.

---

### Post by WrxSTI on 2011-03-11
Hmm, anyone? There has got to be a way to access this feature :/

---

### Post by WrxSTI on 2011-03-12
Anyway, I managed to solve my problem by using HDA Analyzer, so for future reference.

[[IMG]http://img860.imageshack.us/img860/3131/screenshotava.th.png[/IMG]]("http://img860.imageshack.us/i/screenshotava.png/")

Found the 0x14 node (Green out) and activated the "HP" option. Great program. I believe it can also be used to control jack sensing and other things for various inputs.

[U][Link]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")
[/U][]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")

---

