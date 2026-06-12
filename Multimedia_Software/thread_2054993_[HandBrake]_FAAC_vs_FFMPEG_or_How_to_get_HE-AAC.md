---
title: "[HandBrake] FAAC vs FFMPEG or: How to get HE-AAC?"
date: 2012-09-08
forum: Multimedia Software
---

### Post by MrsUser on 2012-09-08
I use HandBrake to convert my DVDs to MKV. Have no problem with the video settings, but audio codecs offered by HandBrake settings are confusing to me.

There are two entries for AAC to choose from, faac or ffmpeg. I wonder which one is better. Also, which faac version is this? And does it use CBR or VBR? On the HandBrake wiki there is unfortunately zero information about this.

Also, I wonder if there is any possiblity to encode to HE-AAC (AAC+) in HandBrake under Ubuntu. I know for Mac OS X that HE-AAC is available. Probably not in Ubuntu. And if so, then how can I convert the audio track to  HE-AAC in Ubuntu? I know there is a CLI binary for NeroAAC for Linux. But is there a GUI?

And if I use faac in HandBrake, is 64kbps enough for a movie? Because I cannot hear any difference to the default setting of 160kbps. So far, I thought one could have the same quality with a 64kbps aac file as with a 128kpbs mp3 file -- at least for he-aac. But what version/implementation of aac is actually used in HandBrake, and what quality delivers it?

Could really need some help here. I'd like to use HE-AAC for my MKV audio tracks. Or at least AAC with reasonable quality at lowest possible file size.

Can HandBrake be 'pimped' with more codecs? If not, is there any GUI solution for Nero's CLI? Or any solution with WINE?

---

### Post by ron999 on 2012-09-08
> **MrsUser said:**
> I know there is a CLI binary for NeroAAC for Linux. But is there a GUI?
... is there any GUI solution for Nero's CLI? Or any solution with WINE?

Hi
When you've put **neroAacEnc** (CLI) in usr/local/bin folder... **DeaDBeeF** can be used as a GUI with Ubuntu.
PPA is here---> [https://launchpad.net/~alexey-smirnov/+archive/deadbeef]("https://launchpad.net/~alexey-smirnov/+archive/deadbeef")

Also **neroAacEnc.exe** can be used with **foobar2000** as a GUI with Ubuntu + WINE.

---

### Post by MrsUser on 2012-09-08
Thanks. I had a look, but isn't Deadbeef just an audio player?

I fiddled with the CLI of Nero now. And I wonder if I could use WinFF as a GUI?!

---

### Post by ron999 on 2012-09-08
> **MrsUser said:**
> ... but isn't Deadbeef just an audio player 
No, **DeaDBeeF** has a _convert_ option. :p
Screenshot attached.

Load the track(s) and right-click > Convert > Choose an encoder.
Command line for Nero is like this:- 
```
neroAacEnc -q 0.5 -ignorelength -if - -of %o
```
> **MrsUser said:**
> ... I wonder if I could use WinFF as a GUI?!
I don't think so. :(

Your questions about **HandBrake**...

It uses **faac**.
With HandBrake GUI it's probably CBR.

The other aac option is **AAC(ffmpeg)**.
I suppose this uses FFmpeg's own aac encoder.

Probably **faac** is the best choice of the two. ;)

HandBrake documentation says:-
> HandBrake does not support external encoders. It is not possible to add an encoder to HandBrake at runtime. All the encoder libraries are built in and not dynamically linked/loaded at runtime.

---

### Post by MrsUser on 2012-09-09
The info was very helpful. Thanks a lot!

---

### Post by qyot27 on 2012-09-09
While I'm not currently at liberty to test this, it may be possible to use qtaacenc or qaac under Wine to access the AAC encoder that ships with Quicktime/iTunes (qaac only relies on the Apple Application Support rather than the full package).  There is at least some support for Quicktime or its components under Wine, but I'm not sure how well or if it extends to making the encoder stable.

