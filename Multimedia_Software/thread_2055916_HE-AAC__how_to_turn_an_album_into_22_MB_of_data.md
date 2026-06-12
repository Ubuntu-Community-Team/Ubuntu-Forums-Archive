---
title: "HE-AAC : how to turn an album into 22 MB of data"
date: 2012-09-10
forum: Multimedia Software
---

### Post by shantiq on 2012-09-10
What if there were an audio format which made very small files and yet had great sound quality; with which you could send an album zipped to a friend as one email of an average size of 22 MB ..


Well there is and it is named [**HE-AAC**]("http://en.wikipedia.org/wiki/HE-AAC") and made by Fraunhofer  [the files play in all players i have tried so far with no extras needed]


> 
 
 
 Over the last couple of years, HE-AAC became one of the most important enabling technologies for state-of-the-art multimedia systems. The codec combines high audio quality with very low bit-rates, allowing for an impressive audio experience even over channels with limited capacity, such as those in broadcasting or mobile multimedia streaming.

Fraunhofer IIS offers fast access to high-quality, product-ready HE-AAC implementations. Optimized encoder and decoder real- time implementations on embedded processors or DSPs are available, as well as software implementations on PC platforms.

HE-AAC is&#8230;

- ... the most efficient high-quality multi-channel and stereo audio codec.
- ... is used in TV, radio, and streaming worldwide.
- ... the perfect codec for adaptive streaming, for example Apple HLS or MPEG DASH.
- ... in more than 5 billion devices already today.
- ... fully compatible with all relevant broadcast metadata.
- ... is supported and maintained by Fraunhofer IIS.Quality	excellent, according to EBU test (for complete results see whitepaper below)
Bitrate	HE-AAC: 48 to 64 kbit/s Stereo, 160 kbit/s for 5.1 Surround (HE-AAC: AAC-LC + SBR) 
 HE-AAC v2: 24 to 32 kbit/s Stereo (HE-AACv2: AAC-LC + SBR +PS) 
 for good quality audio
Sampling rates	24 to 96 kHz
Channels	mono, stereo, multi-channel (e.g. 5.1, 7.1, ...)
Used in	DVB, ISDB , SBTVD, DAB+, DRM+, DRM, ATSC-M/H, ISDB-Tmm, DVB-H, DMB, 3GPP, XM Radio, mobile phones, audio and video streaming services



**examples: converting in ffmpeg and mediainfo**

> 
ffmpeg -i Age.wav -acodec libaacplus  -ab 72k Age.aac
ffmpeg version N-35917-ge4fe4d0 Copyright (c) 2000-2012 the FFmpeg developers
  built on Sep 10 2012 11:04:03 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3 --enable-libaacplus
  libavutil      51. 72.100 / 51. 72.100
  libavcodec     54. 55.100 / 54. 55.100
  libavformat    54. 25.105 / 54. 25.105
  libavdevice    54.  2.100 / 54.  2.100
  libavfilter     3. 16.101 /  3. 16.101
  libswscale      2.  1.101 /  2.  1.101
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
[wav @ 0x1c28260] max_analyze_duration 5000000 reached at 5015510
Guessed Channel Layout for  Input Stream #0.0 : stereo
Input #0, wav, from 'Age.wav':
  Duration: 00:02:42.66, bitrate: 1411 kb/s
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 44100 Hz, stereo, s16, 1411 kb/s
File 'Age.aac' already exists. Overwrite ? [y/N] y
Output #0, adts, to 'Age.aac':
  Metadata:
    encoder         : Lavf54.25.105
    Stream #0:0: Audio: aac, 44100 Hz, stereo, s16, 72 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le -> libaacplus)
Press [q] to stop, [?] for help
size=    1454kB time=00:02:42.67 bitrate=  73.2kbits/s    
video:0kB audio:1454kB subtitle:0 global headers:0kB muxing overhead 0.000000%



000000000000000000:~/Desktop/Taller$ mediainfo  Age.aac
General
Complete name                            : Age.aac
Format                                   : ADTS
Format/Info                              : Audio Data Transport Stream
File size                                : 1.42 MiB

Audio
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format version                           : Version 2
Format profile                           : HE-AAC / LC
Bit rate mode                            : Constant / Variable
Bit rate                                 : 71.6 Kbps
Minimum bit rate                         : 140 Kbps
Maximum bit rate                         : 228 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 1.42 MiB (100%)



**TO INSTALL**


2 ROUTES I am aware of...   there might be others



**Through aacplusenc** 

