---
title: "xHE-AAC"
date: 2019-12-23
forum: Multimedia Software
---

### Post by shantiq on 2019-12-23
do any of you know anything about this codec mentioned [here]("http://www.andrews-corner.org/qaac.html") by Andrew in this excellent howto

He says early days ;)


   [wiki]("https://en.wikipedia.org/wiki/Unified_Speech_and_Audio_Coding")

any news?   any idea how to test find samples and more importantly to convert to

> **xHE-AAC:** Otherwise known as "Extended High      Efficiency AAC". This is the most recent addition to the AAC family      and it aims to unify speech and music encoding primarily for broadcast      with high quality encoding at low bitrates. As far as I know there is      no Linux encoder available yet and the few samples I have found have      been unplayable on Linux. Early days...


Thanx


shan

---

### Post by Yellow Pasque on 2019-12-29
[https://trac.ffmpeg.org/ticket/8411](https://trac.ffmpeg.org/ticket/8411)

---

### Post by andrew.46 on 2020-02-01
Hey Shan :). I never did find too much more about that one...

---

### Post by andrew.46 on 2020-02-03
Somewhat piqued again by xHE-AAC I have investigated a little further and sent an email to Fraunhofer IIS regarding use and licensing. Looks like there are no immediate plans for releasing the encoder / decoder that most people are keen for :(. Mandy (Head of Marketing Communications Audio & Media Technologies Division) sent the following very polite message back to me:

> 
thanks for your mail and your interest in our technology. Unfortunately we are offering our software
only for manufacturers or hard- or software to implement it into their products. We are only a B-2-B
operating company.

We hope that in the near future we can see offers for audio encoders such as the Sonnox tools to
include xHE into their products. 


So keen audiophiles will have to wait a fair while before coming to grips with xHE-AAC...

---

### Post by shantiq on 2020-02-04
Thanx Andrew and hi ;) and Yellow Pasque

WE'll await  .....

---

### Post by andrew.46 on 2020-04-04
> **shantiq said:**
> Thanx Andrew and hi ;) and Yellow Pasque

WE'll await  .....

Allow me to make your day Shan, or even your year perhaps:

How do I produce xHE-AAC files under Ubuntu?
[https://askubuntu.com/q/1224198/57576](https://askubuntu.com/q/1224198/57576)

Happily producing xHE-AAC files here for the last hour, I won't easily forget the excitement of producing my very first one :)

---

### Post by shantiq on 2020-04-05
Andrew you are a WIZARD! :mad:

Will very soon give it a whirl and report

Hope all good with you and yours Down Under

Peace

shan

---

### Post by shantiq on 2020-04-05
You really are a wizard

Install + Conversion went swimmingly

Tried Mplayer/Mpv/ffmplay   no dice for me ....     but you may have more recent versions on your system which do


But Foobar  plugin [here ]("https://www.foobar2000.org/components/view/foo_pd_aac")     see below pic   [then i realized you had put that info on the askubuntu but i leave it anyway for other visitors]


> [COLOR=#000000][FONT=Tahoma]This component replaces the stock input component's AAC decoder with the one from FDK-AAC v2.0.1, to support AAC formats not supported by FFmpeg, such as xHE-AAC / USAC.[/FONT][/COLOR]

===================

Of course   you know what i am gonna say ?   ;)    :KS     ABCDE? to keep you busy in this odd phase :)

