---
title: "Problems playing back h264 file"
date: 2016-08-17
forum: Multimedia Software
---

### Post by stuart77 on 2016-08-17
I have purchased a crappy Vstarcam camera from ebay, I knew it would be a bit dodgy but there we go.

It's producing .h264 files on the memory card.  When I try to play them by double clicking I get a screen that plays three times too fast and no audio on MPlayer.  If I launch VLC it just quits with no error message.  I have installed restricted-extras (and I am on Xenial).

Mediainfo on command line reports:

General
Complete name                            : source.h264
Format                                   : AVC
Format/Info                              : Advanced Video Codec
File size                                : 42.3 MiB

Video
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 1 frame
Format settings, GOP                     : M=1, N=80
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive

I tried installing their bundled 'ZPlayer' windows software via Wine and it does play back audio but the picture is too poor that way (appears to be only 16 colours) and there must be a better way.  Can anyone give me help please?  I have tried on the VLC forums but I have a no reply post on there since 2 weeks ago.

---

### Post by mc4man on 2016-08-17
Maybe try with mpv. 16.04 has an ok version, good enough at least to test.
mpv is basically a cli player based off of mplayer but it also uses a psuedo-gui so just r. click on your file > open with mpv.
(it at a min benefits from a config file but again for this purpose doesn't matter.
Or run from a terminal to see what's reported, e.g. mpv /path/to/filename

---

### Post by stuart77 on 2016-08-18
Thanks that's a really useful answer as I've found out some more info.  It plays the video a bit too fast and with no audio.  Here's what the command line reports during playback:

laying: source.h264
[ffmpeg] Invalid UE golomb code
[ffmpeg] Invalid UE golomb code
[ffmpeg] Invalid UE golomb code
 (+) Video --vid=1 (h264)
This stream has no timestamps!
Making up playback time using 25.000000 FPS.
Seeking will probably fail badly.
[ffmpeg] Invalid UE golomb code
VO: [opengl] 1280x720 yuv420p
V: 00:00:01 (0%)
[ffmpeg] Invalid UE golomb code
V: 00:00:07 (1%)
[ffmpeg] Invalid UE golomb code
V: 00:00:07 (1%)
[ffmpeg] Invalid UE golomb code
V: 00:00:10 (2%)
[ffmpeg] Invalid UE golomb code
V: 00:00:10 (2%)
[ffmpeg] Invalid UE golomb code
V: 00:00:11 (2%)
[ffmpeg] NULL: missing picture in access unit with size 433
V: 00:00:12 (2%)
[ffmpeg/video] h264: data partitioning is not implemented. Update your FFmpeg version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
[ffmpeg/video] h264: If you want to help, upload a sample of this file to [ftp://upload.ffmpeg.org/incoming/](ftp://upload.ffmpeg.org/incoming/) and contact the ffmpeg-devel mailing list. (ffmpeg-devel@ffmpeg.org)
[ffmpeg/video] h264: no frame!
V: 00:00:12 (2%)
Error while decoding frame!
V: 00:00:13 (2%)
[ffmpeg] Invalid UE golomb code
V: 00:00:14 (2%)
[ffmpeg] Invalid UE golomb code
V: 00:00:14 (2%)
[ffmpeg] NULL: sps_id 1 out of range
V: 00:00:14 (2%)
[ffmpeg/video] h264: sps_id 1 out of range
(Paused) V: 00:00:15 (2%)


Exiting... (Quit)


Any further help where I need to be looking please?

---

### Post by mc4man on 2016-08-18
No clue here, after reading about UE golomb (en)coding even less of an idea.
Maybe upload a clip with audio & video & link in a post here.

---

### Post by jeremy31 on 2016-08-18
h264 files on their own will not have audio [http://stackoverflow.com/questions/1884101/can-h264-container-contain-audio-tracks](http://stackoverflow.com/questions/1884101/can-h264-container-contain-audio-tracks)

A few years ago I had some issues with them and it seems they play fast in Windows also as I had to reduce the playback speed there also

---

### Post by andrew.46 on 2016-08-20
Does seem a little odd. As mc4man has suggested perhaps you could post a sample video here:

DataFileHost
[https://www.datafilehost.com/](https://www.datafilehost.com/)

and this might produce some clues as to the exact nature of the playback problem....

---

### Post by mc4man on 2016-08-20
> **andrew.46 said:**
> Does seem a little odd. As mc4man has suggested perhaps you could post a sample video here:

DataFileHost
[https://www.datafilehost.com/](https://www.datafilehost.com/)

and this might produce some clues as to the exact nature of the playback problem....just to mention for what's it's worth
When I checked datafilehost the other day I noticed different owners & when you click to dl a file FF pops up an attack site warning, google also has a warning on the site. While obviously if  you, me  or the next guy uploaded a file & linked here  it should be fine but  the warning would be off putting for sure.
(currently looking for an alternate..., sprunge.us is excellent as a cli pastebin but haven't found a data site yet.

---

### Post by stuart77 on 2016-08-26
Sorry for the delay, joys of having to do work around the house :(

Right, so thanks for the comments to date I really appreciate input.

I have uploaded a link to a sample file here - [https://filebin.net/v6gde8pv9bli2pwt/20160826154956_100.h264](https://filebin.net/v6gde8pv9bli2pwt/20160826154956_100.h264)

It does have audio on the file, I can launch the manufacturer-linked 'Video Player' via Vstarcam's website using Wine.  The image and audio is reduced quality on this player as my machine is working hard to play it, but there is definitely audio.

I can launch it using mpv and mplayer but both run the video too quickly and have no audio.  VLC does nothing and reports no error.

If you can get it playing the audio will be very quiet but it is there if you turn the volume up.  So perhaps this is not a 'true' h264 file but more some sort of wrapper?

---

### Post by andrew.46 on 2016-08-26
Plays fine here but you need to specify fps:

```
mplayer -fps 25 20160826154956_100.h264 
```

as is usual with a raw stream of this kind. There is no audio stream with this file that I could detect. Certainly mediainfo does not report one:

```

andrew@ilium~$ mediainfo 20160826154956_100.h264 
General
Complete name                            : 20160826154956_100.h264
Format                                   : AVC
Format/Info                              : Advanced Video Codec
File size                                : 37.2 MiB

Video
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 1 frame
Format settings, GOP                     : M=1, N=80
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive


andrew@ilium~$ 

```

I note as well that subsequent conversion with FFmpeg is a little problematical, some success with simply repackaging into a Matroska container with mkvtoolnix though.

Here is a slightly reworked version of your file which I had to convert to yuv first to get a decent encode, I am sure FakeOutdoorsman could do  better job:

```
wget http://www.andrews-corner.org/tmp/new_container.mp4
```

This one has no trouble with vlc and friends....

---

### Post by stuart77 on 2016-08-29
> **andrew.46 said:**
> Plays fine here but you need to specify fps:

Here is a slightly reworked version of your file which I had to convert to yuv first to get a decent encode, I am sure FakeOutdoorsman could do  better job:

This one has no trouble with vlc and friends....

Thanks I appreciate your work on that.  The thing that's really baffling me though is if I install the video player from [http://www.eye4.so/download/](http://www.eye4.so/download/) and use Wine to run, I do get badly reduced video quality however there is a sound track.  That's why I'm not sure the file is pure h264, how can I get to this sound track using native Ubuntu?

---

### Post by andrew.46 on 2016-08-30
> **stuart77 said:**
> Thanks I appreciate your work on that.  The thing that's really baffling me though is if I install the video player from [http://www.eye4.so/download/](http://www.eye4.so/download/) and use Wine to run, I do get badly reduced video quality however there is a sound track.  That's why I'm not sure the file is pure h264, how can I get to this sound track using native Ubuntu?

Well I downloaded that player on a Windows VM and ran the file and although there was some odd distortion over my speakers I could hear no soundtrack...

---

### Post by stuart77 on 2016-08-31
The distortion is probably the audio, there isn't a lot but if you play the video back at timestamp 15:50:19 and again at 15:50:27 you hear whooshes that last a couple of seconds, that's the sound of nearby passing traffic.  Is that what you can hear?

---

### Post by andrew.46 on 2016-08-31
I hear 2 noises when I am using the Windows player:

[LIST=1]
[*]A regular tapping noise
[*]A rarer 'whooshing' noise as you have described
[*]
[/LIST]

In absence of any real audio track I confess that I believe this is a shortcoming of the actual windows player rather than a hidden audio track. But I am always ready to be corrected :)

---

### Post by mc4man on 2016-08-31
Have you looked at the specs for your cam on the web site? Most of their current run of the mill cams show ADPCM/32kbps for audio compression.
As it stands no linux app seems to detect an audio stream, you could try in any of several windows apps to see if it finds an audio stream. 
Possibly the only indication here may be that  Invalid UE golomb code warning as it could be from audio ( though I guess it could be used in video..

---

### Post by stuart77 on 2016-09-05
> **mc4man said:**
> Have you looked at the specs for your cam on the web site? Most of their current run of the mill cams show ADPCM/32kbps for audio compression.
As it stands no linux app seems to detect an audio stream, you could try in any of several windows apps to see if it finds an audio stream. 
Possibly the only indication here may be that  Invalid UE golomb code warning as it could be from audio ( though I guess it could be used in video..

Yes it's ADPCM/32k, the camera specs are here -
[http://www.vstarcam.com/C7837WIP-Home-monitoring-IP-Camera-121.html](http://www.vstarcam.com/C7837WIP-Home-monitoring-IP-Camera-121.html)

How can I trick something like VLC to play this back with audio, or at least convert it into a useable mp4 format?  I'm starting to regret buying this cam! ;)

---

