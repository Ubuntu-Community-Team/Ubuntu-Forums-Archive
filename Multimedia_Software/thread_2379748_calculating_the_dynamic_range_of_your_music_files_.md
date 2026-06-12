---
title: "calculating the dynamic range of your music files in Ubuntu"
date: 2017-12-09
forum: Multimedia Software
---

### Post by shantiq on 2017-12-09
If you are interested in calculating the dynamic range of your music files you can use the [foobar2000 1.3.16 / Dynamic Range Meter 1.1.1]("http://www.pleasurizemusic.com/de/free-downloads") under Wine

> DR (or Dynamic Range) is a term for the degree of dynamic variation within a piece of music or album. Low values (e.g. DR3) reflect a high abuse of compression. Tracks that are DR3 have a range of three decibels between the average and peak program signal. A natural recording, with a low amount of dynamic processing, would have a much higher DR value (e.g. DR12+). The DR system is intended to avoid black and white judgment of dynamic quality. While DR7 is low for rock music or very low for Jazz, it is quite acceptable for electronic club music which has nowadays often values below DR4. All values above DR12 have generally a high dynamic quality.


OR


you can use a native Linux command-line tool >>


DR14 T.meter >>

[https://sourceforge.net/projects/dr14tmeter/files/dr14tmeter-1.0.16/dr14tmeter_1.0.16-1_all.deb/download](https://sourceforge.net/projects/dr14tmeter/files/dr14tmeter-1.0.16/dr14tmeter_1.0.16-1_all.deb/download)


it may tell you on 16.04 that 2 things are missing

faac and python-support so >> 

```
wget http://launchpadlibrarian.net/109052632/python-support_1.0.15_all.deb
sudo dpkg -i python-support_1.0.15_all.deb
```

```
sudo apt install faad
```


then you can install DR14 T.meter deb linked above
==========

USAGE:

&#9679; enter a folder and run ```
dr14_tmete*r*
```
&#9679; for a single file you run>>```
dr14_tmeter -f *NAMEOFFILE*
```


It gives you this kind of reading [here on a digitized cassette]

```
&#65279;----------------------------------------------------------------------------------------------    
 Analyzed: Berlin /  Artist: Lou Reed
----------------------------------------------------------------------------------------------    
DR    Peak    RMS    Duration    Title [codec]    
----------------------------------------------------------------------------------------------    
 DR12     -0.00 dB     -17.49 dB    25:00    01 - A-Berlin-Lady Day-Men Of Good Fortune-Caroline Says-How Do You Think It Feels-Oh Jim      [flac]    
 DR13     -0.00 dB     -19.08 dB    25:14    02 - B-Caroline Says It-The kids-The bed-Sad Song      [flac]    
----------------------------------------------------------------------------------------------    
 Number of files:    2
 Official DR value:  DR13
    
 Sampling rate:          48000 Hz
 Average bitrate:          1750kbs 
 Bits per sample:          32 bit
    
Dr14 T.meter 1.0.16 
==============================================================================================    

```

foobar2000 1.3.16 / Dynamic Range Meter 1.1.1 under Wine   gives this


```
foobar2000 1.3.16 / Dynamic Range Meter 1.1.1
log date: 2017-12-09 07:25:45

--------------------------------------------------------------------------------
Analyzed: Lou Reed / Berlin
--------------------------------------------------------------------------------

DR         Peak         RMS     Duration Track
--------------------------------------------------------------------------------
DR12       0.00 dB   -16.62 dB     25:01 0A-A-Berlin-Lady Day-Men Of Good Fortune-Caroline Says-How Do You Think It Feels-Oh Jim
DR13       0.00 dB   -18.25 dB     25:15 0B-B-Caroline Says It-The kids-The bed-Sad Song
--------------------------------------------------------------------------------

Number of tracks:  2
Official DR value: DR13

Samplerate:        48000 Hz
Channels:          2
Bits per sample:   24
Bitrate:           1748 kbps
Codec:             FLAC
================================================================================


```

---

### Post by marseille2 on 2017-12-10
Very nice! This is helpful:)

---

### Post by djfake2 on 2018-09-21
thank you for the help!

---