[http://www.ubuntuupdates.org/package/medibuntu_free/natty/free/base/aacplusenc](http://www.ubuntuupdates.org/package/medibuntu_free/natty/free/base/aacplusenc)

download the deb on the page then install    and run  aacplusenc -h in terminal   you will see this

> Usage:   aacplusenc <wav_file> <bitstream_file> <bitrate> <(m)ono/(s)tereo>

Example: aacplusenc input.wav out.aac 24000 s

it goes up to 72000  ;   64000 the most likely setting


**Through libaacplus [ffmpeg]**   all info for this one is credited to Ron999 who passed it to me.


And to compile FFmpeg with it ...
 Just add --enable-libaacplus to the ./configure line.
 
 
 This can be done through FakeOutDoorsman's guide [**here **]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide") 
 

 But first it is necessary to compile and install libaacplus.

 This is the method that I used...
 (Paste the one single command)

```

cd ~/ && \
wget http://217.20.164.161/~tipok/aacplus/libaacplus-2.0.2.tar.gz && \
tar -xf libaacplus-2.0.2.tar.gz && \
cd libaacplus-2.0.2 && \
./autogen.sh --enable-shared && \
make && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname libaacplus \
--pkgversion 2.0.2 \
--backup=no --default --deldoc=yes --fstrans=no && sudo ldconfig
```


====================================

**RIPPING TO HE-AAC**


Rubbyripper is perfectly happy to handle this format with this line in the "other" . The line below also works in Deadbeef with the converter [right-click on a song/convert/click on pencil/add/enter libaacplus and code] 


```
ffmpeg -i %i -c:a libaacplus -b:a 64k %o.m4a && AtomicParsley %o.m4a -a %a -b %b -g %g -y %y -k %n --title %t -W
```

You will need AtomicParsley installed for tagging   ```
sudo apt-get install atomicparsley
```


you can also rip with aacplusenc but so far I have failed to tag that way.   


**RR code** is

```
aacplusenc "%i"  "%o" .aac 64000 s
```

```
aacplusenc "%i"  "%o" .aac 72000 s
```



There you go ; most of the info I am aware of as of now....   It really gives a good sound album at around 22MB............

---

### Post by shantiq on 2012-10-05
you can also rip with Rubyripper with neroAacEnc [WILL NEED [**neroAacEnc and neroAacTag**]("http://www.nero.com/enu/downloads-nerodigital-nero-aac-codec.php")]


> neroAacEnc  -br 36000 -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t

will give you 

> Format profile : [COLOR="DarkRed"]HE-AACv2[/COLOR] / HE-AAC / LC


if you push over -br 40000  Format profile   :[COLOR="DarkRed"]HE-AAC[/COLOR] / LC

if you push higher than 72000  you will get  [COLOR="DarkRed"]AAC / LC[/COLOR]

> High-Efficiency Advanced Audio Coding (HE-AAC) is a lossy data compression scheme for digital audio defined as a MPEG-4 Audio profile in ISO/IEC 14496-3. It is an extension of Low Complexity AAC (AAC LC) optimized for low-bitrate applications such as streaming audio. HE-AAC version 1 profile (HE-AAC v1) uses spectral band replication (SBR) to enhance the compression efficiency in the frequency domain. HE-AAC version 2 profile (HE-AAC v2) couples SBR with Parametric Stereo (PS) to enhance the compression efficiency of stereo signals. It is a standardized and improved version of the AACplus codec.


================================================

if you want a simple solution and you can handle basic german [it is only in German]

[**Plattenkiste**]("http://www.dieplattenkiste.de/downloads/Plattenkiste255_2_PHBW.exe") is the software for you under Wine

it will rip very well to HE-AAC


see image for guidance


[ATTACH]225122[/ATTACH]


[B]i cannot stress enough the great sound quality for the small size --   using 36k the sound is still excellent
Audacious with the crystallizer effect is a good way to get excellent rendition[/B]

---

### Post by andrew.46 on 2012-12-09
You can add abcde to the list now, neroAacEnc has entered the development version:

[http://code.google.com/p/abcde/source/list](http://code.google.com/p/abcde/source/list)

I am not terribly familiar with the syntax to produce HE-AAC files but a little experimentation produced the following:

```

$ **[COLOR="Red"]mediainfo 01.Breathe.m4a [/COLOR]**
General
Complete name                            : 01.Breathe.m4a
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42
File size                                : 923 KiB
Duration                                 : 4mn 0s
Overall bit rate mode                    : Variable
Overall bit rate                         : 31.4 Kbps
Album                                    : The Dark Side Of The Moon- 20th Anniversary Edition
Track name                               : Breathe
Track name/Position                      : 1
Performer                                : Pink Floyd
Genre                                    : Psychedelic Rock
Recorded date                            : 1992
Encoded date                             : UTC 2012-12-09 07:13:55
Tagged date                              : UTC 2012-12-09 07:14:01

Audio
ID                                       : 1
[B][COLOR="Red"]Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : HE-AAC / LC[/COLOR][/B]
Codec ID                                 : 40
Duration                                 : 4mn 0s
Source duration                          : 4mn 0s
Bit rate mode                            : Variable
Bit rate                                 : 30.6 Kbps
Maximum bit rate                         : 35.4 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 899 KiB (97%)
Source stream size                       : 899 KiB (97%)
Writing library                          : Nero AAC codec 1.5.4.0
Encoding settings                        : -2pass -br 32000 -he
Encoded date                             : UTC 2012-12-09 07:13:55
Tagged date                              : UTC 2012-12-09 07:14:01

Menu

```

But I have no idea what settings I should really be using for this :). I have a dim memory of it being considered a 'bad thing' to specify -he on the commandline....

---

### Post by shantiq on 2012-12-09
thanx Andrew to my mind the best audio codec ever; happy to see one more piece of kit[this time Linux] handling it


as regards the option this is what you get from  ```
neroAacEnc -help
```





> Advanced features / troubleshooting:
-lc           : Forces use of LC AAC profile (HE features disabled).
-he           : Forces use of HE AAC profile (HEv2 features disabled).
-hev2         : Forces use of HEv2 AAC profile
                Note that the above switches (-lc, -he, -hev2) [B]should not be
                used[/B]; **optimal AAC profile is automatically determined **from
                quality/bitrate settings when no override is specified.


So no use specifying
Kbps will take it where it needs be


i found 38k gives you excellent quality due to >  HE-AAC version 2 profile (HE-AAC v2) couples SBR with Parametric Stereo (PS) to enhance the compression efficiency of stereo signals. It is a standardized and improved version of the AACplus codec   **HEv2 kicks in below 40k**



so with neroAacTag

> neroAacEnc  -br 38000 -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t


the sound is so good i have tested myself against flac and found it winning
This must be the reason > Parametric Stereo (PS) to enhance the compression efficiency of stereo signals


Plattenkiste under Wine is wonderful too with full tagging out of the box... easy to use although always in German  [but most people can work it out no doubt]
Thanx to you now we have a Linux option simpler than RR [Rubyripper]




**PS**   ok tried to use it but not finding my way yet   used [**guide**]("http://www.andrews-corner.org/abcde.html#aac")

tried this for .abcde.conf   first 4 lines  

> # Specify the encoder to use for m4a/aac. In this case
# faac is the only choice.
AACENCODERSYNTAX=neroAacEnc

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/faac
AACENC=/usr/bin/neroAacEnc

# Specify your required encoding options here. Multiple options can
AACENCOPTS='-br 38000 -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t'

# Output type for m4a/aac.
OUTPUTTYPE="m4a"


maybe it is not ready yet ?   not sure....   will await instructions  ::]]

