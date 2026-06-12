---
title: "an interesting very high quality sound format"
date: 2010-07-11
forum: Multimedia Software
---

### Post by shantiq on 2010-07-11
was playing with an old ripper earlier on today called **[COLOR="Red"][arson]("http://ubuntu.unlp.edu.ar/ubuntu/pool/universe/a/arson/")[/COLOR]** (also attached here below) and found a lossless format which I had not come across before called [Sun au]("http://en.wikipedia.org/wiki/Au_file_format")   extension is .au


the sound quality is astounding and of course the size of the files huge but this might be of interest to real audio fans people who mind sound quality over everything else

files play in qmmp/[deadbeef]("http://ubuntuforums.org/showthread.php?t=1503749")/audacious/vlc   

and can be converted with soundkonverter if you want a smaller format later on

so i shall attach the ripper    av a try it is really very good/clear a sound

---

### Post by shantiq on 2010-07-11
```

```can also rip to au using icedax ( always found icedax/wodim the kindest to my machine/it is quasi soundless change au at the end of the line of code for wav if you want to experiment)


```
icedax dev=/dev/cdrom -vall cddb=0 -B -Oau
```


if you want other formats


```

-O  audiotype  --output-format
              can be wav (for wav files) or aiff (for apple/sgi aiff files) or
              aifc (for apple/sgi aifc files) or au or sun (for  sun  .au  PCM
              files)  or  cdr  or  raw (for headerless files to be used for cd
              writers).
```



also you can rip to au with pacpl

```
sudo apt-get install pacpl

```


```
pacpl  --outdir /home/yourname/Desktop  --rip all  -t au
```

---

### Post by cascade9 on 2010-07-11
Only some of the .au files are lossless (there are lossy .au files as well). 

I wouldnt bother, lossless is lossless, and its better to use flac IMO (too many codecs means that the eventual 'winner' from the lossless formats will be something lame, like ALAC or worse yet WMA-lossless.

---

### Post by shantiq on 2010-07-11
> **cascade9 said:**
> Only some of the .au files are lossless (there are lossy .au files as well). 

I wouldnt bother, lossless is lossless, and its better to use flac IMO (too many codecs means that the eventual 'winner' from the lossless formats will be something lame, like ALAC or worse yet WMA-lossless.


well cascade the sound is really good on these files just try one track maybe and compare t a flac-8 or a .shn tell me what you hear/think


also there never will be a winner i hope plurality is best otherwise you end up with the mister Gates of this world  i still think shorten is the best but am impressed with this au. 

ps i really like alac too but agree on wmal

---

### Post by cchhrriiss121212 on 2010-07-11
> **shantiq said:**
> well cascade the sound is really good on these files just try one track maybe and compare t a flac-8 or a .shn tell me what you hear/think

ps i really like alac too but agree on wmal
Maybe I'm wrong on this but shouldn't all lossless formats sound the same? The only difference would be file size and compatibility right?

---

### Post by shantiq on 2010-07-11
well yes that is the science but listen hard and tell me

i have had this debate so many times


and i always come back to the ears not the science

if you hear no difference that is cool too

earlier on i ripped a track to flac-5 and to au the flac is 40Mb the au 156Mb are we saying the 2 files carry exactly the same info?

i hear differently

---

### Post by cchhrriiss121212 on 2010-07-11
> earlier on i ripped a track to flac-5 and to au the flac is 40Mb the au 156Mb are we saying the 2 files carry exactly the same info?
Is .au always 4 times the size of flac? Roughly thats about the same size as .wav, which might explain why flac has been more popular
I would say the difference you hear is the placebo affect, flac is lossless so there is no way that another lossless container will retain any extra information. Where do you think this extra info can come from?

---

### Post by cascade9 on 2010-07-11
> **cchhrriiss121212 said:**
> Maybe I'm wrong on this but shouldn't all lossless formats sound the same? The only difference would be file size and compatibility right?
 
 Yes, thats right. 

> **shantiq said:**
> earlier on i ripped a track to flac-5 and to au the flac is 40Mb the au 156Mb are we saying the 2 files carry exactly the same info?

If all the data from the original source isnt there, its not lossless. ;) 

*edit- you havent been checking the  file size before you listen have you? That could explain why you think shorten (which is bigger than .flac) sounds better. 

> **cchhrriiss121212 said:**
> Is .au always 4 times the size of flac? Roughly thats about the same size as .wav, which might explain why flac has been more popular
I would say the difference you hear is the placebo affect, flac is lossless so there is no way that another lossless container will retain any extra information. Where do you think this extra info can come from?

I'm actually wondering how big the original file is. -5 flac normally compresses to a bit over 50% of the original file size.

I have seen that drop a little (I've got 1 -8 flac that is a bit under 1/3 of the original file size)  but I doubt that there would be many, if any -5 flac files that are 1/4 of the original file size.....

---

### Post by shantiq on 2010-07-12
well i tested au versus wav for size on hung up by Madonna and both come up at 56MB so no wonder the au sounds so good also tried this format ircam: SF (Berkeley/IRCAM/CARL)  and it too came to 56MB

now i try flac -0  and flac -8 from the wav and i get

43.1 MB for 0 and 41 MB for 8

i rip to shorten and i get 43.1 MB just like a flac -0


flac options are:


```
-0..-8, --compression-level-0..--compression-level-8
                 Fastest  compression..highest  compression  (default  is -5).
                 These are synonyms for other options:

                 -0, --compression-level-0
                           Synonymous with -l 0 -b 1152 -r 3

                 -1, --compression-level-1
                           Synonymous with -l 0 -b 1152 -M -r 3

                 -2, --compression-level-2
                           Synonymous with -l 0 -b 1152 -m -r 3

                 -3, --compression-level-3
                           Synonymous with -l 6 -b 4096 -r 4

                 -4, --compression-level-4
                           Synonymous with -l 8 -b 4096 -M -r 4

                 -5, --compression-level-5
                           Synonymous with -l 8 -b 4096 -m -r 5

                 -6, --compression-level-6
                           Synonymous with -l 8 -b 4096 -m -r 6

                 -7, --compression-level-7
                           Synonymous with -l 8 -b 4096 -m -e -r 6

                 -8, --compression-level-8
                           Synonymous with -l 12 -b 4096 -m -e -r 6

```


so shorten is not a bigger file than flac

and au is the same size as wav

i still find shorten clearer than flac at the same size and refute the placebo argument

as regards au it seems it is so lossless that in effect it is a wav with another extension   (ditto for ircam: SF (Berkeley/IRCAM/CARL)   all a little confusing;);)

also flac -0 is the fastest compression but also the biggest file
and flac -8 the smallest file but the slowest i guess that makes sense

anyway this is what i found

---

### Post by cascade9 on 2010-07-12
> **shantiq said:**
> so shorten is not a bigger file than flac

Typically, flac is smaller than shn. I havent seen shorten every compress as much as flac (which is part of why shroten is 'dead') 

> **shantiq said:**
> i still find shorten clearer than flac at the same size and refute the placebo argument

as regards au it seems it is so lossless that in effect it is a wav with another extension   (ditto for ircam: SF (Berkeley/IRCAM/CARL)   all a little confusing;);)

