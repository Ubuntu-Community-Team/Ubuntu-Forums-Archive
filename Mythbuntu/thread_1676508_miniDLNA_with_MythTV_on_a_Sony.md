---
title: "miniDLNA with MythTV on a Sony"
date: 2011-01-27
forum: Mythbuntu
---

### Post by ncpokrt on 2011-01-27
I thought it would be helpful to Sony BD and Bravia owners to start a new thread.  I have been trying to get my Sony BDP-S570 Blue-ray player to find my MythTV files.  I tried MediaTomb and Rygel.  Neither worked.  Then I found this thread which was very helpful in installing minidlna:

[http://ubuntuforums.org/archive/index.php/t-1630547.html](http://ubuntuforums.org/archive/index.php/t-1630547.html)

There is also a very large thread on this at [http://ubuntuforums.org/showthread.php?t=1185619](http://ubuntuforums.org/showthread.php?t=1185619) but it is not Myth specific.

I set up minidlna.  The player can see the DLNA server and it can find the correct folders on the MythTV server.  But the says "There is no playable file".

I copied one of the MythTV files to a usb and I plugged it into the player.  The player was able to play the file.  So the player has no problem with the format, except through DLNA.

I will continue to work on this and I will post a solution if I find one.  Has anyone solved this?

---

### Post by ncpokrt on 2011-01-27
After some poking around, it seems that Sony prevents MPEG-4 files from being seen through DLNA.  I wrote to Sony to complain.  I got this very unsatisfying reply:

> I'm sorry that the files on the computer does not play on the Blu-ray Player, using the DLNA feature. I have provided a link with the information on the file types that are supported when using the DLNA feature:

  [http://www.kb.sony.com/selfservice/documentLink.do?externalId=C1017936](http://www.kb.sony.com/selfservice/documentLink.do?externalId=C1017936)

Please note that the files that may be played using the USB stick may not be supported when trying to play using the DLNA feature.

The link gives the following supported file formats:

Video:
MPEG-2 PS	Video: MPEG-2 Audio: LPCM, AC-3, MPEG-1/2 Audio Layer 2 Container: MPEG-2 Program Stream
MPEG-2 TS	Video: MPEG-2 Audio: AC-3 Container: MPEG-2 Transport Stream

Music:
MP3	MPEG-1 Audio Layer 3 (CBR, VBR)
LPCM	LPCM L16 format

Photos: JPEG only

---

### Post by ncpokrt on 2011-01-27
I am happy to say that the miniDLNA works for MythTV files on the PS3.

---

### Post by nickrout on 2011-01-27
> **ncpokrt said:**
> After some poking around, it seems that Sony prevents MPEG-4 files from being seen through DLNA.  I wrote to Sony to complain.  I got this very unsatisfying reply:



The link gives the following supported file formats:

Video:
MPEG-2 PS	Video: MPEG-2 Audio: LPCM, AC-3, MPEG-1/2 Audio Layer 2 Container: MPEG-2 Program Stream
MPEG-2 TS	Video: MPEG-2 Audio: AC-3 Container: MPEG-2 Transport Stream

Music:
MP3	MPEG-1 Audio Layer 3 (CBR, VBR)
LPCM	LPCM L16 format

Photos: JPEG only

I think the one thing you haven't told us is the format and codec of your files?

---

### Post by ener_dk on 2011-01-28
Hi,

I got a sony 32ex500 and have tried with minidlna on a low resource pc.
But the tv doesnt play many format from the server... If you want to use dlna you need to make 'transfor on the fly' with ps3media server or another server that supports transfor on the fly and with a powerfull pc.

Regards :)

---

### Post by ncpokrt on 2011-02-02
> **nickrout said:**
> I think the one thing you haven't told us is the format and codec of your files?

The formats listed are the ones that Sony supports.  The post is just there for FYI so that people don't have to go searching like I did.

My files are from MythTV which I think are MPEG-4.  They have the file extension .mpg

---

### Post by newlinux on 2011-02-02
> **ncpokrt said:**
> The formats listed are the ones that Sony supports.  The post is just there for FYI so that people don't have to go searching like I did.

My files are from MythTV which I think are MPEG-4.  They have the file extension .mpg

The mythtv codec/container depends on your tuner card and recording profile for analog recordings and transcode settings(if transcoding).

My mythtv recordings from ATSC/QAM (using DVB driver) are mpeg-2 transport stream. My recordings from my HD-PVR are using the h.264  codec and I believe muxed into a an mpeg-2 transport stream container

---

### Post by ncpokrt on 2011-02-02
> **newlinux said:**
> The mythtv codec/container depends on your tuner card and recording profile for analog recordings and transcode settings(if transcoding).

That's interesting.  I use an HDHomeRun tuner. After some searching, from [http://www.mythbuntu.org/wiki/hardware:](http://www.mythbuntu.org/wiki/hardware:)

> None of the capture devices listed above perform any encoding; they merely allow your computer to save a copy of a HDTV stream which has already been converted to MPEG-2 at the broadcast facility.  TBD: Except HD-PVR.

So is it MPEG-2?

---

### Post by nickrout on 2011-02-02
For digital TV the encoding codec is whatever the broadcaster sends. Some encode using mpeg2, some use h.264. If you are in the US it is likely to be the former. elsewhere the technology has often moved on to the superior h.264.

Do not confuse this with the container. The container is controlled by mythtv in either case, and mythtv uses mpeg2-ts.

The HD-PVR of course does not capture a digital stream, it converts an analogue stream into a digital stream containing h.264 encoded video. I am not sure of the container myth uses in this case.

---

### Post by newlinux on 2011-02-02
> **nickrout said:**
> For digital TV the encoding codec is whatever the broadcaster sends. Some encode using mpeg2, some use h.264. If you are in the US it is likely to be the former. elsewhere the technology has often moved on to the superior h.264.

Do not confuse this with the container. The container is controlled by mythtv in either case, and mythtv uses mpeg2-ts.

The HD-PVR of course does not capture a digital stream, it converts an analogue stream into a digital stream containing h.264 encoded video. I am not sure of the container myth uses in this case.

I'm fairly sure mythtv puts HD-PVR recordings in an  mpeg-2 transport stream container as well, as I mentioned above.

---

### Post by nickrout on 2011-02-02
> **newlinux said:**
> I'm fairly sure mythtv puts HD-PVR recordings in an  mpeg-2 transport stream container as well, as I mentioned above.

Yes the wiki supports that proposition:

> The HD PVR captures at resolutions from VGA/D1 (480i) up to 1080i, and encodes the component inputs in real time using the h.264/MPEG-4 video codec and the AAC audio codec. The streams are muxed into a slightly modified MPEG-2 Transport Stream container.

[http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)

---

### Post by ncpokrt on 2011-02-03
[HTML][/HTML]Okay, I'm learning.  Thanks to all of the replies that helped open my eyes.

I found a program that will let you inspect video files.  It's called mediainfo.  Here is a link: [http://mediainfo.sourceforge.net/en](http://mediainfo.sourceforge.net/en)

Or if you just want to install it (with Ubuntu 9.10 or above)
$ sudo add-apt-repository ppa:shiki/mediainfo
$ sudo apt-get update
$ sudo apt-get install mediainfo

Here is some of the info on one of the files that I recorded:
General
ID                               : 2487 (0x9B7)
Complete name                    : 1031_20110127210000.mpg
Format                           : MPEG-TS
File size                        : 7.81 GiB
Duration                         : 59mn 58s
Overall bit rate                 : 18.6 Mbps

Video
ID                               : 49 (0x31)
Menu ID                          : 1 (0x1)
Format                           : MPEG Video
Format version                   : Version 2
Format profile                   : Main@High
Format settings, BVOP            : Yes
Format settings, Matrix          : Default
Format settings, GOP             : M=3, N=15
Codec ID                         : 2
Duration                         : 59mn 58s
Bit rate mode                    : Constant
Bit rate                         : 17.7 Mbps
Width                            : 1 920 pixels
Height                           : 1 080 pixels
Display aspect ratio             : 16:9
Frame rate                       : 29.970 fps
Standard                         : Component
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Interlaced
Scan order                       : Top Field First
Compression mode                 : Lossy
Bits/(Pixel*Frame)               : 0.284
Stream size                      : 7.22 GiB (92%)

Audio #1
ID                               : 52 (0x34)
Menu ID                          : 1 (0x1)
Format                           : AC-3
Format/Info                      : Audio Coding 3
Mode extension                   : CM (complete main)
Codec ID                         : 129
Duration                         : 59mn 58s
Bit rate mode                    : Constant
Bit rate                         : 384 Kbps
Channel(s)                       : 6 channels
Channel positions                : Front: L C R, Side: L R, LFE
Sampling rate                    : 48.0 KHz
Bit depth                        : 16 bits
Compression mode                 : Lossy
Delay relative to video          : -297ms
Stream size                      : 165 MiB (2%)

---

### Post by ncpokrt on 2011-02-03
Getting back to the original purpose for this thread, Sony says it supports

> MPEG-2 PS	Video: MPEG-2 Audio: LPCM, AC-3, MPEG-1/2 Audio Layer 2 Container: MPEG-2 Program Stream
MPEG-2 TS	Video: MPEG-2 Audio: AC-3 Container: MPEG-2 Transport Stream

Maybe I'm missing something but it seems that the player should be seeing the files.  I tried changing the file extensions.

.mpg .m2p .mts .ts and .tod are not recognized.

---

### Post by newlinux on 2011-02-03
> **ncpokrt said:**
> Getting back to the original purpose for this thread, Sony says it supports



Maybe I'm missing something but it seems that the player should be seeing the files.  I tried changing the file extensions.

.mpg .m2p .mts .ts and .tod are not recognized.

yes, that's what I was trying to point out to you (I should have been more explicit) - that your recordings probably are not mp4 but rather mpeg-2 (since confirmed) and thus should be seen - so something else is going on especially since your files will play from the USB. Seems like to problem is between the sony and miniDLNA at this point, and I can't help much with either since I don't use either... Or you could try a different DLNA server...

---

### Post by nickrout on 2011-02-03
> **ncpokrt said:**
> Getting back to the original purpose for this thread, Sony says it supports



Maybe I'm missing something but it seems that the player should be seeing the files.  I tried changing the file extensions.

.mpg .m2p .mts .ts and .tod are not recognized.

Have you read all 11 pages of this thread?

[http://ubuntuforums.org/showthread.php?t=1185619](http://ubuntuforums.org/showthread.php?t=1185619)

I haven't, because I don't have a dlna tv and am only trying to help out.

---

### Post by ncpokrt on 2011-02-04
I think I finally have this figured out.  I spent some time with Sony customer support.  They could not help me but they sent me to DLNA.org.  That's where I had the epiphany.  If I am interpreting the white paper at [https://docs.google.com/viewer?url=http://www.dlna.org/news/DLNA_white_paper.pdf](https://docs.google.com/viewer?url=http://www.dlna.org/news/DLNA_white_paper.pdf) correctly, I think DLNA.org requires all Certified DLNA players to play only content that has DRM on it.

So the only way to view these files is if there is a way to add DRM to the files.

---

### Post by nickrout on 2011-02-04
> **ncpokrt said:**
> I think I finally have this figured out.  I spent some time with Sony customer support.  They could not help me but they sent me to DLNA.org.  That's where I had the epiphany.  If I am interpreting the white paper at [https://docs.google.com/viewer?url=http://www.dlna.org/news/DLNA_white_paper.pdf](https://docs.google.com/viewer?url=http://www.dlna.org/news/DLNA_white_paper.pdf) correctly, I think DLNA.org requires all Certified DLNA players to play only content that has DRM on it.

So the only way to view these files is if there is a way to add DRM to the files.

Absolute rubbish.

---

### Post by ncpokrt on 2011-02-04
I realized after I wrote that people might think that I was suggesting you add DRM to the files.  That is not what I meant.   

Is that what you think is rubbish?  If not, maybe you can elaborate?

---

### Post by newlinux on 2011-02-04
> **ncpokrt said:**
> I realized after I wrote that people might think that I was suggesting you add DRM to the files.  That is not what I meant.   

Is that what you think is rubbish?  If not, maybe you can elaborate?

I can't speak for nickrout, but I think it's rubbish if that's the way your Sony works. Just horrible if that's the way it works.

---

### Post by nickrout on 2011-02-04
The proposition that dlna only works with drm files is rubbish.

And I will say again:

Have you read all 11 pages of this thread?

[http://ubuntuforums.org/showthread.php?t=1185619](http://ubuntuforums.org/showthread.php?t=1185619)

---

### Post by ncpokrt on 2011-02-04
I have read all 11 pages of the thread.  I went almost all of them again today.  The general consensus is to run minidlna which is why is stared using it in the first place.  However, that thread is not MythTV specific.  It does not address why MythTV files in particular are not picked up by the player. That is why I started this thread on the Mythbuntu Forum.

According to Sony's info the files should be picked up by the player.  I spoke to Sony tech support.  They genuinely tried to help but they do not have a clue about Linux.  In fact they suggested that I "speak to Linux" about the problem.  I asked them if there is a file size limitation because I thought the large size of MythTV files might be a barrier.  Sony says no.  Sony also suggested that I install TVMOBili, which I did.  That worked as a DLNA server but the player also refused to see the mpg files.  TVMOBili (which is "Certified DLNA") also cannot play the MPEG-2 MythTV files.  However, I used HandBrake to morph one of the files to MPEG-4 and TVMOBiLi can play that.  But the Sony player cannot play MPEG-4.

Based on Sony's past practices regarding DRM, I am still going with the theory that they don't like the open nature of the MythTV files.

---

### Post by Wobblybob on 2011-04-10
I don't use Myth but the problem you are having may be due to the format of your movie files, try converting one using ffmpeg to .mpg using a Terminal with;

$ **ffmpeg -i /path_to_file/input.m4v -target pal-dvd /path_to_file/output.mpg**

change the input ext to the correct one for your input file, and pal to ntsc if required. This format plays on my Bravia TV served up using the minidlna server.

---