---

### Post by andrew.46 on 2012-12-09
> **shantiq said:**
> maybe it is not ready yet ?   not sure....   will await instructions  ::]]

The changes are in the svn version at the moment, not the release version :). I am using the following ~/.abcde.conf with the svn abcde:


```

# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#   m4a/aac using abcde version v2.5.5-UNRELEASED
# 
# -------------------------------------------------- #


# Specify the encoder to use for m4a/aac. In this case
# we are using the closed source neroAacEnc.
**[COLOR="Red"]AACENCODERSYNTAX=neroAacEnc[/COLOR]**

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/faac
**[COLOR="Red"]AACENC=neroAacEnc[/COLOR]**

# Specify your required encoding options here. Multiple options can
# be selected as '--best --another-option' etc.
**[COLOR="Red"]AACENCOPTS='-q 0.65'[/COLOR]**

# Output type for m4a/aac.
**[COLOR="Red"]OUTPUTTYPE="m4a"[/COLOR]**

# Use AtomicParsley for tagging.
**[COLOR="Red"]ATOMICPARSLEY='AtomicParsley'[/COLOR]**

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music/"               

# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean
              
# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```

You don't add all the tagging information in, AtomicParsley will do all of that for you.

---

### Post by shantiq on 2012-12-10
thanx so please is it available and how to install/start it

slightly confused about the svn how to download install:]

---

### Post by andrew.46 on 2012-12-10
Well, it is pre-release at the moment but can definitely be sampled. You will need a subversion client:

```
sudo apt-get install subversion
```

and then you can download a copy:

```

mkdir $HOME/abcde_build && cd $HOME/abcde_build && \
svn checkout http://abcde.googlecode.com/svn/trunk/ abcde-read-only && \
cd abcde-read-only && \
./abcde

```

This will startup the svn abcde without actually installing it and this version of the script allows aac encoding with neroAacEnc. You will need cd-discid installed as well as AtomicParsley.

Next week or so there will be support for the new opus codec added so you might want to have another look then as well :). Hopefully 2.55 will be released at some stage after this and then full installation will be the go...

---

### Post by shantiq on 2012-12-10
thanx for clarifications:KS

---

### Post by andrew.46 on 2012-12-10
> **shantiq said:**
> thanx for clarifications:KS

No problems :). When 2,55 comes out I should post details somewhere on these Forums the method to produce a formal debian package from the release source. Some good stuff coming up, not just neroAacEnc and opus but also Musepack support has moved to SV8. Very exciting times for abcde!

And I will look to you for the best settings for neroAacEnc with abcde :).

---

### Post by shantiq on 2012-12-10
ok tried it now and works very well


once having installed normal abcde [so to get cddb-tool] and installed 
> mkdir $HOME/abcde_build && cd $HOME/abcde_build && \
svn checkout [http://abcde.googlecode.com/svn/trunk/](http://abcde.googlecode.com/svn/trunk/) abcde-read-only && \
cd abcde-read-only && \
./abcde

starting it

> cd abcde_build/abcde-read-only && ./abcde


in the .abcde.conf

i have this line

> AACENCOPTS='-br 38000 -ignorelength  '



which then gives me the prized HE-AACv2


> ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : **[COLOR="DarkRed"]HE-AACv2 [/COLOR]**/ HE-AAC / LC
Codec ID                                 : 40
Duration                                 : 8mn 46s
Bit rate mode                            : Variable
Bit rate                                 : 38.0 Kbps
Maximum bit rate                         : 46.2 Kbps
Channel(s)                               : 2 channels / 1 channel / 1 channel
Channel positions                        : Front: L R / Front: C / Front: C
Sampling rate                            : 44.1 KHz / 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 2.39 MiB (98%)
Writing library                          : Nero AAC codec 1.5.4.0
Encoding settings                        : -br 38000
Encoded date                             : UTC 2012-12-10 14:26:01
Tagged date                              : UTC 2012-12-10 14:26:39


---

### Post by andrew.46 on 2012-12-11
> **shantiq said:**
> [...] which then gives me the prized HE-AACv2

Great news :).

---

### Post by andrew.46 on 2012-12-15
Opus encoding has just been added if you want to *svn up* and try it out...

---

### Post by Yellow Pasque on 2012-12-15
I can't put my finger on it, but there's something about AAC I don't like (in terms of audio quality). I prefer OGG/Mp3 for lossy and FLAC for lossless. Good info, nonetheless.

---

### Post by andrew.46 on 2012-12-15
I ahve to admit as well that despite many, many experiments I almost always use oggenc with -q 6 ...

---

### Post by shantiq on 2012-12-15
it's all about the ear and what we pick up/prefer [sort of like your "sonic taste"]  i do not like aac but i adore  neroAacEnc especially in the low bitrates with  HE-AACv2 .... totally different   

ogg is cool too  and mp3 if 320  but for lossy  nero wins by a landslide for me:KS        and still shorten for lossless


==============


Andrew can you please explain in simple steps [for a dummy like me:KS] what

> Opus encoding has just been added if you want to svn up and try it out...


entails....

---

