---
title: "[SOLVED] Audio CD playing is disrupting periodically"
date: 2007-10-09
forum: Multimedia &amp; Video
---

### Post by perixx on 2007-10-09
Hello Guys,


I'm trying to make my new Xubuntu 7.04 installation fit for all-day-use; one of my major problems is that I cannot playback Audio CD's. As soon as I insert a CD it is automatically recognized. Gxine is starting up and begins to playback the first 6 seconds of the first track, then disrupting for 1 - 2 seconds, again playing 1 or 2 seconds and so on. 
It hardly can be caused by missing DMA settings for CDrom or HDD, as I've doublechecked this with hdparm - DMA is on. The DVD drive was tested at CSL and Master mode at secondary IDE port, with equal results by me.

I also tried an older Samsung DVD drive, which wouldn't work at all.

My hardware is set up as follows:
MSI MS-6330 Motherboard with 512MB SD-RAM, oboard sound
VIA AC'97 Codec (Card VIA 82C686A/B, Chip ICEnsemble ICE1232 - according to Alsamixer)
160GB ATA Hitachi HDD
Toshiba SD-M1502 DVD
ATI Rage 128 

As far as I understand, the ALSA-driver implementation should be ok, as otherwise there wouldn't be any sound at all - and at least the logon sound plays back.

I tested several different CD's with no success....

Additionally, there's no possibility to access the CD's directory directly: somehow Gxine's autoplay must be responsible for hooking the drive, making it impossible to mount or open it although the drive symbol is still on desktop after I close Gxine. I just will get 2 error messages saying sth. like 
mounting drive unsuccessful - couldn't mount drive - unknown error .... 
and 'Cannot mount volume. Invalid mount option when attempting to mount the volume.'


Can you help me please?

perixx

---

### Post by perixx on 2007-10-10
Isn't there any helpful chap out there that might have a clue on my problem...?

Update:

I turned off ICPA (=ACPI) an turned on 'PnP OS installed' in BIOS - no workie either....
I noticed, that every time the sound stops playing and begins again, the drive's LED stops burning for the blink of an eye. 
Btw., under XP I had no problems with playing back CD's with that drive and hardware, so it must be either Xubuntu or Gxine. 
I'd suspect the latter one, as I encountered lots of trouble with it also in all newer versions of Puppy. 
Or maybe there's some audio cache to be enabled somehow, somewhere?

Please help!

---

### Post by perixx on 2007-10-10
Update:

I've plugged in an old PCI audio card for verifying this issue, and still the same... periodically stopping/starting of audio CD playback.... so it can hardly be a matter of the onboard chip!

For the tested backup soundcard Alsamixer says:

card: M Audio Audiophile 24/96
chip: ICE1712


Anybody got ideas...??

---

### Post by perixx on 2007-10-11
Does REALLY nobody have the faintest idea on this problem ????
:-(((

---

### Post by perixx on 2007-10-12
Update: 

when I try to directly play a .wav file from HDD, Gxine pops up, freezes  at 80% CPU-load and can only be terminated by the process manager; no sound here....

How can this be??? Can Gxine play ANY format out-of-the-box!!?

perixx

---

### Post by perixx on 2007-10-12
Autoplaying Audio CD's starts Gxine, with a periodical 'mut/unmute' behaviour, secondwise. Playing .wav file from USB stick or HDD with Gxine freezes it at 80 % CPU-load.

I followed the 'Comprehensive Audio guide' as far as I could, but from what I've seen there, my driver setup should be ok...

I was able to play a .wav file via terminal > aplay 'soundfile.wav' (9MB) without any artifacts or disruptions !


I can't say wether my trouble is coming from 'bad' drive access or Gxzine / codecs. But it should be possible to play .wav files without any upgrades, if alplay can handle this aswell, now shouldn't it? I've just installed the w32codecs package, though I'm pretty shure this will not improve my situation...

Is there ANYBODY that has experience with Gxine and sound problem, PLEASE ???:confused:

HELP!!

---

### Post by perixx on 2007-11-03
I found a personal solution for me meanwhile:


getting rid of Gxine and installing SMplayer + Mozilla-Mplayer-plugin + w32codecs and some more :DD

apart from that, Xubuntu's Gxine couldn't even handle .wav file out of the box, that's why I'll mark this thread as 'unsolved'.


perixx

---

