---
title: "exporting to ape with Audacity"
date: 2020-08-09
forum: Multimedia Software
---

### Post by shantiq on 2020-08-09
In "external program" been trying a lot of combinations but the syntax so far is eluding me


this is the [guide]("https://manual.audacityteam.org/man/exporting_to_an_external_program.html")

this is the encoder i use [ffmpeg not an option to encode]:


```
mac--- Monkey's Audio Console Front End (v 4.11) (c) Matthew T. Ashland ---
Proper Usage: [Input File] [Output File] [Mode]


Modes: 
    Compress (fast): '-c1000'
    Compress (normal): '-c2000'
    Compress (high): '-c3000'
    Compress (extra high): '-c4000'
    Compress (insane): '-c5000'
    Decompress: '-d'
    Verify: '-v'
    Convert: '-nXXXX'


Examples:
    Compress: mac "Metallica - One.wav" "Metallica - One.ape" -c2000
    Decompress: mac "Metallica - One.ape" "Metallica - One.wav" -d
    Verify: mac "Metallica - One.ape" -v
    (note: int filenames must be put inside of quotations)



```



Lines I tried to use out of many :D

```
mac - "%f.wav" "%f.ape" -c3000
```
or
```
mac - "%f.wav" - "%f.ape" -c3000
```
or
```
mac - "f%.wav" - "f%.ape" -c3000

```