### Post by andrew.46 on 2012-12-15
> **shantiq said:**
> Andrew can you please explain in simple steps [for a dummy like me

The non-installation method again, using the existing svn download:

```

cd $HOME/abcde_build/abcde-read-only && \
svn up && \
./abcde

```

You will need the opus-tools package which is available in Quantal repository but not in Precise where you will have to build your own.

---

### Post by shantiq on 2012-12-16
corking


so on Precise you need all this


> [http://downloads.xiph.org/releases/ogg/libogg-1.3.0.tar.gz](http://downloads.xiph.org/releases/ogg/libogg-1.3.0.tar.gz)
[http://downloads.xiph.org/releases/opus/opus-1.0.2.tar.gz](http://downloads.xiph.org/releases/opus/opus-1.0.2.tar.gz)
[http://downloads.xiph.org/releases/opus/opus-tools-0.1.6.tar.gz](http://downloads.xiph.org/releases/opus/opus-tools-0.1.6.tar.gz)







Nice work!

> cd $HOME/abcde_build/abcde-read-only && svn up && ./abcde 
At revision 374.
Using AtomicParsley To Tag AAC Tracks.
Executing customizable pre-read function... done.
Getting CD track info... Querying the CD for audio tracks...
Grabbing entire CD - tracks: 01 02 
Checking CDDB server status...
Querying the CDDB server...
Obtaining CDDB results...
Retrieving 1 CDDB match...done.
---- Louis Armstrong / Swing, You Cats ----
1: Mahogany Hall Stomp
2: Swing You Cats
3: Honey, Don't You Love Me Anymore?
4: Mississippi Basin
5: Laughin' Louis
6: Tomorrow Night
7: Dusky Stevedore
8: There's A Cabin In The Pines
9: Mighty River
10: Sweet Sue, Just You
11: I Wonder Who
12: St. Louis Blues
13: Don't Play Me Cheap
14: I'm In The Mood For Love
15: You Are My Lucky Star
16: La Curaracha
17: Got A Bran' New Suit
18: I've Got My Fingers Crossed
19: Old Man Mose
20: I'm Shooting High

Edit selected CDDB data? [y/n] (n): n
Is the CD multi-artist [y/N]? n
Creating playlist...
Grabbing track 01: Mahogany Hall Stomp...
cdparanoia III release 10.2 (September 11, 2008)

Ripping from sector       0 (track  1 [0:00.00])
	  to sector   11825 (track  1 [2:37.50])

outputting to /home/shantiq/abcde_build/abcde-read-only/abcde.320dc214/track01.wav

 (== PROGRESS == [                              | 011825 00 ] == :^D * ==)   

Done..................................


Grabbing track 02: Swing You Cats...
cdparanoia III release 10.2 (September 11, 2008)

Encoding track 01 of 20: Mahogany Hall Stomp...
Ripping from sector   11826 (track  2 [0:00.00])
	  to sector   23821 (track  2 [2:39.70])

outputting to /home/shantiq/abcde_build/abcde-read-only/abcde.320dc214/track02.wav

 (== PROGRESS == [          >                   | 015323 00 ] == :-) o ==)   Tagging track 01 of 20: Mahogany Hall Stomp...
 (== PROGRESS == [                              | 023821 00 ] == :^D * ==)   

Done.



Finished.
shantiq@shantiq-00000000000000000000000:~/abcde_build/abcde-read-only$ 


---

### Post by andrew.46 on 2012-12-16
Do you need to compile libogg as well? I confess I only have quantal vms at the moment so I cannot test this out :(

---

### Post by shantiq on 2012-12-16
yes libogg 1.3 or opus does not install

---

### Post by Merrattic on 2012-12-16
Shantiq, can you do a recap of what is needed for the basics on this, e.g. what to install, what to compile to get HE-AAC working? Don't think I need all the bells and whistles you and Andrew46 have moved onto.....;)

---

### Post by FakeOutdoorsman on 2012-12-16
> **andrew.46 said:**
> I ahve to admit as well that despite many, many experiments I almost always use oggenc with -q 6 ...

That's basically (with aoTuV) also what I've been using for years; although I don't often get a chance to listen to anything above a whisper unless I want to use headphones...which I don't since I use them all day at noisy work.

HE-AAC seems great for lower bitrates, but I'd stick with LC-AAC for anything, subjectively, <64k (stereo), since it will "preserve" more information (hence the reason many of the HE/LC encoders choose LC above certain bitrates). Also, choose LC-AAC if you want to maximise decoder compatibility.

Update: I forgot to ask--has anyone compared libaacplus, neroAacEnc, and fdk-aac? I believe all of these can output HE-AAC(v2), but I'm not totally sure.

---

### Post by shantiq on 2012-12-16
ok Merrattic if you need/want to   rip to HE-AAC

the absolute fastest is to use


if you want a simple solution and you can handle basic german [it is only in German]

[**Plattenkiste**]("http://www.dieplattenkiste.de/downloads/Plattenkiste255_2_PHBW.exe") is the software for you under Wine

 it will rip very well to HE-AAC


 see image for guidance

click on CDRippen button [on first window]
click on Alle Markieren
click on freeDB and accept to get your tags  [Werte in Tag Editor...]
Start
 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225122&d=1349471049[/IMG]

[B]
================================================[/B]


if on the other hand you want a Linux solution   here are the basics:


First get [**NeroAac**]("http://www.nero.com/enu/downloads-nerodigital-nero-aac-codec.php")


place all Linux 3 codecs in /usr/bin and make executable


then run ```
neroAacEnc -help
``` and find most of the info

you can now bulk [or single]convert from wav with this line


> for f in *.wav ; do neroAacEnc -br 38000 -ignorelength -if "$f" -of "${f%.wav}.m4a" ;done


change kbps to your needs i like 38000 as below 40k you get HE-AACv2 which has better sound

**Tag with easytag or puddletag for this route**


**=========================================**



if you want **rubyripper** or **deadbeef** read posts   1 and 2 of this thread


**=========================================**


if you want **abcde** at this stage it is involved but here goes


> sudo apt-get install subversion  abcde

> 
mkdir $HOME/abcde_build && cd $HOME/abcde_build && \
 svn checkout [http://abcde.googlecode.com/svn/trunk/](http://abcde.googlecode.com/svn/trunk/) abcde-read-only && \
 cd abcde-read-only && \
 ./abcde
 
 
 on precise you need this  [but not on quantal]
 



> [http://downloads.xiph.org/releases/ogg/libogg-1.3.0.tar.gz](http://downloads.xiph.org/releases/ogg/libogg-1.3.0.tar.gz)
[http://downloads.xiph.org/releases/opus/opus-1.0.2.tar.gz](http://downloads.xiph.org/releases/opus/opus-1.0.2.tar.gz)
[http://downloads.xiph.org/releases/opus/opus-tools-0.1.6.tar.gz](http://downloads.xiph.org/releases/opus/opus-tools-0.1.6.tar.gz)


install each one with 

> ./configure
make
sudo make install


then  finally

>  cd $HOME/abcde_build/abcde-read-only && svn up && ./abcde



you can change setting by tinkering with

> gedit .abcde.conf


seek   > AACENCOPTS='-br 38000 -ignorelength'   for bitrate choice



those are the five routes i know.**...........**

---

### Post by andrew.46 on 2012-12-16
> **shantiq said:**
> if you want Andrew's **abcde**[...] 

Just a small clarification: I can now commit to the abcde svn repository but abcde does not belong to me :). The neroAacEnc patch was committed by me, and I added the docs, but the working part of the patch belongs to a gentleman named atheren.

---

### Post by shantiq on 2012-12-16
hey we know and was not a proprietary Andrew:KS:KS   just to say "involved in"   corrected it anyway  ............   nice clean tool
and many thanx for you adding that there

---

### Post by andrew.46 on 2012-12-16
> **shantiq said:**
> hey we know and was not a proprietary Andrew:KS:KS   just to say "involved in"   corrected it anyway  ............   nice clean tool
and many thanx for you adding that there

Lots of fun with abcde :). BTW have you added in the simple FFmpeg pipe for creating these files?

```

ffmpeg -i "08.Brain Damage.ogg" -f wav - | \
neroAacEnc -if - -br 38000 -ignorelength -of "08.Brain Damage.m4a"

```

Just needs some scripting to pick up and rewrite the meta tags...

---

### Post by shantiq on 2012-12-17
no i had not [but now you have :KS ]

this will cater for bulk

> for f in nocaseglob nullglob * ; do ffmpeg -i "$f" -f wav - | neroAacEnc -if - -br 38000 -ignorelength -of "${f%.*}.m4a " ; done

but still the tagging issue


**=========**



which reminds me there is a script from flac which retains the tags  [i do not know who wrote it but thanx to whomever]


> #!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.m4a/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKTOTAL=`metaflac "$f" --show-tag=TRACKTOTAL | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`

flac -c -d "$f" - | neroAacEnc -if -  -cbr 38000 -of  "$OUTF"
neroAacTag "$OUTF"  -meta:artist="$ARTIST" -meta:title="$TITLE" -meta:album="$ALBUM" -meta:genre="$GENRE" -meta:year="$DATE" -meta:track="$TRACKNUMBER" -meta:totaltracks="$TRACKTOTAL"
done
mkdir "$ALBUM" && mv *.m4a "$ALBUM"

paste in txt editor as flac2m4a/place in same folder as flacs files/
make executable ```
sudo chmod +x flac2m4a
```

run ```
./flac2m4a
```


**or MUCH more simply go by terminal to where flac files are and enter script above as one block**


**by the way**   neroAac   can be hiked all the way to 516000  I keep it on 38000  but you can go much higher

---

### Post by andrew.46 on 2012-12-17
This thread has become an absolute mine of information :)

---

### Post by shantiq on 2012-12-17
Andrew   we are the Ubuntu Miners  :KS :-({|=

---

### Post by Merrattic on 2012-12-17
Thanks Shantiq (& Andrew)  :thumbsup:

---

### Post by evilsoup on 2012-12-17
This is a cool thread, but I tend to prefer a quality-based variable bit rate mode (like x264's -crf option) with the -q flag. This way, the files that need it (mostly those with a higher dynamic range) will get a higher bitrate, whereas those that don't need it will use a lower bitrate. It ranges from 0 to 1, I've been using

```
neroAacEnc -if input.wav -q 0.5 outputfile.m4a
```From [here]("http://wiki.hydrogenaudio.org/index.php?title=NeroAAC"), a guide to the average (over a number of different files) bitrates of various VBRs as set by -q:

[IMG]http://i.imgur.com/c0WH9.png[/IMG]
As for that script you found, Shantiq, I happen to have written a similar one recently that uses avprobe to gather metadata and should be more universal than using metaflac. The original thread is [here]("http://ubuntuforums.org/showpost.php?p=12405263&postcount=6"), and that script should be used through nautilus-scripts. Here's a more versatile version for use on the command-line:

```

#!/bin/bash

#### Requires: avconv, neroAacEnc, NeroAacTag

#### Default VBR quality is 0.5
quality="0.5"
mode="q"
adv=

usage ()
{
    echo "Usage: convert-to-m4a input.file <arguments>
By default, this uses a VBR mode with the neroAacEnc tag of -q 0.5
You can set a constant bit rate with -br <bitrate> OR -cbr <bitrate>
You can use any other neroAacEnc options by using -adv \"-option1 -option2\" - be sure to enclose the options in quotation marks!
Advanced options and details on the encoding modes can be found in the neroAacEnc readme.txt"
}
#### Parse command-line options
if [ $# = 0 ]; then
    echo "No input file stated"
    usage
    exit
fi

while [ "$1" != "" ]; do
    case "$1" in
        -h   )    usage
                  exit
                  ;;
        -q   )    mode="q"
                  shift
                  quality="$1"
                  ;;
        -cbr )    mode="cbr"
                  shift
                  quality="$1"
                  ;;
        -br  )    mode="br"
                  shift
                  quality="$1"
                  ;;
        -adv )    shift
                  adv="$1"
                  ;;
        *    )    filename="$1"
                  ;;
    esac
    shift
done

for f in "$filename"; do

#### Now grab some metadata 
    metadata=$(avprobe "$f" 2>&1)
    title=$(echo "$metadata" | grep -i title | sed 's/.*: //')
    artist=$(echo "$metadata" | grep -i artist .tempfile | sed 's/.*: //')
    track=$(echo "$metadata" | grep -i track | sed 's/.*: //')
    tracktotal=$(echo "$metadata" | grep -i tracktotal | sed 's/.*: //')
    genre=$(echo "$metadata" | grep -i genre | sed 's/.*: //')
    date=$(echo "$metadata" | grep -i date | sed 's/.*: //')
    album=$(echo "$metadata" | grep -i album | sed 's/.*: //')
    album_artist=$(echo "$metadata" | grep -i album_artist | sed 's/.*: //')
    disc=$(echo "$metadata" | grep -i disc | sed 's/.*: //')
    if [ "$artist" = "" ]; then
        artist=$(echo "$metadata" | grep -i author | sed 's/.*: //')
    fi

#### The actual conversion to AAC M4A
    avconv -i "$f" -vn -f wav - | neroAacEnc -if - -"$mode" "$quality" -ignorelength "$adv" -of "${f%.*}.m4a"

#### Writing the metadata to the new M4A
    neroAacTag "${f%.*}.m4a" -meta:title="$title" -meta:artist="$artist" -meta:track="$track" -meta:totaltracks="$tracktotal" -meta:genre="$genre" -meta:year="$date" -meta:album="$album" -meta:disc="$disc" -meta:composer="$album_artist"
done
exit 0

```This can be used to convert any format your avconv can read to M4A with neroAacEnc (though of course, you should never transcode from one lossy format to another). Put it in your ~/bin as convert-to-m4a, and basic usage is
```
convert-to-m4a input.file
```To get a usage message, use 
```
convert-to-m4a -h
```

---

### Post by FakeOutdoorsman on 2012-12-17
> **evilsoup said:**
> From [here]("http://wiki.hydrogenaudio.org/index.php?title=NeroAAC"), a guide to the average (over a number of different files) bitrates of various VBRs as set by -q:

Hydrogen Audio Knowledgebase is a great resource. I didn't know there was a NeroAAC section. I often recommend the [LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME) and [Vorbis](http://wiki.hydrogenaudio.org/index.php?title=Vorbis) guides. If only the was one for fdk-aac.

---

### Post by shantiq on 2012-12-17
thanx for one more esoup :KS


getting mixed results with it on some of the tags


all tags good from ogg

artist and year absent from  wv

artist absent from  wma tta flac

not tried other formats


how would you use for bulk?

i tried this [and did fine][of course users can add formats to list]

>  for f in nocaseglob nullglob *.{mp3,flac,ape,wv,m4a,aac,mp4,shn,tta,wma,AOB,ogg,mpc,tak,ac3,ts,m2ts,mkv} \
 ; do convert-to-m4a "$f" ; done 

---

### Post by evilsoup on 2012-12-17
That script *should* work fine for bulk files, just use a wildcard. To convert every ogg in a directory, for example, use
```
convert-to-m4a *.ogg
```

I haven't tested it that much, it may well be imperfect (I got some weirdness with the artist on a flac I converted this way)... and in fact, using it on a directory of files doesn't seem to work. For now, you can enclose it in a for loop, but I can't see why that is necessary, since there's a *for* loop within the script itself.

A little experimenting seems to show that bash is expanding the * wildcard too early - at the variable declaration stage rather than during the *for* loop.

The only way I can think of to do truly universal conversion of metadata is to use avconv (or ffmpeg, if that's your preferred weapon) to copy the metadata over with -map_metadata... but unfortunately, that requires the creation of an extra file, and this will take more time. It shouldn't be a problem for a vaguely modern computer, though, and will simplify the script (and therefore any chance for mistake in writing it).

```

#!/bin/bash

#### Requires: avconv, neroAacEnc, NeroAacTag

#### Default VBR quality is 0.5
quality="0.5"
mode="q"
adv=

usage ()
{
    echo "Usage: convert-to-m4a input.file <arguments>
By default, this uses a VBR mode with the neroAacEnc tag of -q 0.5
You can set a constant bit rate with -br <bitrate> OR -cbr <bitrate>
You can use any other neroAacEnc options by using -adv \"-option1 -option2\" - be sure to enclose the options in quotation marks!
Advanced options and details on the encoding modes can be found in the neroAacEnc readme.txt"
}
#### Parse command-line options
if [ $# = 0 ]; then
    echo "No input file stated"
    usage
    exit
fi

while [ "$1" != "" ]; do
    case "$1" in
        -h   )    usage
                  exit
                  ;;
        -q   )    mode="q"
                  shift
                  quality="$1"
                  ;;
        -cbr )    mode="cbr"
                  shift
                  quality="$1"
                  ;;
        -br  )    mode="br"
                  shift
                  quality="$1"
                  ;;
        -adv )    shift
                  adv="$1"
                  ;;
        *    )    filename="$1"
                  ;;
    esac
    shift
done

for f in "$filename"; do

#### The actual conversion to AAC M4A
    avconv -i "$f" -vn -f wav - | neroAacEnc -if - -"$mode" "$quality" -ignorelength "$adv" -of "${f%.*}.m4a"

#### Writing the metadata to the new M4A
    avconv -i "$f" -i "${f%.*}.m4a" -map_metadata 0 -map 1 -c copy ".123-${f%.*}.m4a"
    mv ".123-${f%.*}.m4a" "${f%.*}.m4a"
done
exit 0

```

Once I've figured out how to escape the * wildcard reliably, I'll work that into the script, but for now, to do multiple files:

```

for a in *.file; do convert-to-m4a "$a"; done

```

---

### Post by ron999 on 2012-12-25
Hi
Examples for using **libfdk_aac** encoder with FFmpeg.

_**CBR**_
For AAC-LC, like this:-
(Format profile : LC)
```
ffmpeg -i foo -c:a libfdk_aac -b:a 128k -afterburner 1 -ar 44100 -ac 2 foo.m4a
```

For AAC-HE, like this:-
(Format profile : HE-AAC / LC)
```
ffmpeg -i foo -c:a libfdk_aac -profile:a aac_he -b:a 64k -afterburner 1 -ar 44100 -ac 2 foo.m4a
```

For AAC-HEv2, like this:-
(Format profile : HE-AACv2 / HE-AAC / LC)
```
ffmpeg -i foo -c:a libfdk_aac -profile:a aac_he_v2 -signaling implicit -b:a 32k -afterburner 1 -ar 44100 -ac 2 foo.m4a
```

_**VBR**_[1-5]
There's some VBR/samplerate information in HA thread here ---> [http://www.hydrogenaudio.org/forums/index.php?showtopic=95989&st=75&p=817833&#entry817833](http://www.hydrogenaudio.org/forums/index.php?showtopic=95989&st=75&p=817833&#entry817833)
```
ffmpeg -i foo -c:a libfdk_aac -vbr 3 -afterburner 1 -ar 44100 -ac 2 foo.m4a
```

(**-afterburner 1** gives improved quality, it's optional)

---

### Post by andrew.46 on 2012-12-25
> **ron999 said:**
> imho this libfdk_aac -vbr 3 sounds better than libfaac.

Is there any consensus on the *many* different types of AAC, including the HE-AAC that is the main thrust of this thread? I will admit that I am getting a little lost :( Although I am naturally drawn to anything with *afterburner* in its commandline...

---

### Post by FakeOutdoorsman on 2012-12-26
General recommendation is to use HE-AAC for low bitrates (64k and below or so); otherwise use LC-AAC. I can clearly hear a difference between HE and LC using fdk-aac.

I haven't personally performed many ABX tests, so I can't say which encoders are "better", but [Kamedo's](http://d.hatena.ne.jp/kamedo2/) tests seem thorough enough for me. For LC-AAC, fdk-aac is absent since the blog article is almost a year old, but this blog [indicates](http://d.hatena.ne.jp/kamedo2/20120102/1325523424):

> qaac > enc_aacPlus > NeroAACEnc > ffmpeg -c:a aac -cutoff 15000 &#8786; libfaac &#8786; vo-aacenc

I'd say fdk-aac would be => NeroAacEnc, but this is just a a mostly uneducated guess and should not be considered to be a very valid statement.

---

### Post by shantiq on 2012-12-26
well had a "good play"  with all these recently and have now got my ffmpeg so it has

>  DEA.L. aac  
AAC (Advanced Audio Coding) (encoders: aac libfaac libfdk_aac libaacplus )




my understanding at this point [testing with my bat ears; the only true scientific way i know :KS:KS

if you want a normal aac/m4a/mp4 audio  libfdk way better than libaac


if you want a small file [has to be below 40k to get HE-AACv2 and therefore SBR enhanced stereo]


you can get it with libaacplus or fdk [thanx Ron999 for syntax]



**This below from any audio format or video to ==== > HE-AACv2  bulk or one file ... also [B]keeps tags **[/B]

**fdk**

>    for f in nocaseglob *; do ffmpeg -i "$f" -c:a libfdk_aac -profile:a aac_he_v2 -signaling explicit_sbr -b:a 38k -afterburner 1  "${f%.*}.m4a"; done


**libaacplus**


  > for f in nocaseglob *; do ffmpeg -i "$f" -c:a libaacplus -b:a 38k  "${f%.*}.m4a"; done



**PS**   i cannot stress enough how good this format is
at 38k it sounds pretty much like a flac or similar and means you can therefore email an entire archived album as one Googlemail attachment
which is amazing... if you want to share the latest exploits of your favoured HipHop hero of the moment with your great-great aunt Beryl...

---

### Post by evilsoup on 2012-12-26
Doesn't -b:a use a fixed bitrate? Isn't it normally better to use a VBR mode targeting a quality? Unless you're doing streaming over the internet or something.

---

### Post by andrew.46 on 2012-12-26
You know that it would be absolutely crazy, and certainly would never appear in the mainstream abcde script, but now I have tinkered a little with qaac (and with abcde!) it would be only a small job to add qaac support to abcde :).

All abcde does is interrogate the cd, request information from cddb, rip to hdd as wav and then use the allocated encoder to convert +/- tag. Easy enough to slot a *new encoder* in, even if it is a windows encoder running through wine!!? The abcde engine itself does not need alteration...

---

### Post by shantiq on 2012-12-27
i have  ripped a few files with qaac    even to 320kbps
and i do not particularly rate the way they sound


i still think neroAacEnc is BEST and now fdk_aac is also really good

i hear qaac as better than libaac [but then what is not?] but nowhere near as clear or defined as 2 mentioned above


so glad i tested it [plus it is wine exe] but a tad underwhelmed :KS

love the way it does alac tho > wine qaac -A --verbose  -i *wav

one guy's ear-view for what it is worth...

---

### Post by ron999 on 2013-01-08
Hi
There's a stand-alone fdkaac encoder available from here ---> [https://github.com/nu774/fdkaac]("https://github.com/nu774/fdkaac")

Use [FONT="Courier New"]fdkaac -h[/FONT] to show the options.

Examples of use.

**CBR**
For AAC-LC, like this:-
(Format profile : LC)
```
fdkaac -b 128k -o foo.m4a foo.wav
```

For AAC-HE, like this:-
(Format profile : HE-AAC / LC)
```
fdkaac -p 5 -b 64k -o foo.m4a foo.wav
```

For AAC-HEv2, like this:-
(Format profile : HE-AACv2 / HE-AAC / LC)
```
fdkaac -p 29 -b 32k -o foo.m4a foo.wav
```

**VBR**[1-5]
```
fdkaac -m 3 -o foo.m4a foo.wav
```

(**afterburner** is enabled by default, use -a 0 to disable it)

---

### Post by evilsoup on 2013-01-08
Having just played around with it a little bit, I have to mostly concur with Shantiq about the high quality of HE-AAC. I think there were a few audio artefacts, but they were so hard to notice that they could just as easily be my imagination, and I certainly wouldn't pick them up with regular listening, where I'm not trying to find those things. An audiophile with top-end gear might disagree, of course, and I haven't tested this on speakers yet (which is where most MP3s fall down for me), but so far it's sounding good. 

It's nice to have a good-quality AAC encoder within ffmpeg at last, I've always found it annoying having to use neroaacenc. Testing out libfdk_aac's -vbr setting, even the lowest setting of -vbr 1 puts out (to me) audio indistinguishable from the source FLAC. I'll probably be sticking to regular AAC for my DVD rips, since not all hardware devices support HE-AAC yet - assuming it sounds good with surround-sound (and I see no reason why it shouldn't).

ron999, what does the -signaling flag do in the ffmpeg examples you gave? I like to know what all the options do when I'm using the CLI, and the ffmpeg documentation is typically unhelpful. I would guess that it puts some kind of metadata flag on the file, to tell the player what AAC profile is being used, or something like that?

EDIT: huh, weird. I used mediainfo on one of the files I encoded with -vbr, and it says 
```

Bit rate mode                            : Constant

```

...so the -vbr tag actually doesn't output a variable bit rate file? I'll have to check out that standalone fdk_aac encoder, to test if it is just an ffmpeg problem.

---

### Post by shantiq on 2013-01-08
> even the lowest setting of -vbr 1 puts out (to me) audio indistinguishable from the source FLAC


so true and that for me is the whole point ...   it sounds [to my ears] as good altho 22000kHz and 38kbps as opposed to 48000khz
and say 700kbps

for more detailed info 

as Ron showed me 



```
ffmpeg --help full
```   gives you



 > libfdk_aac AVOptions:
-afterburner       <int>        E...A. Afterburner (improved quality) (from 0 to 1)
-eld_sbr           <int>        E...A. Enable SBR for ELD (for SBR in other configurations, use the -profile parameter) (from 0 to 1)
-signaling         <int>        E...A. SBR/PS signaling style (from -1 to 2)
   default                      E...A. Choose signaling implicitly (explicit hierarchical by default, implicit if global header is disabled)
   implicit                     E...A. Implicit backwards compatible signaling
   explicit_sbr                 E...A. Explicit SBR, implicit PS signaling
   explicit_hierarchical              E...A. Explicit hierarchical signaling
-latm              <int>        E...A. Output LATM/LOAS encapsulated data (from 0 to 1)
-header_period     <int>        E...A. StreamMuxConfig and PCE repetition period (in frames) (from 0 to 65535)
-vbr               <int>        E...A. VBR mode (1-5) (from 0 to 5)


and



> fdkaac -h
fdkaac 0.0.8
Usage: fdkaac [options] input_file
Options:
 -h, --help                    Print this help message
 -p, --profile <n>             Profile (audio object type)
                                 2: MPEG-4 AAC LC (default)
                                 5: MPEG-4 HE-AAC (SBR)
                                29: MPEG-4 HE-AAC v2 (SBR+PS)
                                23: MPEG-4 AAC LD
                                39: MPEG-4 AAC ELD
                               129: MPEG-2 AAC LC
                               132: MPEG-2 HE-AAC (SBR)
                               156: MPEG-2 HE-AAC v2 (SBR+PS)
 -b, --bitrate <n>             Bitrate in bits per seconds (for CBR)
 -m, --bitrate-mode <n>        Bitrate configuration
                                 0: CBR (default)
                                 1-5: VBR
                               (VBR mode is not officially supported, and
                                works only on a certain combination of
                                parameter settings, sample rate, and
                                channel configuration)
 -w, --bandwidth <n>           Frequency bandwidth in Hz (AAC LC only)
 -a, --afterburner <n>         Afterburner
                                 0: Off
                                 1: On(default)
 -L, --lowdelay-sbr            Enable ELD-SBR (AAC ELD only)
 -s, --sbr-signaling <n>       SBR signaling mode
                                 0: Implicit, backward compatible(default)
                                 1: Explicit SBR and implicit PS
                                 2: Explicit hierarchical signaling
 -f, --transport-format <n>    Transport format
                                 0: RAW (default, muxed into M4A)
                                 1: ADIF
                                 2: ADTS
                                 6: LATM MCP=1
                                 7: LATM MCP=0
                                10: LOAS/LATM (LATM within LOAS)
 -c, --adts-crc-check          Add CRC protection on ADTS header
 -h, --header-period <n>       StreamMuxConfig/PCE repetition period in
                               transport layer

 -o <filename>                 Output filename
 --ignore-length               Ignore length of WAV header

Tagging options:
 --title <string>
 --artist <string>
 --album <string>
 --genre <string>
 --date <string>
 --composer <string>
 --grouping <string>
 --comment <string>
 --album-artist <string>
 --track <number[/total]>
 --disk <number[/total]>
 --tempo <n>


---

### Post by ron999 on 2013-01-08
> **evilsoup said:**
> ... what does the -signaling flag do ... I would guess that it puts some kind of metadata flag on the file, to tell the player what AAC profile is being used...
This is known as "SBR signalling"

> **evilsoup said:**
> ...so the -vbr tag actually doesn't output a variable bit rate file
Maybe MediaInfo gets confused.

Files converted @CBR with fdkaac encoder show as Variable with MediaInfo.
This is probably true, I think AAC CBR is just very constrained VBR.

---

### Post by evilsoup on 2013-01-08
Well at the end of the day I'll just have to trust that the people who made it knew what they were doing. It passes the listening test anyway, and that's the only one that really matters.

---