[[IMG]https://i.postimg.cc/Lq4C6K4L/xHE-AAC.png[/IMG]]("https://postimg.cc/Lq4C6K4L")



============

mediainfo is not put out tho

```
mediainfo 01\ -\ Microbes.m4a General
Complete name                            : 01 - Microbes.m4a
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42 (mp42/isom)
File size                                : 5.41 MiB
Duration                                 : 3 min 45 s
Overall bit rate mode                    : Variable
Overall bit rate                         : 201 kb/s
Encoded date                             : UTC 1954-04-05 08:54:53
Tagged date                              : UTC 1954-04-05 08:55:16


Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Codec ID                                 : mp4a-40-42
Duration                                 : 3 min 45 s
Source duration                          : 3 min 45 s
Source_Duration_LastFrame                : -13 ms
Bit rate mode                            : Variable
Bit rate                                 : 201 kb/s
Maximum bit rate                         : 342 kb/s
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 kHz
Frame rate                               : 46.875 FPS (1024 SPF)
Compression mode                         : Lossy
Stream size                              : 5.37 MiB (99%)
Source stream size                       : 5.37 MiB (99%)
Title                                    : crh
Encoded date                             : UTC 1954-04-05 08:54:53
Tagged date                              : UTC 1954-04-05 08:55:16



```

---

### Post by andrew.46 on 2020-04-05
It would be quite easy to add support for exhale / xHE-AAC to abcde but I guess the big issue at the moment would be playback. The tipping point will be when support arrives in avcodec...

BTW your copy of mediainfo must be a little old, mine shows:

```

andrew@ilium~$ mediainfo luckynight_USAC.m4a 
General
Complete name                            : luckynight_USAC.m4a
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42 (mp42/isom)
File size                                : 766 KiB
Duration                                 : 1 min 0 s
Overall bit rate mode                    : Variable
Overall bit rate                         : 104 kb/s
Encoded date                             : UTC 1954-04-05 10:13:07
Tagged date                              : UTC 1954-04-05 10:13:11

Audio
ID                                       : 1
Format                                   : USAC
Format/Info                              : Unified Speech and Audio Coding
Commercial name                          : xHE-AAC
Codec ID                                 : mp4a-40-42
Duration                                 : 1 min 0 s
Source duration                          : 1 min 0 s
Source_Duration_LastFrame                : -18 ms
Bit rate mode                            : Variable
Bit rate                                 : 104 kb/s
Maximum bit rate                         : 162 kb/s
Channel(s)                               : 2 channels
Channel layout                           : L R
Sampling rate                            : 44.1 kHz
Frame rate                               : 43.066 FPS (1024 SPF)
Compression mode                         : Lossy
Stream size                              : 755 KiB (98%)
Source stream size                       : 755 KiB (99%)
Title                                    : crh
Encoded date                             : UTC 1954-04-05 10:13:07
Tagged date                              : UTC 1954-04-05 10:13:11
Sample peak level                        : -0.188 dBFS
Program loudness                         : -18.25 LKFS


andrew@ilium~$ 

```

And I suspect that I don't have the very latest:

```

andrew@ilium~$ mediainfo --version
MediaInfo Command line, 
MediaInfoLib - v19.04
andrew@ilium~$ 

```

Of course tagging would be easy enough to add with AtomicParsley, so perhaps this would be enough:

```

exhale 3 luckynight.wav luckynight_USAC.m4a && \
AtomicParsley luckynight_USAC.m4a \
              --album "Treasure Quest Soundtrack" \
              --artist "Jody Marie Gnant" \
              --tracknum "9" \
              --title "Lucky Night" \
              --genre "Soundtrack" \
              --year "1995" \
              --comment "Testing exhale encoding..." \
              --overWrite

```

Very exciting times :)

---

### Post by shantiq on 2020-04-05
mediainfo --version
MediaInfo Command line, 
MediaInfoLib - v17.12


;)


So went to [https://mediaarea.net/en/MediaInfo/Download/Ubuntu](https://mediaarea.net/en/MediaInfo/Download/Ubuntu)

and now got:

```
mediainfo 01\ -\ Microbes.m4a General
Complete name                            : 01 - Microbes.m4a
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42 (mp42/isom)
File size                                : 5.41 MiB
Duration                                 : 3 min 45 s
Overall bit rate mode                    : Variable
Overall bit rate                         : 201 kb/s
Encoded date                             : UTC 1954-04-05 08:54:53
Tagged date                              : UTC 1954-04-05 08:55:16


Audio
ID                                       : 1
Format                                   : USAC
Format/Info                              : Unified Speech and Audio Coding
Commercial name                          : xHE-AAC
Codec ID                                 : mp4a-40-42
Duration                                 : 3 min 45 s
Source duration                          : 3 min 45 s
Source_Duration_LastFrame                : -13 ms
Bit rate mode                            : Variable
Bit rate                                 : 201 kb/s
Maximum bit rate                         : 342 kb/s
Channel(s)                               : 2 channels
Channel layout                           : L R
Sampling rate                            : 48.0 kHz
Frame rate                               : 46.875 FPS (1024 SPF)
Compression mode                         : Lossy
Stream size                              : 5.37 MiB (99%)
Source stream size                       : 5.37 MiB (99%)
Title                                    : crh
Encoded date                             : UTC 1954-04-05 08:54:53
Tagged date                              : UTC 1954-04-05 08:55:16
Sample peak level                        : -3.562 dBFS
Program loudness                         : -15.75 LKFS



```

```
mediainfo --versionMediaInfo Command line, 
MediaInfoLib - v20.03



```

---

### Post by Yellow Pasque on 2020-04-05
Sorry, but the exhale encoder does not seem too exciting to me, given that it doesn't do less than 64kb stereo. I don't see any advantage over opus, especially when you factor in patent/licensing issues.

(From the exhale author):
> exhale starts only at 64 kbit/s stereo. xHE-AAC's advantage over its ancestors is much more obvious at rates lower than that. Adding the algorithms necessary for such low-rate coding would roughly triple the amount of source code and, possibly, work-hours (I like to write my source code from scratch and work on exhale in my free-time), and I won't be able to manage that. So I decided to leave the low rates to commercial encoders.

---

### Post by andrew.46 on 2020-04-05
> **Yellow Pasque said:**
> Sorry, but the exhale encoder does not seem too exciting to me, given that it doesn't do less than 64kb stereo. I don't see any advantage over opus, especially when you factor in patent/licensing issues.

It is very early days yet of course but it is exciting to get in *at the very beginning*, certainly exhale represents this for Open Source and for Linux...

---

### Post by andrew.46 on 2020-04-07
> **shantiq said:**
> You really are a wizard [...]

My real name perhaps should be Sparrowhawk :)

