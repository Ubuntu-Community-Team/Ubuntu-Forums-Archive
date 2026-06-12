---
title: "mp3 file created from Audacity report incorrect bitrate and length"
date: 2009-05-04
forum: Multimedia Software
---

### Post by dwasifar on 2009-05-04
I've been ripping vinyl to mp3 using Audacity and I'm running into odd things when I try to use the resulting files.

I've been exporting mp3s as VBR 0 (best quality), joint stereo.  This is more or less the same encoding I use when ripping CDs (lame --preset extreme in that case) and should result in a VBR file with an apparent bitrate in the mid-200s.  But when Amarok sees the file, it reports very low bitrate, in the 80s or 90s, and exaggerated length.  And Nautilus seems to have trouble reporting it correctly in the Properties menu.  My UPNP server has similar issues.

[Here is an example file.]("http://www.dwasifar.com/safari.mp3")  

When you look at the file properties in Nautilus, it shows up with varying properties each time you look at it; usually close to correct, but not exactly, with times varying from 2:02 to 2:38, and bitrates in the low to mid 200s.  Amarok reports it as bitrate 96, time 6:05, which is way off.  My UPNP server (TwonkyMedia) also reports it as 6:05; it doesn't show me bitrates.

What the sam hill is going on here?

---

### Post by logos34 on 2009-05-04
I find [MediaInfo]("http://mediainfo.sourceforge.net/en/Download") to be indispensible in getting the nitty-gritty on mp3 files (or any for that matter)

---

### Post by dwasifar on 2009-05-04
I have a workaround.  Sort a a forehead-slappingly obvious one, really.  I save to .wav instead of .mp3 in Audacity, then use lame to create the .mp3 from the .wav file. 

But I would still like to know what's going on.

---

### Post by logos34 on 2009-05-05
> **dwasifar said:**
> 
But I would still like to know what's going on.

I agree.  Why isn't it exporting correctly (using libmp3lame.so.0)?

---

### Post by logos34 on 2009-05-06
Okay, I even tried pointing audacity to the newer lame version I just compiled and installed in /usr/local/lib.  It sees it fine as "3.98.2".

So I rippped a cd track to wav and mp3, then opened the wav in audacity to export as mp3 and compare the two.  They aren't really close in size.  Nautilus can't read them correctly (assuming mediainfo is, which looks to be the case)

Ripped by ABCDE with lame opts "-V 2":
> 
General #0
Complete name                : 01.No_More_Walks_In_The_Wood.mp3
Format                       : MPA1L3
File size                    : 2.70 MiB
PlayTime                     : 2mn 921ms
Bit rate                     : 187 Kbps
Album                        : Long Road Out Of Eden [Disc 1]
Track name                   : No More Walks In The Wood
Track name/Position          : 01
Performer                    : The Eagles
Genre                        : Country
Recorded date                : 2007
Writing library              : LAME3.98r

Audio #0
Codec                        : MPEG-1 Audio layer 3
Codec profile                : Joint stereo
Bit rate mode                : VBR
Bit rate                     : 187 Kbps
Minimum bit rate             : 32 Kbps
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz
Resolution                   : 16 bits
Writing library              : LAME3.98r
Encoding settings            : VBR (mtrh)




Wav file of above track exported by Audacity to mp3 (Variable, V 2, standard, stereo):

> General #0
Complete name                : eagles_cd1_track1_audacity.mp3
Format                       : MPA1L3
File size                    : 2.97 MiB
Writing library              : LAME3.98.2

Audio #0
Codec                        : MPEG-1 Audio layer 3
Bit rate mode                : VBR
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz
Resolution                   : 16 bits
Writing library              : LAME3.98.2


(Variable, V 2, fast, joint stereo)

> General #0
Complete name                : eagles_track1_audacity_fastvbr.mp3
Format                       : MPA1L3
File size                    : 2.89 MiB
Writing library              : LAME3.98.2

