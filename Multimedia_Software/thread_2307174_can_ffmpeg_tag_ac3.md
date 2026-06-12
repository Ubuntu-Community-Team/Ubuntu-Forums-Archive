---
title: "can ffmpeg tag ac3?"
date: 2015-12-22
forum: Multimedia Software
---

### Post by shantiq on 2015-12-22
**EDIT**: if you want the short answer ac3 takes APEV2 tags and no native way to do so although foobar will with this plugin [http://kode54.foobar2000.org/foo_ac3.fb2k-component](http://kode54.foobar2000.org/foo_ac3.fb2k-component)
The solution therefore is to place the ac3 inside an mka container which will accept id3 tagging
Thanx to  FakeOutdoorsman for suggestion.

```
ffmpeg -i "input.ac3" \
    -metadata title="your title" \
    -metadata artist="your artist" \
    -metadata author="your author" \
    -metadata composer="your composer" \
    -metadata album="your album" \
    -metadata year="your year" \
    -metadata track="01" \
    -metadata comment="your comment" \
    -metadata genre="your genre" \
    -c:a copy  output.mka
```

========================================
========================================

Original post >>>


so far failed miserably with ```
*ffmpeg *-i in.ac3 -*metadata* title="my title" out.ac3
```
is there a way which works? ffmpeg or else

edit:ha ok this way is for id3 tags and APEV2 is what is needed for ac3 it seems  ...    so how can we write APEV2 tags onto an ac3 file in Ubuntu if possible


had so far to resort to foobar [plugin]("http://kode54.foobar2000.org/foo_ac3.fb2k-component") under Wine



thanx
shan

---

### Post by FakeOutdoorsman on 2015-12-23
Can you provide a sample AC3 file that properly shows metadata in your player and/or ffmpeg?

I'm not sure if such metadata are supported. I lazily looked in [&#8203;Digital Audio Compression Standard (Document A/52:2012)]("http://atsc.org/wp-content/uploads/2015/03/A52-201212-17.pdf") and [Dolby Metadata Guide]("http://www.dolby.com/us/en/technologies/a-guide-to-dolby-metadata.pdf"), but neither mentioned "user" metadata.

The AC3 muxer had no private options: ffmpeg -h muxer=ac3

I don't know. You could always throw it in mka container.

---

### Post by shantiq on 2015-12-23
Hi Fake. Thanx for reply.

here is what it looks like in Cantata [MPD]. I added the APEV2 tags here using the foobar mentioned above. See yellow box at bottom
[ATTACH=CONFIG]266332[/ATTACH]so it can be tagged it seems but with APEV2 .... 
also in foobar 
[ATTACH=CONFIG]266333[/ATTACH]

i do not see a Linux way of getting there and funnily enough Mediainfo does not show the tags


```
General
Complete name                            : WDR HD_Can - live in Soest, Winter 1970.ac3
Format                                   : AC-3
Format/Info                              : Audio Coding 3
File size                                : 271 MiB
Duration                                 : 1h 24mn
Overall bit rate mode                    : Constant
Overall bit rate                         : 448 Kbps

Audio
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Format settings, Endianness              : Big
Duration                                 : 1h 24mn
Bit rate mode                            : Constant
Bit rate                                 : 448 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 271 MiB (100%)


```


**BUT**  and thank you the mka route is ace !

[ATTACH=CONFIG]266334[/ATTACH]

```

ffmpeg -i "WDR HD_Can - live in Soest, Winter 1970.ac3" \
    -metadata title="Live in Soest" \
    -metadata artist="Can" \
    -metadata author="Can" \
    -metadata composer="Can" \
    -metadata album="Can - Live in Soest" \
    -metadata year="1970" \
    -metadata track="01" \
    -metadata comment="From WDR Rockpalast" \
    -metadata genre="Krautrock" \
    -c:a copy  WDR.mka
```


giving a happy mediainfo:

```
General
Unique ID                                : 213672252964841084268367052843552729263 (0xA0BFC76E4FB2BB57DE9AF4C4A3F1E8AF)
Complete name                            : WDR.mka
Format                                   : Matroska
Format version                           : Version 4 / Version 2
File size                                : 272 MiB
Duration                                 : 1h 24mn
Overall bit rate mode                    : Constant
Overall bit rate                         : 450 Kbps
Track name                               : Live in Soest
Writing application                      : Lavf57.19.100
Writing library                          : Lavf57.19.100
ARTIST                                   : Can
AUTHOR                                   : Can
COMPOSER                                 : Can
ALBUM                                    : Can - Live in Soest
YEAR                                     : 1970
PART_NUMBER                              : 01
COMMENT                                  : From WDR Rockpalast
GENRE                                    : Krautrock

Audio
ID                                       : 1
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Format settings, Endianness              : Big
Codec ID                                 : A_AC3
Duration                                 : 1h 24mn
Bit rate mode                            : Constant
Bit rate                                 : 448 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 271 MiB (100%)
Default                                  : Yes
Forced                                   : No
DURATION                                 : 01:24:26.400000000


```

---

### Post by andrew.46 on 2015-12-24
I was looking for a method of accomplishing this with mkvmerge but it seems to only accept tags from an xml file, no idea why this should be so. This with the latest version:

```

andrew@ilium~$ **[COLOR="#FF0000"]mkvmerge --version[/COLOR]**
mkvmerge v8.6.1 ('Flying') 64bit
andrew@ilium~$ 

```

Unless I am missing something here?

---

### Post by andrew.46 on 2015-12-24
You *can* use mkvmerge as I have found but it is a little clunky. If you use the file luckynight.wav:

```

wget samples.mplayerhq.hu/A-codecs/lossless/luckynight.wav.bz2 && \
bzip2 -dkv luckynight.wav.bz2

```

then create the ac3 file:

```
ffmpeg -i luckynight.wav luckynight.ac3
```

and create the following xml file as luckynight.xml:

```

<?xml version="1.0" encoding="ISO-8859-1"?>

<!DOCTYPE Tags SYSTEM "matroskatags.dtd">

<Tags>
  <Tag>
    <Targets>
     <TrackUID>1</TrackUID>
   </Targets>

    <Simple>
      <Name>Album</Name>
      <String>Treasure Quest Soundtrack</String>
    </Simple>
    <Simple>
      <Name>Artist</Name>
      <String>Jody Marie Gnant</String>
     </Simple>
      <Simple>
        <Name>Title</Name>
        <String>Lucky Night</String>
      </Simple>
      <Simple>
        <Name>Genre</Name>
        <String>Soundtrack</String>
      </Simple>
      <Simple>
        <Name>Date</Name>
        <String>1995</String>
      </Simple>

  </Tag>
</Tags>

```

(You probably don't need to specify 'target' when the tags are applied to the whole file in this way, target actually allows multiple tracks.) Then you can then join it all together with:

```

mkvmerge -o luckynight.mka --tags 0:luckynight.xml luckynight.ac3

```

 Interesting anyway if not substantially more cumbersome than FFmpeg's simple commandline....

---

### Post by shantiq on 2015-12-24
Thanx Andrew for the research/experimentation that is some Tour De Force!    but yes the other route through mka is a tad easier :] 

Seasonal Greetings to yourself and all others on the forums


[[IMG]http://s2.postimg.org/9dgoatbhh/Krishmas2.jpg[/IMG]]("http://postimg.org/image/9dgoatbhh/")

---

### Post by andrew.46 on 2015-12-24
> **shantiq said:**
> Thanx Andrew for the research/experimentation that is some Tour De Force!    but yes the other route through mka is a tad easier :] 

Mind you once you set up a few templates it would not be so bad and xml is pretty easy if you are used to raw html.

> Seasonal Greetings to yourself and all others on the forums

And to yourself and family!

---

### Post by andrew.46 on 2015-12-31
> **FakeOutdoorsman said:**
> I don't know. You could always throw it in mka container.

Courtesy of this throwaway line I have given abcde support for encoding to the mka container using FFmpeg. Not such a big deal and perhaps nobody but myself will use it, once the documentation is fixed I will push to git :). FFmpeg is not huge on audio but this allows placement in mka directly from audio cd of the following on my system:

```

A..... aac                  AAC (Advanced Audio Coding)
 A..... libfaac              libfaac AAC (Advanced Audio Coding) (codec aac)
 A..... libfdk_aac           Fraunhofer FDK AAC (codec aac)
 A..... ac3                  ATSC A/52A (AC-3)
 A..... ac3_fixed            ATSC A/52A (AC-3) (codec ac3)
 A..... adpcm_adx            SEGA CRI ADX ADPCM
 A..... g722                 G.722 ADPCM (codec adpcm_g722)
 A..... g726                 G.726 ADPCM (codec adpcm_g726)
 A..... adpcm_ima_qt         ADPCM IMA QuickTime
 A..... adpcm_ima_wav        ADPCM IMA WAV
 A..... adpcm_ms             ADPCM Microsoft
 A..... adpcm_swf            ADPCM Shockwave Flash
 A..... adpcm_yamaha         ADPCM Yamaha
 A..... alac                 ALAC (Apple Lossless Audio Codec)
 A..... libopencore_amrnb    OpenCORE AMR-NB (Adaptive Multi-Rate Narrow-Band) (codec amr_nb)
 A..... comfortnoise         RFC 3389 comfort noise generator
 A..X.. dca                  DCA (DTS Coherent Acoustics) (codec dts)
 A..... eac3                 ATSC A/52 E-AC-3
 A..... flac                 FLAC (Free Lossless Audio Codec)
 A..... g723_1               G.723.1
 A..... mp2                  MP2 (MPEG audio layer 2)
 A..... mp2fixed             MP2 fixed point (MPEG audio layer 2) (codec mp2)
 A..... libmp3lame           libmp3lame MP3 (MPEG audio layer 3) (codec mp3)
 A..... nellymoser           Nellymoser Asao
 A..... libopus              libopus Opus (codec opus)
 A..... pcm_alaw             PCM A-law / G.711 A-law
 A..... pcm_f32be            PCM 32-bit floating point big-endian
 A..... pcm_f32le            PCM 32-bit floating point little-endian
 A..... pcm_f64be            PCM 64-bit floating point big-endian
 A..... pcm_f64le            PCM 64-bit floating point little-endian
 A..... pcm_mulaw            PCM mu-law / G.711 mu-law
 A..... pcm_s16be            PCM signed 16-bit big-endian
 A..... pcm_s16be_planar     PCM signed 16-bit big-endian planar
 A..... pcm_s16le            PCM signed 16-bit little-endian
 A..... pcm_s16le_planar     PCM signed 16-bit little-endian planar
 A..... pcm_s24be            PCM signed 24-bit big-endian
 A..... pcm_s24daud          PCM D-Cinema audio signed 24-bit
 A..... pcm_s24le            PCM signed 24-bit little-endian
 A..... pcm_s24le_planar     PCM signed 24-bit little-endian planar
 A..... pcm_s32be            PCM signed 32-bit big-endian
 A..... pcm_s32le            PCM signed 32-bit little-endian
 A..... pcm_s32le_planar     PCM signed 32-bit little-endian planar
 A..... pcm_s8               PCM signed 8-bit
 A..... pcm_s8_planar        PCM signed 8-bit planar
 A..... pcm_u16be            PCM unsigned 16-bit big-endian
 A..... pcm_u16le            PCM unsigned 16-bit little-endian
 A..... pcm_u24be            PCM unsigned 24-bit big-endian
 A..... pcm_u24le            PCM unsigned 24-bit little-endian
 A..... pcm_u32be            PCM unsigned 32-bit big-endian
 A..... pcm_u32le            PCM unsigned 32-bit little-endian
 A..... pcm_u8               PCM unsigned 8-bit
 A..... real_144             RealAudio 1.0 (14.4K) (codec ra_144)
 A..... roq_dpcm             id RoQ DPCM
 A..X.. s302m                SMPTE 302M
 A..X.. sonic                Sonic
 A..X.. sonicls              Sonic lossless
 A..... tta                  TTA (True Audio)
 A..X.. vorbis               Vorbis
 A..... libvorbis            libvorbis (codec vorbis)
 A..... wavpack              WavPack
 A..... wmav1                Windows Media Audio 1
 A..... wmav2                Windows Media Audio 2

```

