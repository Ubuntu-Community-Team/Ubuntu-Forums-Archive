---
title: "converting WMA to flac/wv/shn"
date: 2010-05-31
forum: Multimedia Software
---

### Post by shantiq on 2010-05-31
i have a whole bunch of wma files i want to convert to a more liked format like wv flac or shn

shntool does not seem to want to do that

soundconverter and soundkonverter both refuse too



any ideas?    my wma format is wma1 or wmal cannot tell if is is 1 the number or l the letter L


if you cannot be bothered to read the whole post a summary of info found goes like this    simple solution     1.   they play in xine straight off   xine is in your synaptic


2.  to convert quickly install dBpoweramp under wine   again quick and no fuss[

---

### Post by cascade9 on 2010-05-31
All the tools refused to run? You probably dont have the w32codecs installed (w64codecs on 64bit). 

If they are wmal (L) then they are wma 'lossless' so converting to flac isnt evil (like it would be to convert lossy wma to lossless codecs). Still, if you have the CD, it would be better to just rerip- wma lossless has issues. 

.flac is probably your best bet, .wv isnt bad but I'd rather have flac for a lot of reasons. Dont use .shn, its totally overpowered by the newer lossless codecs in every regard.

---

### Post by shantiq on 2010-05-31
> **cascade9 said:**
> All the tools refused to run? You probably dont have the w32codecs installed (w64codecs on 64bit). 

If they are wmal (L) then they are wma 'lossless' so converting to flac isnt evil (like it would be to convert lossy wma to lossless codecs). Still, if you have the CD, it would be better to just rerip- wma lossless has issues. 

.flac is probably your best bet, .wv isnt bad but I'd rather have flac for a lot of reasons. Dont use .shn, its totally overpowered by the newer lossless codecs in every regard.


[B][COLOR="Blue"]i have  the w32 installed  not sure what it is


thanx for clearing the L thing i shall look around for that


man i am a big shorten fan it is the clearest of all the formats to my ear[/COLOR][/B]

---

### Post by shantiq on 2010-05-31
[B][COLOR="Blue"]ok not a perfect ubuntu solution but since i now know it is wma lossless(thank you cascade9)i browsed the net and lo and behold there is a way that works


installing dbpoweramp under wine and installing the wma plugin then you can convert your files   here is [the howto]("http://thestrayworld.com/2010/04/23/how-to-convert-wma-lossless-to-flac-in-ubuntu-karmic/") i found 

only had to use the second part   Install dBpoweramp Music Converter




OF COURSE if anyone has a linux/ubuntu only solution i will gladly follow that [/COLOR][/B]

---

### Post by mc4man on 2010-05-31
> 
OF COURSE if anyone has a linux/ubuntu only solution

It's probable that dbpoweramp offers most 'complete' solution, if tags matter. (been a while since I used it, forget if it transfers wmal tags), and is easier to use 

Anyway...

If a same name batch convert in linux (no tags) then atm only mplayer with 32 bit codecs will do
mplayer to .wav - then .wav to whatever

Basic batch command to .wav 
At dir. prompt where wma's are, (- beware of characters in name that may hang decoding/encoding -  one that will is a "," (comma), remove any from track names

```
for f in *.wma;  do mplayer "$f" -vo null -vc null -ao pcm:waveheader:fast:file="${f%.wma}.wav"; done
```

You could also pipe from mplayer to whatever, one way is with named pipes 

Ex. of batch named pipes wmal to flac, same name, spaces don't matter, *some characters may, most don't*

Open 2 terminals at dir. prompt where wma's are (typically an album

In first terminal
```
mkdir tmp && for f in *.wma; do mkfifo ./tmp/"$f"; done && for f in ./tmp/*.wma; do flac "${f%.wma}.wma"; done
```
press enter, cursur will be blinking

Then in 2nd term.
```
for f in *.wma;  do mplayer "$f" -vo null -vc null -ao pcm:waveheader:fast:file=./tmp/"${f%.wma}.wma"; done
```

After done in either terminal to remove pipe files

```
cd ./tmp && rm *.wma
```

---

### Post by cascade9 on 2010-06-01
@ mc4man- dbpower amp should be any better than foobar. IIRC foobar doesnt need a plugin to play/convert wma-lossless either.  

Also, I've seen threads here about how wma-lossless wotn play even with w32codecs installed. If thats the case (which it could very well be) then that is why soundconverter wouldnt work with wma-lossless. I dont know if mplayer will play the files, if it does then that method should work...i..f not, then its possible that VLC would, but I have no idea. I dont have a single wma file to test with, let alone a wma-lossless. ;) 

> **shantiq said:**
> **[COLOR=Blue]i have  the w32 installed  not sure what it is[/COLOR]**

Its a package that lets you play .wma, .wmv, .rm (and probably other codecs I've forgotten about).
[B][COLOR=Blue]
[/COLOR][/B]> **shantiq said:**
> **[COLOR=Blue]thanx for clearing the L thing i shall look around for that[/COLOR]**

 Better to look for .flac, .wv, they are better cdoecs with none of the problems of wma-lossless. 
[B][COLOR=Blue] 
[/COLOR][/B]> **shantiq said:**
> **[COLOR=Blue]man i am a big shorten fan it is the clearest of all the formats to my ear[/COLOR]**

That is probably more to do with the decoder than anything else. All the lossless formats should sound the same (in theory).

---

### Post by mc4man on 2010-06-01
> Also, I've seen threads here about how wma-lossless wotn play even with w32codecs installed. If thats the case (which it could very well be) then that is why soundconverter wouldnt work with wma-lossless.

It's not enough to just have 32codecs installed - the app must also support decoding thru dmo, at present no gstreamer app does.

A 32 bit mplayer, vlc built w/ dmo enabled, and most xine based players can decode wmal

(here on lucid I get wmal decoding thru mplayer, vlc, and totem-xine


Edit:
 the latest foobar2000 requires  the presence of windows media runtime libraries in system32 to decode wmal
(have it here

---

### Post by cascade9 on 2010-06-01
> **mc4man said:**
> It's not enough to just have 32codecs installed - the app must also support decoding thru dmo, at present no gstreamer app does.

A 32 bit mplayer, vlc built w/ dmo enabled, and most xine based players can decode wmal

(here on lucid I get wmal decoding thru mplayer, vlc, and totem-xine

Ahh, so thats the reason why gstreamer programs wont work with wma-lossless,a dn why mplayer will (well, people say it will, I dotn have any wma files at all anymore). Thanks for the info ;) 

> **mc4man said:**
> 
Edit:
 the latest foobar2000 requires  the presence of windows media runtime libraries in system32 to decode wmal
(have it here

It does? *blinks* I cant be sure if the earlier versions needed that or not, no wma here. I'm still stuck on 0.9.5.5 since the later versions dont support SCP (single column playlist).

---

### Post by mc4man on 2010-06-01
> It does?
I think so... actually to test something ( drop in desktop/panel launchers), I ended up with both 0.8.3 and 1.0.3 both being installed.
The 0.8.3 has a plugin,(foo.wma.dll), the 1.0.3 doesn't, I don't believe either played wmal until adding the runtime files. (though don't exactly remember

You can always get a sample for testing here (many others also

[http://samples.mplayerhq.hu/A-codecs/lossless/](http://samples.mplayerhq.hu/A-codecs/lossless/)

---

### Post by cascade9 on 2010-06-01
> **mc4man said:**
> I think so... actually to test something ( drop in desktop/panel launchers), I ended up with both 0.8.3 and 1.0.3 both being installed.
The 0.8.3 has a plugin,(foo.wma.dll), the 1.0.3 doesn't, I don't believe either played wmal until adding the runtime files. (though don't exactly remember

You can always get a sample for testing here (many others also

[http://samples.mplayerhq.hu/A-codecs/lossless/](http://samples.mplayerhq.hu/A-codecs/lossless/)

Really streching my memory, but 0.8.3 and earlier versions needed the foo_wma plugin, 0.9 versions dont. I know I did have some .wma files for a while when I was using 0.9, and I never d/led a plugin (and had WMP totally removed as well). Well, I think I didnt d/l a plugin, and there isnt one in my 'folder of foobits' :lolflag:

IIRC, the 0.8.3 and earler versions had the .ape decoder as standard, but it was discontinued with 0.9, and wma support was added. (out of the box, you can play almost anythign with plugins). 

Thanks for the link, I might have to grab a .wma lossless file just for testing reasons. ;) Gawds only know I wont be ripping one, WMP makes me sick :|

---

### Post by shantiq on 2010-06-05
===

---

### Post by shantiq on 2012-01-02
and 2 years later :KS   still the only route for me with **wmal** files  **on 64-bit**

[**&#9658;&#9658; DBpoweramp**]("http://www.dbpoweramp.com/codec-central-windows-media-audio.htm")

with  [**&#9658;&#9658; wma codec**]("http://www.dbpoweramp.com/codec-central-windows-media-audio.htm")



Unless anyone knows new tricks for wmal  [the lossless version]

dbpoweramp does a great job of turning them into flacs with all tags intact  but i still see no way to play the wmal in Ubuntu......

Any of you know differently?

---

### Post by mc4man on 2012-01-02
[http://ubuntuforums.org/showpost.php?p=11393209&postcount=1891](http://ubuntuforums.org/showpost.php?p=11393209&postcount=1891)
Seems that ffmpeg has added wmal decoding - problem is that to date I've seen no indication that it works at all.
If it did then would expect it to be included in mplayer at some point.

What's curious is this ticket (fixed), maybe the decoder works somewhere for someone(s), certainly not here. 
[https://avcodec.org/trac/ffmpeg/ticket/825#comment:8](https://avcodec.org/trac/ffmpeg/ticket/825#comment:8)

Here's the current error on a sample wmal ((see the same whether files were produced by wmp-9.1 or 10
> 
$ ffplay -strict experimental '/home/doug/Music/luckynight.wma'  ffplay version git-2012-01-01-2e0efa3, Copyright (c) 2003-2012 the FFmpeg developers
  built on Jan  1 2012 14:21:03 with gcc 4.6.2
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab
  libavutil      51. 33.100 / 51. 33.100
  libavcodec     53. 49.101 / 53. 49.101
  libavformat    53. 29.100 / 53. 29.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 57.101 /  2. 57.101
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  5.100 /  0.  5.100
  libpostproc    51.  2.100 / 51.  2.100
Input #0, asf, from '/home/doug/Music/luckynight.wma':
  Metadata:
    title           : Lucky Night
    artist          : Jody Marie Gnant
    copyright       : 1995 Sirius Publishing
    comment         : 1-minute song sample demonstrating Windows Media lossless audio compression
    WMFSDKVersion   : 9.00.00.2980
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 1
  Duration: 00:01:00.48, start: 0.000000, bitrate: 871 kb/s
    Stream #0:0(eng): Audio: wmalossless (c[1][0][0] / 0x0163), 44100 Hz, stereo, flt, 868 kb/s
[wmalossless @ 0xa429b20] not enough space for the output samples

---

### Post by shantiq on 2012-01-02
hi there mc4    well that is some movement at any rate   .....

one day soon then  :KS

and Best Wishes for 2012          shan

---

### Post by andrew.46 on 2012-03-02
> **shantiq said:**
> Unless anyone knows new tricks for wmal  [the lossless version]

Newest FFmpeg now has a working decoder and thus FFplay plays wmal :). MPlayer should follow soon enough... This has happened at a very opportune moment for me as I am finally building myself a decent computer which I intend to run as a 'pure' 64bit system!

---

### Post by ron999 on 2012-03-03
hmm...
FFmpeg now converts wmal too.:D
```
ffmpeg -strict -2 -i luckynight.wma luckynight.flac
```

---

### Post by shantiq on 2012-03-03
thanks guys great news:KS

---

### Post by shantiq on 2012-03-04
guys where do i get this latest version which handles wmal  ?

the one i have one my system does not as yet   > ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1




thanx

---

### Post by andrew.46 on 2012-03-04
Try here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by shantiq on 2012-03-04
> **andrew.46 said:**
> Try here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Thank you Andrew and i have used Fake's route before and very thorough it is


but it does take time
is there no shortcut [says the lazy guy] and if not how long will it be do you think before the new changes find their way to the vanilla version if any guesses are possible [IMG]http://img838.imageshack.us/img838/5745/smilie33.png[/IMG]

---

### Post by winh8r on 2012-03-04
You seem to be having some success with it now, there is however another converter which I have found to be very good too

pacpl is a PERL converter/ripper/tagger and has plenty of other options useful for audio conversion.

here is the description from the man page:

```
DESCRIPTION
       Perl Audio Converter is a tool for converting multiple audio types from
       one format to another. It supports AAC, AC3, AIFF, APE, AU, AVR, BONK,
       CAF, CDR, FAP, FLA, FLAC, IRCAM, LA, LPAC, MAT, MAT4, MAT5, M4A, MMF,
       MP2, MP3, MP4, MPC, MPP, NIST, OFR, OFS, OGG, PAC, PAF, PVF, RA, RAM,
       RAW, SD2, SF, SHN, SMP, SND, SPX, TTA, VOC, W64, WAV, WMA, and WV.  It
       can also convert audio from the following video extensions: RM, RV,
       ASF, DivX, MPG, MKV, MPEG, AVI, MOV, OGM, QT, VCD, SVCD, M4V, NSV, NUV,
       PSP, SMK, VOB, FLV, and WMV. A CD ripping function with CDDB support,
       batch conversion, tag preservation for most supported formats,
       independent tag reading/writing, and extensions for Amarok, Dolphin,
       and Konqueror are also provided.
```


Hope this is of some use.

---

### Post by shantiq on 2012-03-04
thanx for this and i love pacpl too very good program but i do not think it handles wmal   the lossless version of wma  only regular wma  [img]http://img839.imageshack.us/img839/5577/smilie39.png[/img]

---

### Post by andrew.46 on 2012-03-05
I suspect these changes will not make it to Precise Pangolin as it will be out soon enough. You may have to revisit this most excellent guide :).

---

### Post by shantiq on 2012-03-05
it is most excellent forgive my laziness [img]http://img96.imageshack.us/img96/2284/smilieubu921.png[/img]

---

### Post by shantiq on 2012-07-15
ok took the plunge 

> ffmpeg
ffmpeg version git-2012-07-15-2c31ed3 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jul 15 2012 11:47:34 with gcc 4.6.3


  and yes all there:KS


>  [FONT="Franklin Gothic Medium"][COLOR="DarkRed"]D A D    wmalossless     Windows Media Audio Lossless[/COLOR][/FONT]
 D A D    wmapro          Windows Media Audio 9 Professional
 DEA D    wmav1           Windows Media Audio 1
 DEA D    wmav2           Windows Media Audio 2
 D A D    wmavoice        Windows Media Audio Voice
 DEVSD    wmv1            Windows Media Video 7
 DEVSD    wmv2            Windows Media Video 8
 D V D    wmv3            Windows Media Video 9
 D V D    wmv3_vdpau      Windows Media Video 9 VDPAU
 D V D    wmv3image       Windows Media Video 9 Image



which is a great step forward  will have to wait to encode tho :KS:KS
it is happy with 16-bit but not as yet with 24-bit wmal  [samples [**here**]("http://www.linnrecords.com/linn-downloads-testfiles.aspx")]

---

### Post by mc4man on 2012-07-15
The 24 bit wmal _still remains something for 32bit & w32codecs,_ linux players supporting would be 
mplayer
vlc (if built with --enable-loader
possibly a xine based player

Though if you've done builds of vlc, mplayer with current FFmpeg then you'd need to specify to use dmo instead.
dmo in vlc for wmal is somewhat spotty, sometimes you get sound, sometimes not
For vlc to switch to w32codecs from default avcodec
vlc --codec dmo /path/to/file

Way back when we were exploring wmal in a 32bit  vlc showed screen playing that very  sample - post 8, [http://ubuntuforums.org/showthread.php?t=1155698](http://ubuntuforums.org/showthread.php?t=1155698)

For mplayer to use this w32codec
 mplayer -ac wma9dmo /path/to/file

---

### Post by ron999 on 2012-07-15
> **mc4man said:**
> The 24 bit wmal _still remains something for 32bit & w32codecs,_ linux players supporting would be 
mplayer
vlc (if built with --enable-loader

Yup, I can confirm that "recit24bit.wma" plays ok with mPlayer and "vlc --codec dmo".
:D

And VLC does a good conversion job:-
```
cvlc --codec dmo recit24bit.wma --sout="#transcode{acodec=s24l}:std{access=file,mux=wav,dst='recit24bit.wav'}" vlc://quit

```

---

### Post by mc4man on 2012-07-15
On an obscure note - foobar2000 can do these also, you just need to place windows media runtime files in ~/.wine/drive_c/windows/system32
(acquiring those files is done in varying ways [...]("http://downloads.phpnuke.org/en/download-item-view-g-v-z-a-v/WINDOWS%2BMEDIA%2BFORMAT%2B9%2BRUNTIME%2BFILES.htm")

---

### Post by shantiq on 2012-07-15
thanx guys for sterling feedback as usual


will try all of the above


Had already seen foobar has no problem with any of those:KS
**and** will convert 24-bit wma to a 24-bit flac or wv with no grumbles whatsoever

---