This is relevant to the discussion seeing as the Quicktime AAC encoder is on the same level as Nero or actually superior to it now according to ABX tests (I never really liked Nero myself, so I've been using the Quicktime encoder as my go-to for 8+ years now).

---

### Post by ron999 on 2012-09-09
> **qyot27 said:**
> ... it may be possible to use qtaacenc or qaac under Wine to access the AAC encoder that ships with Quicktime/iTunes (qaac only relies on the Apple Application Support rather than the full package)...
Yes, **qaac.exe** (with qt bits and pieces) seems to run OK with WINE.
And foobar2000 can act as a GUI. ;)

> [SIZE="1"]Writing application : qaac 1.40, CoreAudioToolbox 7.9.7.9, AAC-LC Encoder, ABR 320kbps, Quality 96[/SIZE]

> [SIZE="1"]Writing application : qaac 1.40, CoreAudioToolbox 7.9.7.9, Apple Lossless Encoder[/SIZE]

---

### Post by shantiq on 2012-09-09
ok just answering this specific question  >  How to get HE-AAC?


and thanx for asking as the answer is yes   and at 64kbps it has incredibly good sound quality and plays on all player i have tried  [mplayer vlc deadbeef xmms  ....]

[URL="http://www.ubuntuupdates.org/package/medibuntu_free/natty/free/base/aacplusenc"][B]
all from here[/B][/URL]


to install and use see below  in red all the code for terminal


> 


