---
title: "How to verify bit-perfect audio playback?"
date: 2012-04-03
forum: Multimedia Software
---

### Post by Welly Wu on 2012-04-03
I have an ASUS N61JV-X2 notebook PC running Ubuntu 11.10 64 bit GNU/Linux with dm-crypt, LUKS, and LVM using the Serpent cipher in ESSIV:SHA256 mode of operation with 256 bit key strength and SHA-512 hash algorithm on my Intel 2nd Generation X25-M 160 GB SSD.

I installed DeaDBeef-0.52 and Clementine 1.01. I am using the default ALSA sink. I configured DeaDBeef to use the ALSA sink and my USB Audio Codec as the output device. I also configured the ALSA sink to not resample and release the device when stopped.

I have about 20 gigabytes of high resolution .FLAC and .WAV loss less audio files recorded at 24 bits or 32 bits resolution and 96, 192, and 384 kHz sampling rates.

I have a high end audio system:

Resolution Audio Opus 21 CD Player, Power Centre, Extra Sources, S30 Power Amplifier
Ray Samuels Audio Emmeline HR-2 headphone amplifier
Sennheiser HD-650 headphones
Balanced Power Technology BP.Jr II Ultra with Signature Upgrades power conditioner [2.5 amps, 120VAC common-mode rejection, 15 and 30 amp duplex outlets]
Balanced Power Technology 9 gauge Litz 2.0 meter Power cord
Cardas Golden Reference Power 1.0 meter cord
Cardas Golden Reference Interconnects 0.5 meters RCA terminations
Cardas Clear Serial Bus (USB) 1.5 meter Type A to Type B
Cardas Neutral Reference Digital S/PDIF 0.5 meter RCA terminations
DNM Reson DIN-RCA 1.0 meter for Resolution Audio Opus 21 CD Player
Volex 17964 1.0 meter Power cord

How do I check to see if my software music player is playing my .FLAC, .WAV, and .MP3 files at the correct resolution and sampling rate? In other words, how do I verify bit-perfect sound playback in Ubuntu?

On a related matter, how do I configure Ubuntu to ensure bit-perfect audio playback? I think that I have already done so by following the instructions posted on Head-Fi.Org by another member using DeaDBeef for GNU/Linux and the ALSA sink, but I am not sure if it is accurate. I need verification.

Please help if you can. Thank you.

---

### Post by Welly Wu on 2012-04-03
Do both DeaDBeef-0.52 and Clementine 1.0.1 support bit-perfect audio playback? What about if I use the ALSA sink with them?

---

