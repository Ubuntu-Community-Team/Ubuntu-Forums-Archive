---
title: "No Audio with output videos from OpenShot(and others)"
date: 2014-10-20
forum: Multimedia Software
---

### Post by frank75 on 2014-10-20
I've used OpenShot as my basic video editor for some time under Manjaro and it always worked fine.  Now with Ubuntu MATE' I get no audio on my edited videos with OpenShot and also Kdenlive gave no audio either.  I've installed the extras(Blender and there was one other that slips my mind right now) with OpenShot. The videos have sound from the download and have sound in OpenShot if played but the exported vids have no sound what so ever. I've looked around on the interweb for the answer with none being found so now I"m asking the forum. Is there some other audio codec or something that I need to install with VLC to get video working with the exported OpenShot vids or what? Thanks.

---

### Post by frank75 on 2014-10-20
Anyone? I'm going to do a Kali install on an external SSD drive that I have and then install OpenShot and see if it'll work there. If it does then it's got to be something about Ubuntu that's not letting the audio transfer out to the project, if it doesn't work under Kali then it'll have to be something to to with OpenShot. Either way I'd like to figure this out.

---

### Post by frank75 on 2014-10-21
Well, I edited some videos in Kali with OpenShot and still had sound after edit. Transfered the vids to Ubuntu MATE' and still had sound so it must be something about OpenShot within Ubuntu MATE' that's the issue and not OpenShot per say.

---

### Post by Rob Sayer on 2014-10-21
It may be a codec issue in ubuntu.  Have you installed ubuntu-restricted-extras?

VLC and some other media apps like SMplayer install with their own codec libraries, so that shouldn't affect VLC playback.

---

### Post by frank75 on 2014-10-21
> **Rob Sayer said:**
> It may be a codec issue in ubuntu.  Have you installed ubuntu-restricted-extras?

VLC and some other media apps like SMplayer install with their own codec libraries, so that shouldn't affect VLC playback.

I was thinking the same thing but wasn't sure what to install to fix the issue. I'll see about installing Ubuntu Restricted Extras and see if that'll resolve the problem. Thanks.

---

### Post by frank75 on 2014-10-21
Well, that didn't help. I don't understand it. I can edit a video under Kali and move it to my Ubuntu MATE home folder then open Ubuntu MATE and it works perfectly but if I edit it under Ubuntu MATE there's no audio that comes through.  Still, I think it has to be a codec or something but then why would it play under U-MATE with sound when edited under Kali but not when edited under U-MATE?

---

### Post by Rob Sayer on 2014-10-22
I don't know much about Kali Linux, but I suspect your problem lies there.  Somehow I doubt the codec support is very good.

---

### Post by frank75 on 2014-10-22
> **Rob Sayer said:**
> I don't know much about Kali Linux, but I suspect your problem lies there.  Somehow I doubt the codec support is very good.

I think you misunderstood.  OpenShot works 100% in Kali, my problem is with audio in exported videos that I cut with OpenShot under Ubuntu MATE. I checked both OpenShot folders in Kali and Ubuntu MATE and they're both the same and anything that I cut and export over the the Ubuntu MATE drive works fine just as it does in Kali. It's only when I cut and export a video in U-MATE that the audio doesn't come through.  It's probably an audio codec that's missing in U-MATE but I don't even know where to start looking to see what it may be.  I had hopped that someone else may have had a similar issue that they fixed and could lend that knowledge to me here.

---

### Post by dannyboy79 on 2014-10-22
what is the mediainfo on the resulting video from openshot? i want to know the audio codec, whether it's mp3, aac, vorbis or what. also, have you tried a different rendering profile (different audio codec) within U Mate openshot?

---

### Post by frank75 on 2014-10-22
I've tried several audio codecs with no success. Also, something else I've noticed, may be nothing but the exported video under Ubuntu MATE has the volume in VLC turned down to zero on start up.

---

### Post by frank75 on 2014-10-23
There is just no audio track being exported when using OpenShot under Ubuntu MATE. I can open "audio" in VLC and nothing. I look at the original video and there's an audio track listed in VLC so I doubt that it's a VLC problem. For some reason OpenShot when used under Ubuntu MATE is just not extracting the audio. It's there in OpenShot because I can play the video in OpenShot and I have audio within the OpenShot player but it's just not getting sent out with the video info during extraction.  This has become very puzzling to me because there's just no logical reason why audio shouldn't get extracted with video.

---

### Post by frank75 on 2014-10-23
Ok, after doing an Ubuntu 14.04.1 install to an external SSD drive and booting to it then installing OpenShot and testing it out under Ubuntu Unity I've come to the conlusion that it's a MATE issue and not an Ubuntu one. OpenShot exported the audio just fine under Ubuntu Unity so I need to look at what MATE doesn't have that Unity does have when working with OpenShot and add it to MATE.