> Of course  you know what i am gonna say ?   ;)    :KS     ABCDE? to keep you busy in this odd phase :)

I no longer have access to a computer with a CD / DVD drive or indeed any audio CDs :(. However exhale could be added in easily enough by following the steps I previously used to put fhgaacenc into abcde but *omitting all mention of wine*. You could have a crack at it by opening up the script itself with your favourite text editor or if you like I could do it 'blind' *without testing* and you could be my tester.

Would be difficult from my end as I normally obsessively test and retest, not possible without an optical drive unfortunately...

---

### Post by andrew.46 on 2020-04-07
OK I have produced and early version of abcde with xHE-AAC encoding and tagging with AtomicParsley mostly for Shantiq but feel free to jump in! It is completely untested by me as I do not have an optical drive any more, however I know this section of the script well as I heavily developed this section for a few years!

What you need:

[LIST=1]
[*]A full installation of abcde, preferably from git
[*]AtomicParsley installed, preferably [from here...]("https://bitbucket.org/wez/atomicparsley/src/default/")
[*]A copy of exhale, instructions [here...]("https://askubuntu.com/a/1224199/57576")
[*]
[/LIST]

With all of that organised download the patched abcde and provided abcde.conf file that I have made available [here...]("http://www.andrews-corner.org/tmp/abcde_USAC_beta1.tar.gz"). To make everything safe it would be a great idea to back up your installed file:

```

sudo mv -v /usr/bin/abcde /usr/bin/abcde_bak
cp ~/.abcde.conf ~/.abcde.conf_bak

```

Then extract the archive from my web site and copy both files into the correct location:

```

sudo mv -v abcde /usr/bin/abcde
sudo chmod +x /usr/bin/abcde
cp abcde.conf ~/.abcde.conf

```

You will see a section in the supplied abcde.conf file that can be altered as you see fit:

```

# Specify your required encoding options here, exhale takes numerals
# here from 1 (about 64kbit/s) to 10 (about 192kbit/s):
EXHALENCOPTS="4" 

```

And cross your fingers :)

Restore your system if all is a disaster:

```

sudo mv -v /usr/bin/abcde_bak /usr/bin/abcde
mv ~/.abcde.conf_bak ~/.abcde.conf

```

And walk away :)

**Edit:** I have made a full diff against the git head that also includes the doc changes [here...]("http://www.andrews-corner.org/tmp/abcde_USAC.diff.gz") I had forgotten how much fun this is :)

---

### Post by shantiq on 2020-04-12
Just seen this Thanx Andrew will give it a whirl and report

---

### Post by shantiq on 2020-04-12
and yes Andrew direct hit