If its the same size as the .wav, then technically its not lossless. Lossless means 'lossless compression', not file renaming. 

If its not placebo, then its a decoder issue. Like I said above, lossless is lossless, and to be 'lossless' there cant be any difference between the original source file and the compressed then decompessed version. 

> **shantiq said:**
> well i tested au versus wav for size on hung up by Madonna and both come up at 56MB so no wonder the au sounds so good also tried this format ircam: SF (Berkeley/IRCAM/CARL) and it too came to 56MB 

Ahh, yes, so you are checking the filesize.

---

### Post by shantiq on 2010-07-12
when playing au file in deadbeef it shows 2822 kbps which is twice a wav at 1411 kbps so that would explain the high sound quality

---

### Post by cascade9 on 2010-07-12
> **shantiq said:**
> when playing au file in deadbeef it shows 2822 kbps which is twice a wav at 1411 kbps so that would explain the high sound quality

No, it doesnt. 

> **cchhrriiss121212 said:**
> Where do you think this extra info can come from?

If its ripped from CDDA, WAV (etc) then there is nowhere for the extra data to appear from. ;)

---

### Post by cchhrriiss121212 on 2010-07-12
> **cascade9 said:**
> 
If its ripped from CDDA, WAV (etc) then there is nowhere for the extra data to appear from. ;)
That was supposed to be my point.;) I need to work on my rhetorical questions.:D

---

### Post by cascade9 on 2010-07-13
> **cchhrriiss121212 said:**
> That was supposed to be my point.;) I need to work on my rhetorical questions.:D

You do? :biggrin:

It was such a good point I felt it was worth making twice.

---

### Post by Chronon on 2010-07-13
> **shantiq said:**
> well yes that is the science but listen hard and tell me

i have had this debate so many times


and i always come back to the ears not the science

if you hear no difference that is cool too

earlier on i ripped a track to flac-5 and to au the flac is 40Mb the au 156Mb are we saying the 2 files carry exactly the same info?

i hear differently

You are experiencing a placebo effect.  Any two lossless formats will decode to exactly the same PCM data.  The data being fed to the ADC will be identical in either case.

I bet you can't reliably ABX the difference.

Some lossless codecs are able to compress the same data to a smaller file size.  It still decodes to the same PCM.

---

### Post by shantiq on 2010-07-13
hi guys.no not from a cd. a piece of music i have created.

[CENTER][IMG]http://img37.imageshack.us/img37/3605/unknownartistnewvistasi.png[/IMG][/CENTER]

it is a piece of music i have written on rosegarden and saved to a midi file then converted to wav on audacity

i then saved it to au on audacity too and it shows 1411kbps for wav and 2822kbps for au as you can see on the picture

puzzling  ok it is not running it again through audacity it says 32-bit that is the answer it must have picked that as default setting hence the 2822.  of course the sound is ASTOUNDING on that sort of kbps

And  1411bbps is all that comes out of a cd

Wonder if there are ways to store higher kbps on fixed medium/?

Any of you know?

ps   this here is [the music]("http://shan.bandcamp.com/") i write all on ubuntu with rosegarden

---

### Post by cascade9 on 2010-07-13
Acording to the reading on the bottom of deadbeef, that is a 16bit/44.1KHz file...the same as you get on CDDA. 

I dont know if audacity is stuffing up, or deadbeef, but something has made a hash of things ;) 

> **shantiq said:**
> puzzling  ok it is not running it again through audacity it says 32-bit that is the answer it must have picked that as default setting hence the 2822.  of course the sound is ASTOUNDING on that sort of kbps

kbs =/= a measure of quality. 

Its not that hard to make a huge filesize from virtually any audio file (just rip to 24bi/96KHz or 24bit/192KHz  flac, or 32bitbit 96KHz wavpack). BTW, flac can sort of do 32bit (32-bit integer samples, but not 32-bit float) but according to the audio engineer I know (and forum posts I've seen here and there), anything past 24bit is pointless. 

By 'fixed medium' I guess you mean a CD/DVD. If you have a CD/DVD/media player that can handle flac at high resolutions, then that would work. I *think* there might be some players that will play high res .wavs, but I dont know that for sure. 

Apart from that, .dts would do it.....but there is no free .dts encoders.

*edit- if you dont have a single gun theory album, get one.

---

