---
title: "DTS Encoder"
date: 2010-04-16
forum: Multimedia Software
---

### Post by Sumo74 on 2010-04-16
I have been trying literally for days on end for a DTS encoder that can take 6 mono PCM wav file and encode it to DTS. I have tried windows program after windows program under wine, and all seem to either crash, or use Java, which does not correspond well with Wine. I have successfully converted it to an .mlp file, which I cannot playback on anything, and have even tried ffplay (which from what I understand does have that codec) and nothing.

So I have really hoping I can find a solution, any solution, other than taking all the programs over to a buddys computer just for this single album.

Thanks.

---

### Post by Sumo74 on 2010-04-16
Sorry for the bump, but I am literally going crazy with trying to find a solution, I have even resorted to calling my friends with windows, but ran into a logistic issue (How to transfer nearly 4 gb of music, without a 4 gb flash drive handy), but I am really looking for a Linux solution, whatever it be.

---

### Post by mc4man on 2010-04-17
I'm fairly sure you won't find a linux dts encoder, though I guess anythings possible.

As far as your .mlp, I've no trouble with various .mlp files i have using mplayer or vlc. ( vlc is a bit more 'flexible' atm

You'd need to possibly use a non-repo version of either though the ffmpeg used in karmic and lucid does support and *the repo mplayer and vlc will play  mlp* ( though it's possible the lucid vlc will also play some 'unplayable' mlp (trhd) as mlp in mkv (.mka

Ex. 
> VLC media player 1.0.6-git Goldeneye
0x845d318] avcodec decoder debug: libavcodec initialized (interface 0x343b00)
[0x845d318] avcodec decoder debug: ffmpeg codec (MLP/TrueHD Audio) started

> MPlayer SVN-r30881-4.4.3 (C) 2000-2010 MPlayer Team
Selected audio codec: [ffmlp] afm: ffmpeg (FFmpeg MLP)


If desired (though I'd try the repo version(s) first), you'd find it easier to get a more recent mplayer from a ppa [or build one]("http://ubuntuforums.org/showthread.php?t=1305181"), a decent vlc build would require a bit more work. 

Otherwise you'd find it fairly easy to do a 5.1 flac from your .wavs or ac3 (aften

If you had the means to upload a sample of your mlp files that may prove informative as to why you can't get playback.

---

### Post by Sumo74 on 2010-04-18
Well I did find a round about way to doing this. Because you said Flac 5.1 it basically lite up a light bulb in my head. Using FFMPEG I just converted the .mlp to flac and sure enough they keep the sound 5.1 and keep the sample rate (A lot of my issues have been from using downsampled material to make my .mlps), but I still can't get mplayer or VLC to play the .mlp files. VLC keeps saying it cannot play trhd and there is no way around that and mplayer is downloaded a codec, but it read the .mlp file as a mpeg-4 audio and video file, so the codec has no use for me. 

I have the most recent version of both (Both being from the repo), so I am not for sure what could be up with that. I could try to attach an .mlp I have stored, I can't here, the file size is too big, even if I compress it greatly.

---

### Post by mc4man on 2010-04-18
> I have the most recent version of both (Both being from the repo),
I see you haven't mentioned what ubuntu release you're using.

Anyway, to test the repo apps I didn't use this install because I have a self built, modded  vlc. It just dawned on me that my testing install is lucid which has vlc 1.0.5.

If you're on karmic (vlc 1.0.2) you could consider finding a ppa for a more current vlc.

I can recommend this one though do note - there are a ton of packages here, I'd suggest if using to enable the ppa, install/upgrade what you wish and then disable it till you want to use again. In other words don't leave enabled..., though I don't see anything that would be an issue if inadvertently upgraded, you never know.

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

If inclined to upload,  something like mediafire is pretty good and *should work ok* on linux.

---

### Post by Sumo74 on 2010-04-18
Sorry meant to mention that I have Lucid, Beta 2. And also that FFplay did play the .mlp files, but speed them up so bad, it was unrecognizable.

---

### Post by shantiq on 2012-05-31
a couple of years on there seems to be some help here for converting from mlp/aob   [if mlp rename aob]


to 24-bit flac/ogg/wav   [**dvd audio extractor **]("http://www.dvdae.com/download")   and there is a deb for Ubuntu and 30 day free usage

> shantiq@shantiq-00000000000000000000000:~/Music/1AUDIO_TS$ mediainfo ATS_01_2.aob
General
Complete name                            : ATS_01_2.aob
Format                                   : MPEG-PS
File size                                : 1 024 MiB
Duration                                 : 28mn 13s
Overall bit rate mode                    : Variable
Overall bit rate                         : 5 072 Kbps

Audio
ID                                       : 189 (0xBD)-161 (0xA1)
Format                                   : MLP
Muxing mode                              : DVD-Video
Duration                                 : 28mn 13s
Bit rate mode                            : Variable
Maximum bit rate                         : 9 600 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 192 KHz
Bit depth                                : 24 bits


shantiq@shantiq-00000000000000000000000:~/Music/1/AUDIO_TS$ mediainfo ohio01_2.flac
General
Complete name                            : ohio01_2.flac
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
File size                                : 977 MiB
Duration                                 : 28mn 13s
Overall bit rate mode                    : Variable
Overall bit rate                         : 4 841 Kbps
Album                                    : Unknown Album
Track name                               : Chapter 01
Track name/Position                      : 1
Performer                                : Unknown Artist

Audio
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
Duration                                 : 28mn 13s
Bit rate mode                            : Variable
Bit rate                                 : 4 841 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 192 KHz
Bit depth                                : 24 bits
Stream size                              : 977 MiB (100%)
Writing library                          : libFLAC 1.2.1 (UTC 2007-09-17)


---