```
outputting to /home/shan/abcde.a20e740c/track02.wav

 (== PROGRESS == [                              | 046671 00 ] == :^D * ==)   


Done.




 echo Encoding track 02 of 12: Praise...
Encoding track 02 of 12: Praise...
encodetrack-m4a-02 nice -n 10 exhale 9 /home/shan/abcde.a20e740c/track02.wav /home/shan/abcde.a20e740c/track02.m4a


  ---------------------------------------------------------------------
 | exhale - ecodis extended high-efficiency and low-complexity encoder |
 |                                                                     |
 | version 1.0.2 (x64, built on Apr  5 2020) - written by C.R.Helmrich |
  ---------------------------------------------------------------------


 Encoding 44-kHz 2-channel 16-bit WAVE to low-complexity xHE-AAC at 192 kbit/s


 Progress: --------------------------------- Done, actual average 206.7 kbit/s


 Input statistics: Mobile loudness -20.25 LUFS,	sample peak level -2.11 dBFS


encodetrack-02 true
 echo Tagging track 02 of 12: Praise...
Tagging track 02 of 12: Praise...
tagtrack-m4a-02 nice -n 10 AtomicParsley /home/shan/abcde.a20e740c/track02.m4a --artist=Inner City --album=Praise --title=Praise --tracknum=02 --year=0 --genre=Techno --comment=xHE-AAC encoding --overWrite


 Started writing to temp file.
 Progress: =======================================================>100% |
 Finished writing to temp file.
tagtrack-02 true
movetrack-02 mv /home/shan/abcde.a20e740c/track02.m4a /home/shan/Music/m4a/Inner City-Praise/02.Praise.m4a
movetrack-output-m4a true




Finished.



```

---

### Post by shantiq on 2020-04-12
first full album tagged xHE-AAC


[[img]https://i.postimg.cc/XZfHhntf/f.png[/img]](https://postimg.cc/XZfHhntf)

---

### Post by andrew.46 on 2020-04-12
> **shantiq said:**
> and yes Andrew direct hit

Great news :). How does it feel to be the first person in the world to rip an audio CD to xHE-AAC?

---

### Post by shantiq on 2020-04-13
Very nice :] and thanx   I see you have submitted it to the abcde   so soon we can have it in the panoply   5 [correction: 7] aac codecs right ?

---

### Post by andrew.46 on 2020-04-13
> **shantiq said:**
> Very nice :] and thanx   I see you have submitted it to the abcde   so soon we can have it in the panoply   5 aac codecs right ?

I have not submitted the patch yet although I have left a message with Steve in #abcde to see if he is interested. Two things I guess:

[LIST=1]
[*]I am not sure if I still have *write access *to the git repository
[*]If I have I would probably not use it as I am no longer really one of the developers, etiquette dictates that I should not really just barrel in with a big patch that is not all that mainstream
[/LIST]

So if Steve is interested I will hopefully get the patch into abcde one way or the other. I am lurking on abcde tonight in the hope of catching him, you could join if you like: Freenode / #abcde ...

---

### Post by shantiq on 2020-04-13
Thanx for clarifications

---

### Post by andrew.46 on 2020-04-13
> **shantiq said:**
> Thanx for clarifications

I have just spoken to Steve on IRC and he has the git diff, hopefully he will like it and apply in the near future. Very exciting :)

---

### Post by shantiq on 2020-04-13
[https://ubuntuforums.org/showthread.php?t=2433697&p=13946264#post13946264](https://ubuntuforums.org/showthread.php?t=2433697&p=13946264#post13946264)   :D

---

### Post by andrew.46 on 2020-04-24
So for any who are interested in patching abcde for xHE-AAC encoding I have parked the patch against current git [here...]("http://www.andrews-corner.org/downloads/") pending its possible arrival in the abcde master.

---

### Post by andrew.46 on 2020-07-31
So it is a bit ugly but you can force Linux playback of USAC files generated by exhale with something like the following:

```

ffplay -hide_banner -loglevel 0 -autoexit -codec:a libfdk_aac test.m4a

```

Of course '-hide_banner -loglevel 0' are only intended to mask terminal spew but '-autoexit' seems to be required on my system at least to stop ffplay spinning along forever...

---

### Post by shantiq on 2020-07-31
> **andrew.46 said:**
> So it is a bit ugly but you can force Linux playback of USAC files generated by exhale with something like the following:

```

ffplay -hide_banner -loglevel 0 -autoexit -codec:a libfdk_aac test.m4a




```

Of course '-hide_banner -loglevel 0' are only intended to mask terminal spew but '-autoexit' seems to be required on my system at least to stop ffplay spinning along forever...

Cool will give it a spin later
We have hot weather here today Andrew so we are making the best of that &#128512;

EDIT tried but not got the latest ffmpeg so

```
ffplay version N-91586-g90dc584 Copyright (c) 2003-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/home/shan/ffmpeg_build --pkg-config-flags=--static --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --extra-libs='-lpthread -lm' --bindir=/home/shan/bin --enable-gpl --enable-libaom --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-openssl --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-nonfree
  libavutil      56. 18.102 / 56. 18.102
  libavcodec     58. 22.101 / 58. 22.101
  libavformat    58. 17.101 / 58. 17.101
  libavdevice    58.  4.101 / 58.  4.101
  libavfilter     7. 26.100 /  7. 26.100
  libswscale      5.  2.100 /  5.  2.100
  libswresample   3.  2.100 /  3.  2.100
  libpostproc    55.  2.100 / 55.  2.100
[aac @ 0x7fb1fc002f00] Audio object type 42 is not implemented. Update your FFmpeg version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7fb1fc000bc0] Failed to open codec in avformat_find_stream_info
[aac @ 0x7fb1fc002f00] Audio object type 42 is not implemented. Update your FFmpeg version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '01 Dream.m4a':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isom
    title           : dream
    artist          : manuel
    creation_time   : 2020-07-31T15:53:35.000000Z
  Duration: 00:30:31.47, start: 0.000000, bitrate: 189 kb/s
    Stream #0:0(und): Audio: aac (mp4a / 0x6134706D), 44100 Hz, 2 channels, fltp, 187 kb/s (default)
    Metadata:
      creation_time   : 2020-07-31T15:53:35.000000Z
      handler_name    : crh
[COLOR=#800000][aac @ 0x7fb1fc011d80] Audio object type 42 is not implemented. Update your FFmpeg version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
Failed to open file '01 Dream.m4a' or configure filtergraph[/COLOR]
```

---

### Post by andrew.46 on 2020-07-31
Mid winter here and I see a small heatwave over your way. Just remember that Australia laughs at your summer heat while Canada laughs at your winters :)