[[IMG]https://i.postimg.cc/5XHMdVWN/Screenshot-from-2020-08-09-17-41-44.png[/IMG]]("https://postimg.cc/5XHMdVWN")





any better offers?

thanx

---

### Post by Yellow Pasque on 2020-08-10
Make sure 'mac' works as a regular command first. Here in Debian sid, it just segfaults, so I can't really test it.
It looks like you are trying to use two input files (- is stdin). Try:
```
mac - "%f.ape" -c3000
```

---

### Post by Yellow Pasque on 2020-08-10
Also, I have to ask, why Monkey's Audio?

---

### Post by shantiq on 2020-08-10
hi yellow pasque

thanx for reply

that line does not work but looks better than my efforts
APE    just to see if it works and it should ; just a case of cracking the syntax ...   I think you got closer but still no dice



> [h=2]Format Options[/h][COLOR=#000000][FONT=sans-serif]In the **Command:** box type:[/FONT][/COLOR]

[LIST=1]
[*]The path to the program
[*]If the program syntax requires it, **space** then the *infile* command
[*]**Space**, **hyphen**
[*]If required, **space** then valid output options for the file
[*]If the program syntax requires it, **space** then the *outfile* command
[*]Finally (assuming file output), **space** then **"%f"**.
[/LIST]
[COLOR=#000000][FONT=sans-serif]The "%f" command passes the file name and extension entered in the [/FONT][/COLOR][Export Audio]("https://manual.audacityteam.org/man/file_export_dialog.html")[COLOR=#000000][FONT=sans-serif] dialog as the output file of the external program.[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2020-08-10
Here's how I read it:
1. The path to the program
```
mac
```

2. If the program syntax requires it, space then the infile command
Not/Applicable, since mac does not need "-i" like ffmpeg, for example.

3. Space, hyphen
```
mac -
```

4. If required, space then valid output options for the file
mac puts the options on the end, so skip for now.

5. If the program syntax requires it, space then the outfile command
Not/Applicable, since mac does not need "-o" like flac, for example.

6. Finally (assuming file output), space then "%f".
(Note that you either need to add the .ape here or on dialog's filename.)
```
mac - "%f"
```

7. Put your option on the end
```
mac - "%f" -c3000
```

^That is the only thing that makes sense to me.

---

### Post by shantiq on 2020-08-10
Thanx 
I had tried that but it yields

[[IMG]https://i.postimg.cc/JDYq7XZf/1.png[/IMG]]("https://postimg.cc/JDYq7XZf")


The problem there is here is that mac wants:

> Proper Usage: [Input File] [Output File] [Mode]

Modes: 
    Compress (fast): '-c1000'
    Compress (normal): '-c2000'
    Compress (high): '-c3000'
    Compress (extra high): '-c4000'
    Compress (insane): '-c5000'
    Decompress: '-d'
    Verify: '-v'
    Convert: '-nXXXX'


Examples:
    Compress: ```
mac "Metallica - One.wav" "Metallica - One.ape" -c2000

```    Decompress: mac "Metallica - One.ape" "Metallica - One.wav" -d
    Verify: mac "Metallica - One.ape" -v
    (note: int filenames must be put inside of quotations)




mention of wav and ape in the line

also tried ```
mac - "%f.ape"  -c3000
```

I know there must a way :D but which?

---

### Post by Yellow Pasque on 2020-08-11
1002 = invalid input file (I tried it in Ubuntu 20.04 VM and got the same thing. At least I was able to get 'mac' working as its own command.)

"mac" encoder doesn't seem to like input from stdin. I think you are better off working with WAV file in Audacity and converting when you're done.

---

### Post by &amp;KyT$0P# on 2020-08-11
Did you try specifying [FONT=Courier New]/dev/stdin[/FONT] as input file?

---

### Post by Yellow Pasque on 2020-08-11
> **halogen2 said:**
> Did you try specifying [FONT=Courier New]/dev/stdin[/FONT] as input file?

This gives the  same error 1002 - Invalid Input
I don't think 'mac' can take input from stdin

---

### Post by shantiq on 2020-08-13
Thanx for input guys

There might indeed be incompatibilities in the way mac was written but somehow there must be a way round this

```
[COLOR=#000000][FONT=&amp]mac "Metallica - One.wav" "Metallica - One.ape" -c2000[/FONT][/COLOR]
```

[FONT=arial][COLOR=#000000]it wants to have .wav and .ape written somewhere in the line it seems and you cannot get away with not using -cXXXX  I have tried on the command line and all 3 must be there

[/COLOR][/FONT]```
[COLOR=#000000][FONT=&amp]mac "Metallica - One.wav" -c2000[/FONT][/COLOR]
```[FONT=arial][COLOR=#000000] or [/COLOR][/FONT]```
[COLOR=#000000][FONT=&amp]mac "Metallica - One.wav" "Metallica - One.ape"[/FONT][/COLOR]
```[FONT=arial][COLOR=#000000] really do not work


Also Maybe audacity was written so that it can only accept some and not others according to the way they were put together but somehow it feels it should be doable [/COLOR][/FONT]:KS



[FONT=arial][COLOR=#000000]PS   now posted same on Audacity Forum
[/COLOR][/FONT]

---

### Post by Yellow Pasque on 2020-08-14
> **shantiq said:**
> PS now posted same on Audacity Forum

A link would be nice. Oh, look at that!: [https://forum.audacityteam.org/viewtopic.php?f=48&t=112565](https://forum.audacityteam.org/viewtopic.php?f=48&t=112565)

---

### Post by shantiq on 2020-08-14
yep the reason why i had not linked YP was that it takes time for post to be moderated so NO link at first; anyway someone also posted a reply which does not work ...

#backtothedrawingboard

---

### Post by Yellow Pasque on 2020-08-14
> **shantiq said:**
> yep the reason why i had not linked YP was that it takes time for post to be moderated so NO link at first

Ah, I see. 
Anyway, the Audacity dev gave you the same command I did, so that makes me feel more confident that I read the directions correctly and I didn't suggest anything nonsensical.

---

### Post by shantiq on 2020-08-14
No YP nothing nonsensical; just a difficult puzzle. Thanx for input


==================


**EDIT:**  Ha ok seems the encoder only handles 16-bit **QED** . After judicious questions from Steve on the [audacity forum]("https://forum.audacityteam.org/viewtopic.php?f=48&t=112565&p=402449#p402449") ; this is what seems to transpire:

I ran a 24-bit alac to wav then to mac and again the dreaded ERROR: 1002 reared its head again

And since Audacity works from 32-bit that right there might indeed be the fly in the ointment

see below:


```
shan@shan-Aspire-XC-780:~/Desktop/trial$ mediainfo Rubycon\ Part\ 1.m4a 
General
Complete name                            : Rubycon Part 1.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A  (M4A /isom/iso2)
File size                                : 185 MiB
Duration                                 : 17 min 15 s
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 494 kb/s
Album                                    : Rubycon
Track name/Position                      : 1
Performer                                : Tangerine Dream
Genre                                    : Berlin School, Krautrock, Kosmische Rock, Cosmic Rock, Electronic, Electronica,
Recorded date                            : 1975
Writing application                      : Lavf58.49.100
Cover                                    : Yes
COMMENT                                  : 1975 UK Cassette


Audio
ID                                       : 1
Format                                   : ALAC
Codec ID                                 : alac
Codec ID/Info                            : Apple Lossless Audio Codec
Duration                                 : 17 min 15 s
Duration_LastFrame                       : -4 ms
Bit rate mode                            : Variable
Bit rate                                 : 1 472 kb/s
Nominal bit rate                         : 2 304 kb/s
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 kHz
Bit depth                                : 24 bits
Stream size                              : 182 MiB (98%)
Default                                  : Yes
Alternate group                          : 1


shan@shan-Aspire-XC-780:~/Desktop/trial$ ffmpeg -i Rubycon\ Part\ 1.m4a -c:a pcm_s24le Rubycon\ Part\ 1.WAV
ffmpeg version N-98601-g134a48a Copyright (c) 2000-2020 the FFmpeg developers
  built with gcc 9 (Ubuntu 9.3.0-10ubuntu2)
  configuration: --prefix=/home/shan/ffmpeg_build --pkg-config-flags=--static --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --extra-libs='-lpthread -lm' --bindir=/home/shan/bin --enable-gpl --enable-gnutls --enable-libaom --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-nonfree
  libavutil      56. 57.100 / 56. 57.100
  libavcodec     58. 98.100 / 58. 98.100
  libavformat    58. 49.100 / 58. 49.100
  libavdevice    58. 11.101 / 58. 11.101
  libavfilter     7. 87.100 /  7. 87.100
  libswscale      5.  8.100 /  5.  8.100
  libswresample   3.  8.100 /  3.  8.100
  libpostproc    55.  8.100 / 55.  8.100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x562aa7618380] stream 0, timescale not set
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Rubycon Part 1.m4a':
  Metadata:
    major_brand     : M4A 
    minor_version   : 512
    compatible_brands: M4A isomiso2
    artist          : Tangerine Dream
    album           : Rubycon
    genre           : Berlin School, Krautrock, Kosmische Rock, Cosmic Rock, Electronic, Electronica,
    track           : 1
    date            : 1975
    encoder         : Lavf58.49.100
    COMMENT         : 1975 UK Cassette
  Duration: 00:17:15.77, start: 0.000000, bitrate: 1494 kb/s
    Stream #0:0(und): Audio: alac (alac / 0x63616C61), 48000 Hz, stereo, s32p (24 bit), 1471 kb/s (default)
    Metadata:
      handler_name    : SoundHandler
    Stream #0:1: Video: mjpeg (Baseline), yuvj444p(pc, bt470bg/unknown/unknown), 1540x2492 [SAR 72:72 DAR 55:89], 90k tbr, 90k tbn, 90k tbc (attached pic)
Stream mapping:
  Stream #0:0 -> #0:0 (alac (native) -> pcm_s24le (native))
Press [q] to stop, [?] for help
Output #0, wav, to 'Rubycon Part 1.WAV':
  Metadata:
    major_brand     : M4A 
    minor_version   : 512
    compatible_brands: M4A isomiso2
    IART            : Tangerine Dream
    IPRD            : Rubycon
    IGNR            : Berlin School, Krautrock, Kosmische Rock, Cosmic Rock, Electronic, Electronica,
    IPRT            : 1
    ICRD            : 1975
    ICMT            : 1975 UK Cassette
    ISFT            : Lavf58.49.100
    Stream #0:0(und): Audio: pcm_s24le ([1][0][0][0] / 0x0001), 48000 Hz, stereo, s32 (24 bit), 2304 kb/s (default)
    Metadata:
      handler_name    : SoundHandler
      encoder         : Lavc58.98.100 pcm_s24le
size=  291311kB time=00:17:15.77 bitrate=2304.0kbits/s speed= 506x    
video:0kB audio:291311kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.000094%
shan@shan-Aspire-XC-780:~/Desktop/trial$ mediainfo Rubycon\ Part\ 1.WAV 
General
Complete name                            : Rubycon Part 1.WAV
Format                                   : Wave
File size                                : 284 MiB
Duration                                 : 17 min 15 s
Overall bit rate mode                    : Constant
Overall bit rate                         : 2 304 kb/s
Part/Position                            : 1
Director                                 : Tangerine Dream
Genre                                    : Berlin School, Krautrock, Kosmische Rock, Cosmic Rock, Electronic, Electronica,
Recorded date                            : 1975
Writing application                      : Lavf58.49.100
Original source form/Name                : Rubycon
Comment                                  : 1975 UK Cassette


Audio
Format                                   : PCM
Format settings                          : Little / Signed
Codec ID                                 : 00000001-0000-0010-8000-00AA00389B71
Duration                                 : 17 min 15 s
Bit rate mode                            : Constant
Bit rate                                 : 2 304 kb/s
Channel(s)                               : 2 channels
Channel layout                           : L R
Sampling rate                            : 48.0 kHz
Bit depth                                : 24 bits
Stream size                              : 284 MiB (100%)




shan@shan-Aspire-XC-780:~/Desktop/trial$ mac Rubycon\ Part\ 1.WAV Rubycon\ Part\ 1.ape -C5000
--- Monkey's Audio Console Front End (v 4.11) (c) Matthew T. Ashland ---
Compressing (insane)...


Error: 1002

```

======

further corroborated by the fact that I got nowhere fast with ttaenc either [I know I can get a tta through ffmpeg in audacity]


the message I get from Audacity and ttaenc is this:


```
ttaenc -e Rubycon\ Part\ 1.wav 
TTA1 lossless audio encoder/decoder, release 3.4.1
Copyright (c) 2007 Aleksander Djuric. All rights reserved.
For more information see [http://tta.sourceforge.net](http://tta.sourceforge.net)
------------------------------------------------------------
File:    [Rubycon Part 1.wav]
[COLOR=#800000][B][SIZE=2]Error:  not compatible file format
[/SIZE][/B][/COLOR]Total:    [0/1, 0.0/0.0 Mb], ratio: 0.000, time: 0'00
------------------------------------------------------------




FROM THIS 32-Bit FILE


shan@shan-Aspire-XC-780:~/Desktop/trial$ mediainfo Rubycon\ Part\ 1.wav 
General
Complete name                            : Rubycon Part 1.wav
Format                                   : Wave
File size                                : 379 MiB
Duration                                 : 17 min 15 s
Overall bit rate mode                    : Constant
Overall bit rate                         : 3 072 kb/s
Part/Position                            : 1
Director                                 : Tangerine Dream
Genre                                    : Berlin School, Krautrock, Kosmische Rock, Cosmic Rock, Electronic, Electronica,
Recorded date                            : 1975
Writing application                      : Lavf58.49.100
Original source form/Name                : Rubycon
Comment                                  : 1975 UK Cassette


Audio
Format                                   : PCM
Format settings                          : Little / Signed
Codec ID                                 : 00000001-0000-0010-8000-00AA00389B71
Duration                                 : 17 min 15 s
Bit rate mode                            : Constant
Bit rate                                 : 3 072 kb/s
Channel(s)                               : 2 channels
Channel layout                           : L R
Sampling rate                            : 48.0 kHz
Bit depth                                : 32 bits
Stream size                              : 379 MiB (100%)

```


AND YET ffmpeg CAN encode to 24-bit from a 32-bit when ttaenc cannot so there must be a way to do likewise in Audacity maybe with mac and ttaenc if you catch my roundabout logic  ;) or maybe not ...


see: ```
ffmpeg -i Rubycon\ Part\ 1.wav -c:a tta Rubycon\ Part\ 1.tta
ffmpeg version N-98601-g134a48a Copyright (c) 2000-2020 the FFmpeg developers
  built with gcc 9 (Ubuntu 9.3.0-10ubuntu2)
  configuration: --prefix=/home/shan/ffmpeg_build --pkg-config-flags=--static --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --extra-libs='-lpthread -lm' --bindir=/home/shan/bin --enable-gpl --enable-gnutls --enable-libaom --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-nonfree
  libavutil      56. 57.100 / 56. 57.100
  libavcodec     58. 98.100 / 58. 98.100
  libavformat    58. 49.100 / 58. 49.100
  libavdevice    58. 11.101 / 58. 11.101
  libavfilter     7. 87.100 /  7. 87.100
  libswscale      5.  8.100 /  5.  8.100
  libswresample   3.  8.100 /  3.  8.100
  libpostproc    55.  8.100 / 55.  8.100
Input #0, wav, from 'Rubycon Part 1.wav':
  Metadata:
    artist          : Tangerine Dream
    comment         : 1975 UK Cassette
    date            : 1975
    genre           : Berlin School, Krautrock, Kosmische Rock, Cosmic Rock, Electronic, Electronica,
    album           : Rubycon
    track           : 1
    encoder         : Lavf58.49.100
  Duration: 00:17:15.77, bitrate: 3072 kb/s
    Stream #0:0: Audio: pcm_s32le ([1][0][0][0] / 0x0001), 48000 Hz, stereo, s32, 3072 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s32le (native) -> tta (native))
Press [q] to stop, [?] for help
[tta @ 0x55ebbc8c05c0] encoding as 24 bits-per-sample
Output #0, tta, to 'Rubycon Part 1.tta':

```




PS:    all these I have tested and work


```
ffmpeg -i - -c:a alac -sample_fmt s32p "%f" [24-bit]
ffmpeg -i - -acodec alac "%f"   [16-bit]
ffmpeg -i -  -c:a wavpack  "%f" [16-bit]
ffmpeg -i -  -c:a wavpack -sample_fmt s32p "%f" [24-bit]
ffmpeg -i - -c:a tta "%f" [16-bit]
shorten - "%f"   [16-bit]
```

---

### Post by andrew.46 on 2020-08-18
I am wondering if some of these issues are due to some of the slightly odd versions of mac for Linux that are circulating? I achieved success with Audacity and mac by using a version of mac that is apparently a port of the original work and can be seen [here...]("https://github.com/fernandotcl/monkeys-audio") I do not claim to understand all of the different versions circulating, some from Debian Multimedia, some from SuperMMX (yes Slackware I am looking at you!!).

If you want to take it for a spin the following should get it going, you should *remove *your installed version first:

```

cd $HOME/Desktop
wget https://github.com/fernandotcl/monkeys-audio/archive/release-3.99.6.tar.gz
tar xvf release-3.99.6.tar.gz && cd monkeys-audio-release-3.99.6
cmake .
make
install -D -s -m 0755 mac $HOME/bin

```

This certainly worked in well with Audacity and I simply used the command line:

```

mac - "%f" -c3000

```

in the 'Format Options --> Command:' box. The filename is not automatically changed by Audacity based on this, if you look at the box at the top of that window, next to "Name" I simply trimmed the suffix off and added filename.ape and all was well. I add a screenshot here that hopefully makes that clear:

---

### Post by shantiq on 2020-08-18
Thanx Andrew this works
I had finally worked out my mac version was limited but had stopped there

Now i know ape can now produce 24-bit files since 2004 which is what I am after here. This here produced a 16-bit from a 32-bit wav
Any way to do that you can think of?


Again much appreciated

---

### Post by andrew.46 on 2020-08-18
> **shantiq said:**
> Now i know ape can now produce 24-bit files since 2004 which is what I am after here. This here produced a 16-bit from a 32-bit wav
Any way to do that you can think of?

I suspect that you are actually the expert in this area rather than myself :). What is missing here is an *active* developer for the Linux port, I see the Windows version is being developed quite actively with a recent release of version 5.49....

**Edit:** Actually I just installed the latest Monkey's Audio on my Win 10 VM and it is a very nice application! And as you might expect it took a 24bit wav file and created a 24bit ape file with no fuss :)

**Edit again!** And the latest Windows Monkey's Audio works perfectly from Wine. Not much use for adding to various Linux applications but even so...

---

### Post by shantiq on 2020-08-19
yea  i have done this easy too Andrew with dbpoweramp [free version]("https://www.dbpoweramp.com/install/dMC-R17.1-Ref-Trial.exe") to try and Monkey's exe 5.49 :KS but yes i suppose at this point there are no Linux version of mac advanced enuff to do that ....   we will be patient then


```
mediainfo Rubycon\ Part\ 1.ape General
Complete name                            : Rubycon Part 1.ape
Format                                   : Monkey's Audio
File size                                : 175 MiB
Duration                                 : 17 min 15 s
Overall bit rate                         : 1 418 kb/s


Audio
Format                                   : Monkey's Audio
Duration                                 : 17 min 15 s
Bit rate                                 : 1 418 kb/s
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 kHz
Bit depth                                : 24 bits
Compression mode                         : Lossless
Compression ratio                        : 1.624
Stream size                              : 175 MiB (100%)
Encoding settings                        : Insane



```




**AND   **it does not seem possible to use wine to bring an exe as an external encoder   tried with flac.exe then MAC.exe and no good so far

used:

```
wine "/home/shan/.wine/drive_c/Program Files/Monkey's Audio/MAC.exe" - "%f"  -C5000
```   and again gave me error 1002

when I tried the flac.exe to see it was wine it gave me yikes >> [[IMG]https://i.postimg.cc/HrpfM1gC/1.png[/IMG]]("https://postimg.cc/HrpfM1gC")

So I take it audacity does not want to put a wine exe through ...




[B]--===========


[/B]*so the cumbersome route from a 24-bit wav  *;) ```
wine "/home/shan/.wine/drive_c/Program Files/Monkey's Audio/MAC.exe" '/home/shan/Desktop/trial/Rubycon Part 24.wav' '/home/shan/Desktop/trial/Rubycon Part 24.ape' -C5000--- Monkey's Audio Console Front End (v 5.49) (c) Matthew T. Ashland ---
Compressing (insane)...
Progress: 100.0% (0.0 seconds remaining, 44.0 seconds total)          
Success...
016d:fixme:ver:GetCurrentPackageId (0x32fe94 (nil)): stub
shan@shan-Aspire-XC-780:~$ mediainfo '/home/shan/Desktop/trial/Rubycon Part 24.ape'
General
Complete name                            : /home/shan/Desktop/trial/Rubycon Part 24.ape
Format                                   : Monkey's Audio
File size                                : 175 MiB
Duration                                 : 17 min 15 s
Overall bit rate                         : 1 418 kb/s


Audio
Format                                   : Monkey's Audio
Duration                                 : 17 min 15 s
Bit rate                                 : 1 418 kb/s
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 kHz
Bit depth                                : 24 bits
Compression mode                         : Lossless
Compression ratio                        : 1.624
Stream size                              : 175 MiB (100%)
Encoding settings                        : Insane



```

---