and I guess makes abcde one of the few to cater for mka :). Pushed to git in the next day or so...

**Edit:** Mind you not all of these would fit in mka, certainly: Vorbis, MP2, MP3, LC-AAC, HE-AAC, WMAv1, WMAv2, AC3, eAC3, Opus....

---

### Post by FakeOutdoorsman on 2015-12-31
Glad to see work on abcde continuing. I don't use MKA much myself, except when testing, but the [Matroska FAQ](http://www.matroska.org/technical/guides/faq/index.html) has some interesting points:
> [B]
Q: What is the advantage of using the .mka file instead of the original audio formats, like mp2, mp3 etc?[/B]
A: You can embed lyrics or transcriptions (e.g. from srt subtitles) in the audio file. You can use chapters to separate parts of a track or a live album. In some case (MP3, AC3, DTS) the Matroska file may also be smaller than the original with much better/cleaner seeking support.
[B]
Here are some reasons that placing audio in MKA is useful:[/B]
1. The tags will be the same no matter what audio format you use. That means that if you write a program to read back tags, it only has to read them from one type of tagging system, no matter what type of audio is being used.
2. All tracks to a CD can be in a single file. You have the option of dividing the tracks into seperate Tracks, or seperate Chapters. You could make your own compilation in a single file, even using different audio formats, such as MP3 and Vorbis.
3. If you write a program to read audio of of MKA, then you don't need to understand how the framing works in the different formats because it is already done for you in Matroska.
4. It is easy to delete portions of the audio without reencoding because you just throw away those blocks. You don't even have to be able to play that format back, you could edit by just knowing timecodes.
5. Detecting differences between two audio streams would be easy because you could store both in a single file, start playback, and then just switch between tracks.
6. If you intend to combine the audio with video, then having is in MKA means you can merge it with an MKV, even if the application doesn't support the audio type.
7. In the case of MP3, MP2 AC3 and even some AAC, using "compressed headers" the MKA file may even be smaller than the original "raw" file, without losing any bit of information.

---

### Post by andrew.46 on 2015-12-31
> **FakeOutdoorsman said:**
> Glad to see work on abcde continuing.

I will continue for a while longer I think, the learning curve continues :). Pity the audio cd is slowly fading away....

---

### Post by shantiq on 2016-01-01
> Pity the audio cd is slowly fading away....

no worries there will be other things to play with no doubt :]

---

### Post by FakeOutdoorsman on 2016-01-01
I forgot to ask: why use AC3?

---

### Post by Yellow Pasque on 2016-01-01
> **FakeOutdoorsman said:**
> I forgot to ask: why use AC3?

Maybe it's because you have a concert/music DVD and that's all that's on the DVD. Unless you're willing to do a lossy->lossy conversion and lose audio quality (or a lossy->lossless conversion and lose disk space), then it makes sense to keep the AC3. I've been lucky and gotten uncompressed PCM on the music DVD's I own.

---

### Post by shantiq on 2016-01-02
yes T to answer Fake's question; basically my OP was because i had extracted ac3 as is from a Music Video and wanted to retain 5.1 **and** add tagging ... as regards ripping a cd to ac3; one might want to do that to add to a self-created video mayhaps ...

---