I see you have compiled against libfdk-aac but perhaps not the latest, I am using 2.01 here and this might be worth looking at. You did not give the command line that you used but I assume you used the vital: -codec:a libfdk_aac ?

---

### Post by shantiq on 2020-08-01
yea we have anaemic weather all year round so when we get a 32°C day [36° in London] we lap it up some of us do at least
most say: "God it is boiling" ; most English folks truly only like 8°C to 15°C and a drizzle all else foxes them :] 

Anyway so I used

```
ffplay  -codec:a libfdk_aac 01\ Dream.m4a
```

as the extra stuff return nowt


now off to [THE GUIDE]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu") will report when on the other side ....


Actually it gave me:

```
sudo apt-get install libfdk-aac-devReading package lists... Done
Building dependency tree       
Reading state information... Done
libfdk-aac-dev is already the newest version (0.1.6-1).
```

but anyway reinstalled entire Ffmpeg and most codecs were already up-to-date

Also threw interesting [kink]("https://askubuntu.com/questions/1252997/unable-to-compile-ffmpeg-on-ubuntu-20-04") but this fixed it


So now:

```
ffmpegffmpeg version N-98601-g134a48a Copyright (c) 2000-2020 the FFmpeg developers
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
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...



```


and now it plays with your full line

[[IMG]https://i.postimg.cc/fJtNhyJ7/1.png[/IMG]]("https://postimg.cc/fJtNhyJ7")


although only [in case wondering] :


```
dpkg -l libfdk-aac-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                 Version      Architecture Description
+++-====================-============-============-====================================================
ii  ***libfdk-aac-dev:amd64 0.1.6-1***      amd64        Fraunhofer FDK AAC Codec Library - development files
```

---

### Post by shantiq on 2020-08-01
But no exe for xHE-AAC as yet it seems

---

### Post by andrew.46 on 2020-08-01
> **shantiq said:**
> But no exe for xHE-AAC as yet it seems

I believe you might find some joy [here...]("https://www.rarewares.org/aac-encoders.php")

---

### Post by shantiq on 2020-08-01
ha cool

---

### Post by andrew.46 on 2020-08-01
I confess that I could not warm to EAC but I knew that you were a big user :). As for fdkaac.exe my memory was finally jogged and if you ever want to go a little deeper into the rabbit hole I have published a page a while back demonstrating how to cross compile fdkaac for Windows on a linux platform using MXE. The distro used is actually Slackware but the principles would be the same for Ubuntu:

[https://www.andrews-corner.org/mxe.html](https://www.andrews-corner.org/mxe.html)

This way you can 'roll your own' without waiting for somebody to provide an updated copy. Mind you Slackware makes it all very easy...

---

### Post by shantiq on 2020-08-01
thanx will definitely try this


PS   i do use slackware on my older machine too and worship it but Ubuntu still on my main and will try on U


EDIT


tried the guide on MXE on Ubuntu and rolled my own fdkaac.exe 32 bit for my EAC [tried stupidly 20 times with the downloaded one only to finally realize it was a 64-bit der!]
AS all your guides worked a treat 
Thanx



on EAC

```
-p 29 -b 39 -a
```   gives you a 


```
Writing application                      : fdkaac 1.0.0, libfdk-aac 4.0.0, CBR 38kbps

Audio
ID                                       : 1
Format                                   : AAC LC SBR PS
Format/Info                              : Advanced Audio Codec Low Complexity with Spectral Band Replication and Parametric Stereo
Commercial name                          : **HE-AACv2**



```

happy with that

---

### Post by andrew.46 on 2020-08-02
> **shantiq said:**
> [...]tried the guide on MXE on Ubuntu and rolled my own fdkaac.exe 32 bit for my EAC
AS all your guides worked a treat  [...]

That is excellent news :). My colleagues on HydrogenAudio have demonstrated that binaries compiled as native Windows applications using Windows compilers tend to be *a little faster *than the binaries produced by MXE from a native Linux host. But there is a greater joy in rolling your own Windows executables for sure, rather than trustingly downloading somebody else's efforts, and MXE can be a lot of fun!

Good to hear that EAC is firing ahead with your fdkaac.exe, you certainly are the source of knowledge on EAC running on Linux. There appears to still be audio CDs and interest in them in places, it will be sad when this technology has slowly faded away. My own investment of time and effort in audio CDs has decreased somewhat but I have recently purchased a USB3 external DVD burner so that I can experiment a little with exhale and abcde. Not out of the box yet but next rainy weekend I will start at it.

And as an aside: it is good to talk to you again! UbuntuForums seems to have subsided a little from busier days but it is nice to 'see' old friends again :)

---

### Post by shantiq on 2020-08-03
> [COLOR=#000000]native Windows applications using Windows compilers tend to be [/COLOR]*a little faster than the binaries produced by MXE from a native Linux host*

Fair dues ;)



> **andrew.46 said:**
> 

And as an aside: it is good to talk to you again! UbuntuForums seems to have subsided a little from busier days but it is nice to 'see' old friends again :)


Totally. Not sure what happened. It all went dead[-ish] at one point. Was more vibrant a few years ago it seems

Thanx for all the tips Andrew

shan


PS   and yes under Wine all these currently active :)