---

### Post by dannyboy79 on 2014-10-23
as i asked, what is the mediainfo of the files that MATE openshot produced??? if you don't know how to use mediainfo than at least click on the video codec and audio codec option within VLC to find out. with this information we'll be able to track down the problem. this may sound silly but are you sure your rendering profile you're choosing when rendering in MATE with openshot doesn't have audio excluded?

---

### Post by frank75 on 2014-10-24
I do exactly the same think in Kali and Ubuntu Unity that I do in Ubuntu MATE when outputting a video and audio plays fine in those videos. There is NO info on audio in VLC with the video output under Ubuntu MATE and I'm not muting the audio, I've used OpenShot for a while now and while I'm not an expert at using it I do know HOW to use it.   I'm going to download some audio only pod casts and try cutting them in OpenShot to see if audio will come though. I'll get back to you with more info.


Ok, just to add a bit more info. I downloaded one of the Linux Luddites pod casts in mp3 format and played it with VLC. Here's the info of the actual download.
Stream 0
Type:Audio
Codec:MPEG Audio Layer 1/2 (mpga)
Channels: Mono
Sample rate: 44100 Hz
Bitrate: 96 kb/s

Here's the info from the cut portion played with VLC
Stream 0
Type: Audio
Codec: MPEG Audio Layer 1/2 (mpga)

Stream 1
Type: Video
Codec: MPEG-1/2 Video (mpgv)
Resolution: 720x480
Display resolution: 720x480
Frame rate: 29.970030
Decoded format: Planar 4:2:0 YUV

Even though there's no video with this pod cast it still exports it from OpenShot as video but no audio will play with the exported version. The VLC player is set to zero for audio on start up. There is info this time under "audio" in the player but no sound what so ever.  I'll try to get a video to edit later on and post the results same as I did for the mp3 pod cast so we can compare the two.

---

### Post by frank75 on 2014-10-24
Ok, downloaded an mp4 video from YouTube to test with. Specs are as follows:

Stream0
Type: Video
Codec: H264-MPEG-4 AVC(part 10)(avc1)
Resolution: 1280x738
Display resolution 1280x720
Frame rate: 29.970030
Decoded format: Planar 4:2:0 YUV

Stream 1
Type: Audio
Codec: MPEG AAC Audio(mp4a)
Channels:Sterreo
Sample rate: 44100 Hz.

Cut video ran though OpenShot as DVD-NTSC, med quality.

Stream 0
Type:Video
Codec: MPEG-1/2 Video(mpgv)
Resolution:720x480
Frame rate: 29.970030
Decoded format: Planar 4:2:0 YUV
 
NO Audio information available under "Codec" in VLC so no audio was exported by OpenShot. 

If you want me to export it in a different format let me know which one and I'll give it a try but so far no format I've tried will allow audio through on export.

---

### Post by Rob Sayer on 2014-10-25
You're been asked several times to open the file in mediainfo.  That's exactly what you should do.  And post the output with code tags.

You also may not realize that ubuntu mate is not an official spin supported by canonical.  I don't see any tech support whatsoever on their site.  Installing actual ubuntu was a good idea.

---

### Post by frank75 on 2014-10-25
> **Rob Sayer said:**
> You're been asked several times to open the file in mediainfo.  That's exactly what you should do.  And post the output with code tags.


I thought what I posted above was the media info? Where are you asking me to look? I need more information about what you're wanting and where you're wanting me to look for the information you need.

---

### Post by dannyboy79 on 2014-10-25
the audio codec info you posted was informational. this means that whatever profile you're choosing in openshot to export as contains some audio codec that is NOT installed on your system. what profile are you choosing to render to in openshot? clearly there's a bug in openshot or just failing to inform you that the render profile you're choosing won't work since the produced video has no audio in it. i would suggest explicitly choosing to render to some audio codec you know is installed on the machine like mp3 when you choose to export your video from openshot. you do that by clicking on the advanced tab and choosing the Audio Settings area.

---

### Post by frank75 on 2014-10-25
> **dannyboy79 said:**
> the audio codec info you posted was informational. this means that whatever profile you're choosing in openshot to export as contains some audio codec that is NOT installed on your system. what profile are you choosing to render to in openshot? clearly there's a bug in openshot or just failing to inform you that the render profile you're choosing won't work since the produced video has no audio in it. i would suggest explicitly choosing to render to some audio codec you know is installed on the machine like mp3 when you choose to export your video from openshot. you do that by clicking on the advanced tab and choosing the Audio Settings area.