Audio #0
Codec                        : MPEG-1 Audio layer 3
Codec profile                : Joint stereo
Bit rate mode                : VBR
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz
Resolution                   : 16 bits
Writing library              : LAME3.98.2

Nautilus properties>media tab shows 'CBR' and bitrate '160'

???

Add: oh, and same thing as you with Amarok--gets the times and bitrates all wrong--except for the first one encoded directly by lame, which appears perfectly with correct track title, number, bitrate and time

---

### Post by mc4man on 2009-05-06
I didn't notice any play or time issues, (exactly the same.

Audacity seems to use the equivalent of vbr-old while lame use vbr-new by default, the Aud. mp3 being bigger at a slightly higher but not necessarily better br.

(both set to -V 2

Aud.
> 
Duration                         : 3mn 18s

Bit rate mode                    : Variable

Bit rate                         : 212 Kbps

Minimum bit rate                 : 32.0 Kbps

Channel(s)                       : 2 channels

Sampling rate                    : 44.1 KHz

Resolution                       : 16 bits

Writing library                  : LAME3.98r

Encoding settings                : [COLOR="Red"]VBR (rh)[/COLOR]



Lame (abcde

> Duration                         : 3mn 18s

Bit rate mode                    : Variable

Bit rate                         : 193 Kbps

Minimum bit rate                 : 32.0 Kbps

Channel(s)                       : 2 channels

Sampling rate                    : 44.1 KHz

Resolution                       : 16 bits

Writing library                  : LAME3.98r

Encoding settings                : [COLOR="Red"]VBR [/COLOR][COLOR="Red"](mtrh)[/COLOR]

Aud. doesn't seem like best choice to do the mp3 encode

---

### Post by logos34 on 2009-05-06
> **mc4man said:**
> Audacity seems to use the equivalent of vbr-old while lame use vbr-new by default

That's what I'm thinking...Seems like it's using the 'alt-preset' settings, but according to [this]("http://wiki.hydrogenaudio.org/index.php?title=Lame#Hey.21_What_happened_to_.22--alt-preset.22.3F") you can still end up with the same output, so not really sure what audacity is doing.  The only thing you can choose is vbr, cbr, abr, bitrate range, fast, standard, and stereo mode. I even tried to specify "external compressor" or whatever in the dropdown menu instead of mp3, and entered the lame command on the line, but nothing happens. ('/usr/local/bin/lame -V 2 ...')

I agree about Audacity not being good choice to export to mp3.  Personally I'd just save as wav and then manually run lame on it, + add id3 tags.

---

### Post by mc4man on 2009-05-06
> The only thing you can choose is vbr, cbr, abr,......

My aud has a 'preset' option, but even with that it still comes out with

VBR (rh)

> 
Personally I'd just save as wav and then manually run lame on it, + add id3 tags. 
Best advice for anyone looking and using aud.

---

### Post by dwasifar on 2009-05-09
Yeah, I'm just using the workaround now, save to wav and then lame from commandline and add tags in Kid3.  I never knew lame had such an interesting text-mode graph to display its progress.  :)

The thing that still puzzles me is why the same Audacity-created file can report different values every time you look at it in Nautilus.  There must be some sampling or estimating process going on to produce them, which would mean they're not stored explicitly.  Maybe that is actually the problem.

---

### Post by logos34 on 2009-05-09
> **dwasifar said:**
> Yeah, I'm just using the workaround now, save to wav and then lame from commandline and add tags in Kid3.  I never knew lame had such an interesting text-mode graph to display its progress.  :)

yeah, I love that little bitrate histogram...been default for some time I think

> The thing that still puzzles me is why the same Audacity-created file can report different values every time you look at it in Nautilus.  There must be some sampling or estimating process going on to produce them, which would mean they're not stored explicitly.  Maybe that is actually the problem.


Don't trust anything nautilus reports about a media file ('audio' tab)...I think it may use gstreamer libs to read them, not sure though...Use [MediaInfo]("http://mediainfo.sourceforge.net/") or some other similar app.

---