[[IMG]https://i.postimg.cc/8sdGPYbs/Screenshot-from-2020-08-03-11-50-41.png[/IMG]]("https://postimg.cc/8sdGPYbs")

---

### Post by andrew.46 on 2021-03-09
I have just now updated the xHE-AAC patch to cover the latest git abcde and tested it all out and it ran very, very nicely! Also I have added an ~/.abcde.conf file for xHE-AAC:

~/.abcde.conf for AAC: Exhale
[https://www.andrews-corner.org/abcde/abcde_aac.html#exhale](https://www.andrews-corner.org/abcde/abcde_aac.html#exhale)

My colleagues on hydrogenaudio tell me that playback under Linux is possible with RhythmBox  if gstreamer plugin is compiled against fdkaac. I have not tried this as I am not really a GStreamer sort of guy, still waiting for FFmpeg to come to the party.

I am aware that my enthusiasm for exhale and xHE-AAC encoding is not widespread, but I still feel that it is so exciting to get in at the beginning with Open Source xHE-AAC encoding :).

---

### Post by shantiq on 2021-03-09
> **andrew.46 said:**
> I have just now updated the xHE-AAC patch to cover the latest git abcde and tested it all out and it ran very, very nicely! Also I have added an ~/.abcde.conf file for xHE-AAC:

~/.abcde.conf for AAC: Exhale
[https://www.andrews-corner.org/abcde/abcde_aac.html#exhale](https://www.andrews-corner.org/abcde/abcde_aac.html#exhale)

My colleagues on hydrogenaudio tell me that playback under Linux is possible with RhythmBox  if gstreamer plugin is compiled against fdkaac. I have not tried this as I am not really a GStreamer sort of guy, still waiting for FFmpeg to come to the party.

I am aware that my enthusiasm for exhale and xHE-AAC encoding is not widespread, but I still feel that it is so exciting to get in at the beginning with Open Source xHE-AAC encoding :).


thanx Andrew will give it a whirl :KS

---

### Post by andrew.46 on 2021-03-09
> **shantiq said:**
> thanx Andrew will give it a whirl :KS

Interestingly enough it looks like the next version of Ubuntu has already done this:

[https://packages.ubuntu.com/hirsute/gstreamer1.0-fdkaac](https://packages.ubuntu.com/hirsute/gstreamer1.0-fdkaac)

---

### Post by shantiq on 2021-03-09
Oh no not there yet ....    what am i to do with the patch? I probably did not understand what it is i should do with it Andrew :KS


this is what i did         ```
sudo chmod +x abcde_USAC.diff
```   then ```
sudo mv abcde_USAC.diff /usr/bin
``` 

clearly not the right thing to do ....    do i need to copy parts of the patch into /usr/bin/abcde    ...    that does not seem right either ....   please kindly enlighten 

my version of abcde is abcde v2.9.4-DEV.

#whatdididowrongthistime ? :KS

---

### Post by andrew.46 on 2021-03-09
If you modified abcde before (by patching for exhale) there is nothing more required, the newer patch does not add anything different than the previous patch, just lines are changed to follow git head.

If you are using the latest version of exhale you might want to experiment with the newer presets:

```

 preset	=  # (0-9)  low-complexity standard compliant xHE-AAC at 16*#+48 kbit/s
 	     (a-g)  low-complexity compliant xHE-AAC with SBR at 12*#+36 kbit/s


```

I have not looked at the [SBR]("https://en.wikipedia.org/wiki/Spectral_band_replication") options yet. Neither have a I looked at the options for LUFS and dBFS in part because I have no idea what these options even mean :)

---

### Post by shantiq on 2021-03-10
Hi Andrew you may have thought i knew how to do this but i have never added a patch before :KS  so the way to do this is

```
[COLOR=#111111][FONT=Consolas]patch [options] originalfile patchfile [/FONT][/COLOR]
```


which gives me here

```
sudo patch  /usr/bin/abcde /home/shan/Desktop/abcde_USAC.diff [sudo] password for shan: 
patching file /usr/bin/abcde
Hunk #1 FAILED at 327.
1 out of 1 hunk FAILED -- saving rejects to file /usr/bin/abcde.rej
patching file /usr/bin/abcde
patching file /usr/bin/abcde
Hunk #1 FAILED at 357.
Hunk #2 FAILED at 429.
Hunk #3 FAILED at 441.
3 out of 3 hunks FAILED -- saving rejects to file /usr/bin/abcde.rej
patching file /usr/bin/abcde
Hunk #1 FAILED at 67.
Hunk #2 FAILED at 153.
Hunk #3 FAILED at 166.
Hunk #4 FAILED at 275.
Hunk #5 FAILED at 298.
5 out of 5 hunks FAILED -- saving rejects to file /usr/bin/abcde.rej



```

Then it is seen

```




 echo Encoding track 02 of 99: Re-Rewind...
Encoding track 02 of 99: Re-Rewind...
encodetrack-m4a-02 nice -n 10 exhale 5 /home/shan/abcde.30115163/track02.wav /home/shan/abcde.30115163/track02.m4a


  ---------------------------------------------------------------------
 | exhale - ecodis extended high-efficiency and low-complexity encoder |
 |                                                                     |
 | version 1.0.2 (x64, built on Apr  5 2020) - written by C.R.Helmrich |
  ---------------------------------------------------------------------


 Encoding 44-kHz 2-channel 16-bit WAVE to low-complexity xHE-AAC at 128 kbit/s


 Progress: --------------------------------- Done, actual average 143.8 kbit/s


 Input statistics: Mobile loudness -16.62 LUFS,    sample peak level -0.50 dBFS


encodetrack-02 true
 echo Tagging track 02 of 99: Re-Rewind...
Tagging track 02 of 99: Re-Rewind...
tagtrack-m4a-02 nice -n 10 AtomicParsley /home/shan/abcde.30115163/track02.m4a --artist=Artful Dodger --album=It&#8217;s All About the Stragglers --title=Re-Rewind --tracknum=02 --year=2000 --genre= --comment=abcde version 2.8.1 --overWrite


 Started writing to temp file.
 Progress: ======================================================> 99% -|
 Finished writing to temp file.
tagtrack-02 true
movetrack-02 mv /home/shan/abcde.30115163/track02.m4a Music/m4a/Artful Dodger-It&#8217;s All About the Stragglers/02.Re-Rewind.m4a
Finished.



```





Thanx for this addition Andrew ....    you wizard




============

my AAC .abcde.conf now looks thus

```
# ALL THE AAC SHENANIGANS RIGHT HERE :]

# IF YOU WANT AN ALAC FILE CHANGE NEXT LINE  from fdkaac/exhale to qaac 


AACENCODERSYNTAX=exhale
#FDKAAC=fdkaac


# Specify the encoder to use for m4a/aac. Exhale is the only Open Source
# xHE-AAC encoder available under native Linux at the moment:

EXHALE="exhale"
EXHALENCOPTS="9"

QAAC="$HOME/.wine/drive_c/qaac/qaac.exe"
QAACENCOPTS="--alac" 

OUTPUTTYPE="m4a"

# Output type for alac:
OUTPUTTYPE="m4a"


# For fdkaac options see 'fdkaac --help' THIS HERE BELOW WILL GIVE YOU A HE-AACv2 FILE
FDKAACENCOPTS='-p 29  -b 38000 -I' 

###############end of AAC################
```



PS2:   did look at the possibility of using RhythmBox which i really do not rate anyway but looking at Gstreamer for fdkaac on Ubuntu 20.04.2 LTS is a total headfork as it runs 16 version and this newfangled toy runs on 18 version so will wait to test meantimes still totally fine through this free software arguably the best in any OS anyway


[[img]https://i.postimg.cc/mhtsqkLx/1.png[/img]](https://postimg.cc/mhtsqkLx)

---

### Post by Yellow Pasque on 2021-03-10
You need the latest abcde git for the patch to apply properly:

```
cd <whatever directory you want abcde source in>
git clone https://git.einval.com/git/abcde.git
cd abcde/
cp <path to abcde_USAC.diff> .
patch -p1 < abcde_USAC.diff
```

---

### Post by shantiq on 2021-03-10
> **Yellow Pasque said:**
> You need the latest abcde git for the patch to apply properly:

```
cd <whatever directory you want abcde source in>
git clone https://git.einval.com/git/abcde.git
cd abcde/
cp <path to abcde_USAC.diff> .
patch -p1 < abcde_USAC.diff
```


Thanx YP   was already [sorted]("https://ubuntuforums.org/showthread.php?t=2433697&p=14025313#post14025313")  :KS

---

### Post by Yellow Pasque on 2021-03-10
Maybe you need to:
```
git pull
```

---

### Post by andrew.46 on 2021-03-10
Hopefully all is sorted? If not I have placed my fully patched up abcde here for a short time:

[https://www.andrews-corner.org/tmp/abcde](https://www.andrews-corner.org/tmp/abcde)

This can actually be placed in $HOME/bin and after reboot (or sourcing appropriate ~/.bash*** file) should trump the system abcde.

BTW might be worth updating your copy of exhale, the SBR, loudness and peak sample adjustments can be seen in later releases. I have updated the AskUbuntu post that deals with this here:

[https://askubuntu.com/q/1224198/57576](https://askubuntu.com/q/1224198/57576)

---

### Post by andrew.46 on 2021-03-10
> **shantiq said:**
> 

PS2:   did look at the possibility of using RhythmBox which i really do not rate anyway but looking at Gstreamer for fdkaac on Ubuntu 20.04.2 LTS is a total headfork as it runs 16 version and this newfangled toy runs on 18 version so will wait to test meantimes still totally fine through this free software arguably the best in any OS anyway

I am retired now so I might take some time to download an iso of the Hirsute Hippo and have a go with the fdkaac gstreamer and see if I can coax xHE-AAC playback out of RhythmBox. I am also not a great fan of this but it will be an interesting exercise :)

**Edit:** Looks like RhythmBox and Clementine both successfully play xHE-AAC files after installation of the fdkaac gstreamer libraries. Exciting times ahead! I could not coax either application to display details of the codecs being played, any ideas?

---

### Post by andrew.46 on 2021-03-10
So after some fiddling around I can see that playback of xHE-AAC will be possible in most players that use Ubuntu's gstreamer1.0-fdkaac package. The most satisfactory of these applications for me was Quod Libet, an application that I have not met before. I also tested RhythmBox and Clementine and while both worked I could not warm to either application :(.

I attach a screenshot of Quod Libet playing back xHE-AAC files ripped by abcde from my single remaining audio CD (don't judge me by this album!). Further playback possibilities [here...]("https://hydrogenaud.io/index.php?topic=118888.msg994653#msg994653")

---

### Post by shantiq on 2021-04-09
--

---

### Post by shantiq on 2021-04-09
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288091&stc=1&thumb=1&d=1615433701[/IMG] 
  [mission totally accomplished ]("https://ubuntuforums.org/showthread.php?t=2433697&p=13919327#post13919327")Andrew ;) 
and thank you

---

### Post by andrew.46 on 2021-04-10
Nice to see some closure to a thread that started some time ago :). My ears are not good for such things but I am impressed by the quality of the audio produced by exhale. Exciting to be involved too (on [Slackware]("https://slackbuilds.org/repository/14.2/audio/exhale/") and [Ubuntu]("https://askubuntu.com/q/1224198/57576")) in the early stages of development.

---