I've done that with no luck what so ever.  I can export an edited video in Ubuntu Unity, move the file to Ubuntu MATE and the audio plays just fine. If I do it the same exact way in Ubuntu MATE then I get no audio export what so ever. Why???  If an imported, edited video from Ubuntu Unity will play under Ubuntu MATE with audio then why can't one that's edited under Ubuntu MATE play just as well?  I've tried many different audio codecs. I've tried DVD, Blue Ray, All Formats and set audio to acc, mp3, wav and some others that I can't remember off hand but no audio comes through the render in Ubuntu MATE but using the same technique in Ubuntu Unity(or Kali for that matter) then moving that file to my internal SSD gives me audio.

---

### Post by frank75 on 2014-10-27
So I guess I just give up on this and compile my videos on an external hard drive with Ubuntu Unity, Kali or other Distro on it and not bother with Ubuntu MATE then?

---

### Post by ojc123 on 2014-11-01
I've been having exactly the same problem.  I clean installed 14.10 and now Openshot and Kdenlive both render without audio.  I've tried a variety of settings for the audio and it makes no difference.  I opened the files in movies and in vlc.  Both players open with the volume set to zero but turning it up makes no difference.

I used Openshot on 14.04 with no problems.  I just used the presets, usually Device/Xbox360/720HD because it just worked .  

I've installed Pulse Audio but that makes no difference.  Any solutions welcome.  Please assume that I don't know anything and you won't be too far wrong.  I am willing to learn though.

---

### Post by ojc123 on 2014-11-01
Here's the mediainfo output for the rendered file.  I don't pretend to understand it in any more than a basic way.

General
Complete name                            : /home/owen/Desktop/tub flv rip.avi
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 2.73 MiB
Duration                                 : 28s 896ms
Overall bit rate                         : 793 Kbps
Writing application                      : Lavf56.1.0


Video
ID                                       : 0
Format                                   : xvid
Codec ID                                 : xvid
Duration                                 : 28s 896ms
Bit rate                                 : 784 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Bits/(Pixel*Frame)                       : 0.028
Stream size                              : 2.70 MiB (99%)


Audio
ID                                       : 1
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Codec ID                                 : 2000
Duration                                 : 28s 896ms
Bit rate mode                            : Constant
Bit rate                                 : 320 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 1.10 MiB (40%)
Alignment                                : Aligned on interleaves

---

### Post by ojc123 on 2014-11-03
I've uppdated everything I could think of and one of them has solved the problem.  I'm not sure which though.

---

### Post by Rob Sayer on 2014-11-04
> **frank75 said:**
> So I guess I just give up on this and compile my videos on an external hard drive with Ubuntu Unity, Kali or other Distro on it and not bother with Ubuntu MATE then?

Good luck with *their* tech support ...

---

### Post by ares70 on 2014-12-11
O my god, no have resolution for this? My Openshot dont export audio track in Ubuntu 14.10 64bits. Work Perfect in 14.04 32 bits.

---

### Post by ares70 on 2014-12-11
Mensage in termina are this:

[libx264 @ 0x7f54b882a880] [Eval @ 0x7f54c9cf64c0] Undefined constant or missing '(' in 'dct8x8'
[libx264 @ 0x7f54b882a880] Unable to parse option value "dct8x8"
[libmp3lame @ 0x7f54b9469460] [Eval @ 0x7f54c9cf6470] Undefined constant or missing '(' in 'dct8x8'
[libmp3lame @ 0x7f54b9469460] Unable to parse option value "dct8x8"

---

### Post by ares70 on 2014-12-11
Hey Brothers, i fix it. 

