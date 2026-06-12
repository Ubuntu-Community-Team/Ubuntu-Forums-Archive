---
title: "flac, external dac"
date: 2009-05-31
forum: Multimedia Software
---

### Post by vmsda on 2009-05-31
I need to do three things to have hifi quality sound from my Linux pc:

1. Convert a CD to flac format: ok with Audio Extractor.
2. Play the converted .flac file, ie. decode it: ok with RhythmBox and Mplayer, sound coming through the pc speakers.
3. Send the decoded output to an external, usb-connected DAC.

Anybody know how to get step 3 done?

---

### Post by Man_Beach on 2011-07-03
Anyone got a solution to this yet? I want to do the same thing.

---

### Post by tsh on 2011-07-05
Well, I have an arcam rDAC which worked when I plugged it in, but I have no idea how to check if it is seeing the correct bit rate. (I cheated, I downloaded some test flac encoded files rather than ripping from CD)

---

### Post by timvanderwart on 2011-10-30
> **tsh said:**
> Well, I have an arcam rDAC which worked when I plugged it in, but I have no idea how to check if it is seeing the correct bit rate. (I cheated, I downloaded some test flac encoded files rather than ripping from CD)

Old thread but here goes nothing...

I'm thinking about purchasing an Arcam rDac and connecting it wirelessly via Arcam asynchrone USB input using KLEER Wireless to my laptop running on 11.10.

I'm just not sure if Ubuntu will recognize the Arcam usb wireless stick. Does anybody have experience with this or knows something about this?

---

### Post by timvanderwart on 2011-10-30
> **timvanderwart said:**
> Old thread but here goes nothing...

I'm thinking about purchasing an Arcam rDac and connecting it wirelessly via Arcam asynchrone USB input using KLEER Wireless to my laptop running on 11.10.

I'm just not sure if Ubuntu will recognize the Arcam usb wireless stick. Does anybody have experience with this or knows something about this?

Found it: [http://www.arcam.co.uk/products,Devices,Accessories,rWave.htm#](http://www.arcam.co.uk/products,Devices,Accessories,rWave.htm#)

I guess that in Sound settings it will probably be possible to select the 'arcam wireless' device as appointed hardware. :D

---

### Post by BicyclerBoy on 2011-10-30
Putting aside clock jitter..(reclocking digital inputs solves this).

HDMI audio makes all external DACs look increasing pointless unless you are after an audiophile solution (>$10K).

Have you looked at an A/V receiver with DLNA. May have to plug a wifi dongle into AVR.

This soln could let you stream 8 ch 192KHz/24 bit LPCM & video..

You resample with pulse or alsa libsample (very CPU intensive) to the max rate supported by external device).'

The current video streaming in HT amps/ AVRs seems poor..

---

