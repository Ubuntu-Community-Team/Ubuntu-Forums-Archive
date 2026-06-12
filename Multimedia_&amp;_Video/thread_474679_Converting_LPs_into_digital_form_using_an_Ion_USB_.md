---
title: "Converting LPs into digital form using an Ion USB Turntable"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by MLX on 2007-06-15
I am thinking of buying a Ion USB turntable which can be seen here
[http://www.ion-audio.com/ittusb.php]("http://www.ion-audio.com/ittusb.php")

Does anyone use one of these and if so how does it work with Ununtu? It looks like it ships with Audacity so that is no problem and it uses the USB Audio Codec which I don't know if that will be a problem or not. 

If anyone has another method of digitizing music from LPs any help would be appreciated. 

Thanks in advance

---

### Post by Kelimion on 2007-06-16
I don't have one of these, but what I do have is a Logitech USB headset.

Point in case is that it's properly detected (Feisty) and an extra soundcard shows up in moments. If as you say this turntable supports USB Audio, then it shouldn't be too much of a problem?

If they sell those turntables at a proper PC shop, you could ask them to hook it up to one of the PCs on display, pop in a bunty cd, and see if it comes up?

---

### Post by dabl on 2007-06-16
> **MLX said:**
> 
If anyone has another method of digitizing music from LPs any help would be appreciated. 


Heh.  Been digitizing 78's and 33's for about 6 weeks now.  I should organize my know-how into a seminar, but probably you would be the only attendee ....  :D   A lot of my special challenges, including special stylus and re-equalizer were due to the 78s, and their non-standard equalization issues -- 33s are much more of "current technology".

Here's the short course, which I did bother to write down, mainly as defense against senility:

A. Equipment Setup:
Receiver: Onkyo TX-8511
Turntable: Audio-Technica AT-PL-120
Cartridge: Stanton V500.V3
Stylus: Esoteric Sound D5130EJ
Re-Equalizer: Esoteric Sound
Computer:
1.Intel D975XBX motherboard, Intel Core 2 Extreme (X6800) CPU, 4 GB RAM
2.Integrated Intel HDA audio system (STAC 92xx chip)
	Software:
1.Ubuntu 7.04 Linux 64-bit low-latency OS
2.Audacity ver. 1.2.6
3.Gnome Wave Cleaner ver. 0.21-05

B. Process:
1.Set Audacity I/O to ALSA: HDA Intel: STAC 92xx (both record and playback), mono
2.Set Audacity Quality (Edit>Preferences>Quality) to sample at 48,000 Hz, 32-bit float
3.Set Audacity uncompressed file export format to WAV (Microsoft 16-bit PCM)
4.Clean the record side to be recorded, and also the stylus
5.Set turntable to 45 rpm
6.Stylus pressure works best in the 4-gram vicinity for most 78s &#8211; your mileage may vary
7.Lower tonearm and initiate &#8220;record&#8221; with Audacity
8.Test signal strength -- adjust input level to maximum possible while not exceeding ±1 dB
9.Capture unmodulated lead-in and end of side noise &#8211; you will need it for gwc de-noising
10.Capture the full side of a 78 in a single file
11.Save captured file in native Audacity .aup format
12.Export file as WAV file
13.Close Audacity (or start using it for the next capture ...)
14.Open Gnome Wave Cleaner (gwc), open exported WAV file
15.Zoom in 3 or 4 times, go to beginning or end unmodulated noise (whichever is worse), select as much noise as you can, avoiding music or the pop of the stylus touching down or the noise after the stylus exits the end of the music groove and enters the &#8220;landing zone&#8221; part of the groove.  Use this for your noise sample. Read up on gwc technique for more details.
16.Zoom back out, click in between the &#8220;two&#8221; tracks, and click &#8220;View>Select All&#8221;
17.First run de-click, then de-crackle, then de-noise (all under the &#8220;Edit&#8221; menu)
18.Manually de-click as many of the worst pops as you have time for
19.Save the cleaned file with a new file name
20.Open the cleaned file with Audacity, and insert silence and/or trim to a couple of seconds at the beginning and the end of the modulated signal
21.Select the entire signal, and change the speed from 45 to 78 rpm, with &#8220;Effect>Change Speed&#8221;
22.With the file still selected, normalize the signal level with &#8220;Effect>Normalize&#8221;
23.Export the resulting file as a WAV, with a new file name (this is the final file for the CD)
24.Or ... for really bad cases, open this 78 rpm normalized file in gwc, and run &#8220;de-click&#8221; and &#8220;de-crackle&#8221; on it, then call it &#8220;final for the CD&#8221;
25.Follow burning procedure for the CD burner of your choice


Now, there's some "Open Source" sharing !  :D

---

### Post by MLX on 2007-06-17
Thank you for the replys. It looks like this should work with Ubuntu. I will post back in a few weeks and tell my story of how it works with Ubuntu. 
dabl...I have your directions printed out and ready to go. Thanks again!

---

### Post by asdl on 2007-09-26
I had no problem getting Audacity to recognize the Ion USB turntable on my Ubuntu system. I simply plugged it in and found the ALSA USB codec as an option under EDIT/PREFERENCES/AUDIO IO. There were no downloads or installations necessary. I wish installing the lamemp3 was as easy.

---

### Post by benzs_s on 2008-01-14
Just a quick bump... yes, this will work fine on Audacity (insofar as it will RECORD then playback once you stop the recording), but i'm wondering if a program exists which will just PLAY the turntable without recording?

---