1 - open a terminal and type: **[COLOR=#333333][FONT=Ubuntu]sudo add-apt-repository ppa:sunab/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]kdenlive-[/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]**release**
2 - [B]sudo apt-get update
[/B]3 - sudo apt-get install [/FONT][/COLOR]libmlt6
[COLOR=#333333][FONT=Ubuntu]4 - sudo apt-get install [/FONT][/COLOR]libmlt++3

[COLOR=#333333][FONT=Ubuntu]Annnnd, Work now brothers, or in pt-br(yes im brasilian), Funcionou pra caralho malucoooo. hehehe. 




[/FONT][/COLOR]

---

### Post by Peter_Nerlich on 2014-12-14
> **ares70 said:**
> 1 - open a terminal and type: **[COLOR=#333333][FONT=Ubuntu]sudo add-apt-repository ppa:sunab/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]kdenlive-[/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]**release**
2 - [B]sudo apt-get update
[/B]3 - sudo apt-get install [/FONT][/COLOR]libmlt6
[COLOR=#333333][FONT=Ubuntu]4 - sudo apt-get install [/FONT][/COLOR]libmlt++3

Just had the same problem, saw this thread - and Your solution worked, first try. Thank You so much, and Happy Christmas (well, soon...)!

---

### Post by sidharthcnadhan on 2014-12-21
[COLOR=#333333][FONT=Ubuntu]Go here: [/FONT][/COLOR][http://packages.debian.org/sid/libmlt6](http://packages.debian.org/sid/libmlt6)[COLOR=#333333][FONT=Ubuntu] and here: [/FONT][/COLOR][http://packages.debian.org/sid/libmlt++3](http://packages.debian.org/sid/libmlt++3)[COLOR=#333333][FONT=Ubuntu] 
and in both pages at the bottom there's the option to Download the package, you choose your architecture and download both packages. Then you have to put both packages in the same folder, open that folder in the terminal and type "sudo dpkg -i libmlt+[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]+3_0.9.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]2+git20141027-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]1_amd64.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]deb libmlt6_[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]0.9.2+git201410[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]27-1_amd64.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]deb" where the name of the two packages can change if you have a different architecture than amd64.

See more details [here]("https://answers.launchpad.net/openshot/+question/257781") : [/FONT][/COLOR]

---

### Post by nothor84 on 2014-12-22
Is not an Openshot bug, it's related to those packages: libmlt6 and libmlt++3

In the following link there is a solution to render any video with audio.
[https://askubuntu.com/questions/541635/no-audio-in-rendered-video-files/548279](https://askubuntu.com/questions/541635/no-audio-in-rendered-video-files/548279)

I'm using Ubuntu 14.10 64bits an it works for me.

---

### Post by Diogenesis on 2015-01-30
):PI'm having the exact same problems running Open Shot with Ubuntu 14.10 (no audio being exported), and to be quite honest this thread has managed to confuse me more than enlighten me, lol. So, is there a quick 'n' easy solution? (I did read through it, but you lost me at sudo) :(

---

### Post by viniciusspader on 2015-02-18
> **ares70 said:**
> Hey Brothers, i fix it. 

1 - open a terminal and type: **[COLOR=#333333][FONT=Ubuntu]sudo add-apt-repository ppa:sunab/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]kdenlive-[/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]**release**
2 - [B]sudo apt-get update
[/B]3 - sudo apt-get install [/FONT][/COLOR]libmlt6
[COLOR=#333333][FONT=Ubuntu]4 - sudo apt-get install [/FONT][/COLOR]libmlt++3

[COLOR=#333333][FONT=Ubuntu]Annnnd, Work now brothers, or in pt-br(yes im brasilian), Funcionou pra caralho malucoooo. hehehe. 




[/FONT][/COLOR]

Worked perfectly!

---

### Post by djtarki on 2015-02-24
> **ares70 said:**
> Hey Brothers, i fix it. 

1 - open a terminal and type: **[COLOR=#333333][FONT=Ubuntu]sudo add-apt-repository ppa:sunab/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]kdenlive-[/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]**release**
2 - [B]sudo apt-get update
[/B]3 - sudo apt-get install [/FONT][/COLOR]libmlt6
[COLOR=#333333][FONT=Ubuntu]4 - sudo apt-get install [/FONT][/COLOR]libmlt++3

[COLOR=#333333][FONT=Ubuntu]Annnnd, Work now brothers, or in pt-br(yes im brasilian), Funcionou pra caralho malucoooo. hehehe. 

[/FONT][/COLOR]

This fix works for me only if I export to .dvd . If I export to .mp4 I keep having problems (no audio).

Thanks ares70!

---

### Post by FariAzz on 2015-03-03
> **djtarki said:**
> This fix works for me only if I export to .dvd . If I export to .mp4 I keep having problems (no audio).

Thanks ares70!

I don't get audio when exporting to MP4 either. I'm in Ubuntu 14.10 64 bits. In 14.04 it worked like a charm..

---

### Post by andresv on 2015-03-31
> **ares70 said:**
> Hey Brothers, i fix it. 

1 - open a terminal and type: **[COLOR=#333333][FONT=Ubuntu]sudo add-apt-repository ppa:sunab/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]kdenlive-[/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]**release**
2 - [B]sudo apt-get update
[/B]3 - sudo apt-get install [/FONT][/COLOR]libmlt6
[COLOR=#333333][FONT=Ubuntu]4 - sudo apt-get install [/FONT][/COLOR]libmlt++3

[COLOR=#333333][FONT=Ubuntu]Annnnd, Work now brothers, or in pt-br(yes im brasilian), Funcionou pra caralho malucoooo. hehehe. 




[/FONT][/COLOR]

Thank you so much, it now works for me too.

---