[http://www.ubuntuupdates.org/package/medibuntu_free/natty/free/base/aacplusenc](http://www.ubuntuupdates.org/package/medibuntu_free/natty/free/base/aacplusenc)


**to download deb**

[ATTACH]223953[/ATTACH]

**[COLOR="DarkRed"]wget with link from the main page above[/COLOR]**







**to install deb**

shantiq@0000000000000:~$ [COLOR="DarkRed"]sudo dpkg -i aacplusenc_0.17.5-0.0medibuntu1_amd64.deb[/COLOR]
Selecting previously unselected package aacplusenc.
(Reading database ... 377687 files and directories currently installed.)
Unpacking aacplusenc (from aacplusenc_0.17.5-0.0medibuntu1_amd64.deb) ...
Setting up aacplusenc (0.17.5-0.0medibuntu1) ...
Processing triggers for man-db ...


**to convert wav to he-aac**


00000:~$ [COLOR="DarkRed"]aacplusenc Age.wav Age.aac 64000  s[/COLOR]
input file Age.wav: 
sr = 44100, nc = 2 fmt = 1

output file Age.aac: 
br = 64000 inputSamples = 4096  maxOutputBytes = 1543 nc = 2 m = 0

[3502]

encoding finished
shantiq@shantiq-00000000000000000000000:~/Desktop/Taller$ mediainfo Age.aac
General
Complete name                            : Age.aac
Format                                   : ADTS
Format/Info                              : Audio Data Transport Stream
File size                                : 1.26 MiB

Audio
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format version                           : Version 2
Format profile                           [B][COLOR="DarkRed"]: HE-AAC / LC
Bit rate mode                            : Constant / Variable
Bit rate                                 : 63.9 Kbps
Minimum bit rate                         : 122 Kbps
Maximum bit rate                         : 204 Kbps[/COLOR][/B]
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 1.26 MiB (100%)



   ** NJOI**   corking format   1.26 MiB   on a 2:42 mn

---

### Post by MrsUser on 2012-09-10
Wonderful! Now there are even two choices for a HE-AAC encoder. The only thing I'm missing is info on [B]how to mix down  6-ch (5.1) AC3 to 2-ch Stereo HE-AAC?

[/B]I couldn't find any wiki or documentation for the two encoders. Or do I need to do the mixdown first and then give the result as input to the HE-AAC encoder? I know I can use a pipe, so I don't have to write an intermediary wav-file. But does anyone know what the command line must be like for a mixdown to Stereo?

Also, when I use ffmpeg for converting ac3 to aac in terminal, e.g.:
```
ffmpeg -i input.ac3 -f wav - | neroAacEnc -br 48000 -if - -ignorelength -of output.mp4
```then I get the following message:
```
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[ac3 @ 0xbbc9c0] max_analyze_duration reached
[ac3 @ 0xbbc9c0] Estimating duration from bitrate, this may be inaccurate
```Don't know if ffmpeg produces some faulty file there?! Anyway, it played fine. So I suppose the output was ok.

What bothers me though is that with the removal of ffmpeg I'd have to learn how to use avconv. And I can't find an easily understandable wiki/info about it. It has so many options that it confuses me ("avconv -help" presents an endless list of switches).

---

### Post by shantiq on 2012-09-10
Hi Mrs   you can do that conversion


```
ffmpeg -i "file.ac3"   -acodec libaacplus -ab 64k -ac 2 "file.aac"
```



but will need to equip yourself with libaacplus first   see **[here]("http://ubuntuforums.org/showthread.php?t=2055916")**

---

### Post by MrsUser on 2012-09-10
Thanks so much!

Also, meanwhile, I figured how to do it with NeroAacEnc via pipe and ffmpeg. For those who are interested:

```
ffmpeg -i input.ac3 -f wav -ac 2 - | neroAacEnc -q 0.4 -if - -ignorelength -of output.mp4
```I usually choose quality 0.4 for Nero AAC encoder.

However, the direct usage of the libaacplus seems just more elegant. But I don't know if the quality is on par with the Nero encoder. Would really be interested which is superior, Nero or the libaacplus.

---

### Post by shantiq on 2012-09-10
both great quality compared to faac and faad  but of course libaacplus  wins hands down   when you can rip a whole album to 22MB   and have sound quality which to my ears  is north of mp3 320k.........  nero is amazing on quality of sound but you still have the big size for a lossy file

my input for what it's worth:KS

---

### Post by qyot27 on 2012-09-10
> **MrsUser said:**
> ```
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[ac3 @ 0xbbc9c0] max_analyze_duration reached
[ac3 @ 0xbbc9c0] Estimating duration from bitrate, this may be inaccurate
```Don't know if ffmpeg produces some faulty file there?! Anyway, it played fine. So I suppose the output was ok.

What bothers me though is that with the removal of ffmpeg I'd have to learn how to use avconv. And I can't find an easily understandable wiki/info about it. It has so many options that it confuses me ("avconv -help" presents an endless list of switches).
Those ac3 messages aren't really errors or warnings, so you don't have to worry about them, especially if the output is okay.

The 'removal' part is just a political squabble that's taking place between [FFmpeg](http://ffmpeg.org) and its [fork](http://libav.org).  Debian (and therefore Ubuntu) took sides with the fork.  FFmpeg itself is not deprecated, and the removal only refers to the distro supplying the ffmpeg binary (for legacy/compatibility reasons) with the fork's libraries and binaries.

If you would prefer to actually use *FFmpeg*, you have to build it yourself (well, maybe someone's got a PPA for it, but I don't pay attention since I just build my own).  [This thread](http://ubuntuforums.org/showthread.php?t=786095) was the go-to guide for doing so, but is now hosted on FFmpeg's wiki.  Discussion still continues on that thread, though.

---

### Post by MrsUser on 2012-09-11
Very good info from you guys! Thank you all so much for your kind help!  Now I really know what to do :)

And I'm glad to find out that these 'error messages' are nothing to worry about. And yes, the output files were fine. However, if ffmpeg is abandoned by Ubuntu, I'll do their switch as well. So I have to dig a bit for avconv guidelines. If it's a fork, perhaps the command lines will just stay the same, except for the name change from ffmpeg to avconv. That'd be convenient.

As for the libaacplus, I will make some personal listening testing. A whole album compressed to 22MB is really amazing if the sound quality is still good then. Personally, I don't hear any difference between a 128kbps mp3 and a 320kbps mp3, for instance. So I guess the libaacplus will produce results that are sufficient for me anyway.

---

### Post by MrsUser on 2012-10-02
I have found a very nice Open Source software (with GUI) that is available for Linux too. It's called Free Audio Converter or fre:ac (former BonkEnc) and it is able to use external encoders, thus it can also use Nero's CLI (NeroAacEnc):

[http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php](http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php)

To have Nero encoder available as CLI in terminal, you have to put it in usr/bin and make it executable:

```
sudo cp neroAacEnc /usr/bin
cd /usr/bin
sudo chmod +x neroAacEnc
```additionally you should also copy Nero's AAC tag tool there:

```
sudo cp neroAacTag /usr/bin
cd /usr/bin
sudo chmod +x neroAacTag
```Then open terminal to test if Nero encoder is there and see all available options for usage:

```
neroAacEnc -help
```

In case it says it can't find the file, then you're obviously running a 64-bit system. But the Nero encoder is 32-bit. To fix it, install:

 ```
sudo apt-get install lib32stdc++6
```

In many cases this is not needed, as other software might have installed this dependency already. But on a fresh install of 64-bit Ubuntu, Nero will not work unless you install this dependency.

If you have neroAacEnc already in your usr/bin directory, fre:ac will automatically find it and provide it as an encoder option. 
Alternatively, you can also put the neroAacEnc in fre:ac's directory under codecs > cmdline (and you have to make it executable of course; just right-click the file, choose properties and under 'Permissions' check 'Allow executing file as program'):

[IMG]http://i.imgur.com/U9BCa.jpg[/IMG]

Project's official homepage:
[http://www.freac.org/](http://www.freac.org/)

Linux snapshots vailable here, for both 32-bit and 64-bit:
[https://sourceforge.net/projects/bonkenc/](https://sourceforge.net/projects/bonkenc/)

The binaries work out of the box  in Ubuntu 12.04.

[IMG]http://i.imgur.com/EdNpg.jpg[/IMG]

---

### Post by digitall.doc on 2012-10-14
Sorry for asking in a 'solved' thread...

When I try to run freac, I get this error:

```
./freac: error while loading shared libraries: libbz2.so.1.0: cannot open shared object file: No such file or directory

```

Any clues?

I'm running Linux Mint KDE, Ubuntu 12.04 inside.
I verified I've got libbz2 1.0 installed.

(I hope Mint is not a problem to post here. I learnt all about linux here...)

---

### Post by shantiq on 2012-10-14
Hi doc   well you may have libbz2-1.0 missing


and it is [**here**]("http://pkgs.org/ubuntu-11.04/ubuntu-main-i386/libbz2-1.0_1.0.5-6ubuntu1_i386.deb.html") for 64 and 32  install it and try again maybe


or   > sudo apt-get install libbz2-1.0

---

### Post by digitall.doc on 2012-10-14
Hi shantiq,
yes, I already had libbz2-1.0 installed...

...but I had downloaded the wrong 32bit fre:ac version. :oops:  #-o ](*,)

Now, with the fre:ac 64bit version, it starts OK.

I will try it working.

Thanx

---

### Post by MrsUser on 2012-10-14
> **digitall.doc said:**
> Hi shantiq,
yes, I already had libbz2-1.0 installed...

...but I had downloaded the wrong 32bit fre:ac version. :oops:  #-o ](*,)

Now, with the fre:ac 64bit version, it starts OK.

I will try it working.

Thanx

Yeah, on the download site clicking the large green button downloads the 32-bit version. For 64-bit people have to click that little link 'Browse all files' to see the 64-bit snapshots too:

[http://sourceforge.net/projects/bonkenc/files/snapshots/](http://sourceforge.net/projects/bonkenc/files/snapshots/)

---

### Post by shantiq on 2012-10-15
as regards the whole he-aac rip/conversion thing    freac is good too   and thanx   never knew of it before   [does not rip for me tho gets stuck and freezes at cddb stage]


if you want a simple solution and you can handle basic german [it is only in German]   there is also

[**Plattenkiste**]("http://www.dieplattenkiste.de/downloads/Plattenkiste255_2_PHBW.exe")  under Wine

 it will rip very well to HE-AAC   [all codecs are in the program]


 see image for guidance

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225122&d=1349471049[/IMG]

---

### Post by andrew.46 on 2012-12-26
> **ron999 said:**
> Yes, **qaac.exe** (with qt bits and pieces) seems to run OK with WINE.

I am looking at running qaac under wine but I am a little lost with the required 'Apple Application Support' that is required. How did you work around this?

---

### Post by shantiq on 2012-12-26
hi Andrew from this [**link**]("http://audiophilesoft.ru/commandline/qaac/qaac_1.46_CoreAudioToolbox_7.9.8.1.7z") go into qaac and run wine qaac  works well here

---

### Post by ron999 on 2012-12-26
> **andrew.46 said:**
> ...'Apple Application Support' that is required. How did you work around this?
Hi
In my foobar2000 > components directory there is a folder "qaac".
I downloaded the bits and pieces from www, but not sure where from.
Can't remember.:confused:

---

### Post by qyot27 on 2012-12-26
> **andrew.46 said:**
> I am looking at running qaac under wine but I am a little lost with the required 'Apple Application Support' that is required. How did you work around this?
Download the iTunes or Quicktime installer, unpack the .exe (7za might be able to do this, since 7zip proper can do it under Windows), and use the Application Support .msi installer.  Or so I would guess (I use qtaacenc, which needs full Quicktime - I've also never tried it under Wine, IIRC).  Considering you can install iTunes under Wine, it should have the ability to install the Application Support package only.

---

### Post by andrew.46 on 2012-12-26
Seems ok although I am not a keen wine user:

[http://www.andrews-corner.org/samples/luckynight.m4a](http://www.andrews-corner.org/samples/luckynight.m4a)

BTW new version of qaac out...

**Edit:** So others can critique here is the commandline I used:

```

wine qaac luckynight.wav -c 64 -r keep --he \
    --album "Treasure Quest Soundtrack" --title "Lucky Night" \
    --track "9" --artist "Jody Marie Gnant" --genre "Soundtrack" \
    --comment "1-minute song sample demonstrating HE_AAC encoding with qaac." \
    -o luckynight.m4a

```

And the completed file is as follows:

```

andrew@skamandros~/media$ mediainfo luckynight.m4a 
General
Complete name                            : luckynight.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 480 KiB
Duration                                 : 1mn 0s
Overall bit rate mode                    : Variable
Overall bit rate                         : 64.9 Kbps
Album                                    : Treasure Quest Soundtrack
Track name                               : Lucky Night
Track name/Position                      : 9
Performer                                : Jody Marie Gnant
Genre                                    : Soundtrack
Encoded date                             : UTC 2012-12-26 23:27:38
Tagged date                              : UTC 2012-12-26 23:27:41
Writing application                      : qaac 2.10, CoreAudioToolbox 7.9.8.1, AAC-HE Encoder, CBR 64kbps, Quality 96
Comment                                  : 1-minute song sample demonstrating HE_AAC encoding with qaac.

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : HE-AAC / LC
Codec ID                                 : 40
Duration                                 : 1mn 0s
Bit rate mode                            : Variable
Bit rate                                 : 64.0 Kbps
Maximum bit rate                         : 69.0 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz / 22.05 KHz
Compression mode                         : Lossy
Stream size                              : 474 KiB (99%)
Encoded date                             : UTC 2012-12-26 23:27:38
Tagged date                              : UTC 2012-12-26 23:27:41

```

Now that I have setup a bash alias for running wine + qaac it does not even look like I am using wine at all :)

---

### Post by andrew.46 on 2012-12-27
So to get HE-AAC with qaac from *any* file the following commandline should work:

```

ffmpeg -i <input.file> -f wav - | \
       qaac -c 64 -r keep --he - -o <output.m4a>

```

But I have used a bash alias:

```

alias qaac='wine ~/.wine/drive_c/Program\ Files/qaac/x86/qaac.exe'

```

just to make things a little simpler :) Now to assemble the libsndfile extras for qaac....

---

