---
title: "SoundConverter/Sound Converter MP3 and Ogg File Sizes"
date: 2008-03-09
forum: Multimedia Production
---

### Post by AlexInBlack on 2008-03-09
Preface: I've done two searches, once with the term "soundconverter" and once with "sound converter". My other terms were MP3 and Ogg. I looked through all threads that seemed to pertain and didn't find an answer to my question.

When I use SoundConverter to convert my FLAC collection to MP3/Ogg for use on my portable digital audio player (DAP), using the High setting for Ogg and High/VBR setting for MP3, I've found that the Ogg converted files, for some reason, are converting at a higher bitrate than the MP3 ones, even from the same source. For example, my Ogg version of Nine Inch Nail's _The Downward Spiral_ is 88 MB, with Nautilus generally giving 192 kbps and the MP3 version is 70.5 MB, giving 150 kbps, both converted from the same FLAC files.

I haven't done AB/X tests to see if there's a difference in quality, since my sound card isn't very high quality and AB/X tests using my higher quality DAP would either be a hassle (if I had someone else help) or wouldn't be objective.
However, all the codec comparisons I've read about have said that Ogg generally gives higher quality than MP3 at the same bitrate. Is the SoundConverter setting for High not correct for MP3?

---

### Post by logos34 on 2008-03-09
nautilus file properties tab is only showing you the nominal bitrate for ogg (same if you look at it in a media player), while it gives the average bitrate for mp3.  The target bitrate for 'high' setting for either format in soundconverter is ~192 (~quality setting -q 6 in ogg, -V 2 --vbr-new in mp3), but the average is almost always lower.  To find out the average rate for your oggs, open a terminal and cd to the folder, and type:

ogginfo *.ogg

Actually -q 5 (~160kbps) for ogg should be transparent (or nearly) and sound as good as mp3 at 192kbps

---

### Post by AlexInBlack on 2008-03-10
Well, even if the bitrates given by Nautilus are imprecise, the actual file sizes still show that the ogg files are being encoded larger or more bits per second than the mp3 files.
Does this means that ogg on Normal in SoundConverter is equivalent in sound quality to mp3 on High or that in general, in SoundConverter, the sound quality in ogg at a certain quality level is equivalent to that of mp3 of one level higher?
I know that SoundConverter's target bitrates are 64, 96, 128, 192, and 256.
Is there a reason that the ogg files and mp3 files,set at the same target bitrates, end up with the ogg files being encoded closer to the target of 192 and the mp3 files at a lesser bitrate?

---

### Post by logos34 on 2008-03-10
yeah, you're right, the size shows something is amiss.   I never use Soundconverter, but let see what I come up with on a couple of files.

---

### Post by logos34 on 2008-03-10
Ok I just checked it out with a flac file conversion and it seems there's a problem with MP3 at High and Very High VBR settings.  Both give out files almost exactly the same size (~158-159kbps average) despite the fact that the target bitrates are 192 and 256, respectively.  The latter is way off and the former should be up around 175+ kbps average.

Even 'normal' setting is off--taget bitrate of ~128 and yet the file averages MORE, 145kbps. Maybe that's a typo and the target bitrate is really 160, dunno.

It's supposed to use the gstreamer-lame plugins if installed, yet this is what mediainfo shows:

Codec                        : MPEG-1 Audio layer 3
> Codec profile                : Joint stereo
Bit rate mode                : VBR
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz
Resolution                   : 16 bits
[COLOR="Red"]Writing library              : Gogo (after 3.0)[/COLOR]

Shouldn't it say lame?

I don't know where the configuration file is for gstreamer-lame or the app.

My advice is use another converter.  dBpoweramp on wine works great for me. Lots of options. Foobar2000 converter is another.  Then there's Gnormalize and TransKode (KDE though).

---

### Post by AlexInBlack on 2008-03-11
Thanks for the help. I guess I'll use some other Linux-native converters.
I couldn't get Exact Audio Copy to run under Wine despite the copious amounts of guides I tried to use, so I'll leave Wine for another day.

---

### Post by logos34 on 2008-03-11
> **AlexInBlack said:**
> Thanks for the help. I guess I'll use some other Linux-native converters.
I couldn't get Exact Audio Copy to run under Wine despite the copious amounts of guides I tried to use, so I'll leave Wine for another day.

I know what you mean...I had trouble too at first, despite checking and rechecking settings in wine config.  In my case it wouldn't recognize the cdrom drive. Finally I used the native win32 apsi interface and, voila, it worked. 

As for soundconverter, I got curious and checked the website forums and found [this thread]("http://developer.berlios.de/forum/message.php?msg_id=40517"). The OP alludes to some gstreamer issue with VBR lengths, about which I am unaware.  The responder says the modes currently recognized are 1,3,5,6,7...It skips 2 and 3 (go figure) so I tried setting Soundconverter settings in gconf-editor to vbr '2' instead, but it won't take.  Still outputs ~159kbps.

---

### Post by vikrant82 on 2008-03-11
Pissed at soundConverter (was getting inexplicable/unpredictable bitrates), I finally settled upon lame and soundKonverter for my mp3 conversions. 

I wrote about the same [here.]("http://kakku.wordpress.com/2008/02/24/music-compression-formats-bitratesvbrcbrabr-codecs-lame-ogg-vorbis-aac/")

---

### Post by JPorter on 2008-06-30
This is a killer bug. Has anyone filed a bug report on this?

And why is the Ubuntu repository version of Sound Converter not updated to the current 1.3.1?  This may have been fixed already.



Homepage for Gnome SoundConverter:  [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

---

