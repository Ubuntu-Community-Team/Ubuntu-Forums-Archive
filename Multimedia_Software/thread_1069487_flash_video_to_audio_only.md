---
title: "flash video to audio only"
date: 2009-02-14
forum: Multimedia Software
---

### Post by truthseer0 on 2009-02-14
Ok here it is, I downloaded a video from youtube using the firefox cache from about:cache and just dragged dropped to desktop for easy access. It'll play just fine using Totem video player, but everything else i've tried FAILS. everything else doesn't' support it. what i want to do is get this from flash vid to some kind of audio format, be it mp3, wav, ogg, i don't care really. when it was in the cache it was just a series of numbers and letters with no file extension. properties says type is "Flash video (video/x-flv)". looked around web and found this ffmpeg thing that sounded good, didn't work. knowing me, i'm missing something so obvious it's about to bite my head off...
other random info: H.264/AVC Video codec and AAC audio codec.
ideas? options? i'm so lost :( :confused:
thank you for help :)

---

### Post by Melcar on 2009-02-14
I normally download Youtube flash videos with clive.  Once I got the file, just use ffmpeg to extract the audio track:

ffmpeg -i flashvideo.flv flashvideo.mp3

---

### Post by andrew.46 on 2009-02-14
Hi truthseer,

> **truthseer0 said:**
> what i want to do is get this from flash vid to some kind of audio format, be it mp3, wav, ogg, i don't care really.

Melcar has suggested a method to strip out the audio using FFmpeg. You can also use FFmpeg to interrogate the file and reveal its contents:

```
ffmpeg -i myfile.flv
```

If you are happy with using FFmpeg you can then accurately and with some precision convert to other formats. Was there a problem downloading FFmpeg from the Ubuntu repositories?

Andrew

---

### Post by neu2buntu on 2009-02-14
another option is to use qjackctl and audacity running together,if setup properly any audio that can be heard from your speakers can be recorded in audacity and then saved from there it can then be burned to cd (if the source isnt copyrighed or something)

---

### Post by lswb on 2009-02-14
mplayer can also extract an mp3 from a flash video:

mplayer -dumpaudio file.flv -dumpfile file.mp3

---

### Post by truthseer0 on 2009-02-15
thanks folks, i'll go through and try these until something works :) lol. but as a side note i've got to say, ubuntu rocks for community if nothing else, i was honestly suprised when i found that there are people actually willing to help :P

---

### Post by truthseer0 on 2009-02-15
well my noob term seems to be lasting quite awhile. and i tried the ffmpeg options and the mplayer route and both came up with unsupported file types. "[flv @ 0x8837aa8]Unsupported video codec (7)" (spit out from mplayer) and "[flv @ 0xb8000388]Unsupported video codec (7)" (spit out from ffmpeg). it didn't have to flv extension from the beginning and i added it to the end but it's always been a flash video. i'm thinking it has to do with me pulling it straight out of the firefox cache to save? like i said, plays in totem still but not in vlc or *anything* else i've tried. should i just move on to software to jack it from youtube instead of this mess? like that "clive" thing from melcar?
thanks,
Ed

---

### Post by neu2buntu on 2009-02-15
after you have streamed your video from youtube the complete file is in  your /tmp folder so you can just drag it to your desktop .you dont need to be root either to do this ,just tried there now.  make sure the video is completely streamed ,what i do is just pause the video as soon as it starts and wait till the red bar is all the way to right. and try again with one of the above posts ie ffmpeg or whatever !!!

---

### Post by bestsoft666 on 2009-02-17
I suggest [free youtube mp3 converter(ubuntu > 8.04)]("http://www.free-star.org/free-youtube-mp3-converter-freeware.html"),it download youtube video and convert to mp3 at same time.

---

### Post by mikewu on 2009-02-17
I've had limited success with extracting audio from /tmp.

What I usually do now it use youtube-dl to download the .flv

It's in the repositories, just sudo apt-get install youtube-dl

youtube-dl youtube-video-website

Then as others have suggested

mplayer -dumpaudio file.flv -dumpfile file.mp3

---

### Post by FakeOutdoorsman on 2009-02-17
> **truthseer0 said:**
> ... "[flv @ 0xb8000388]Unsupported video codec (7)" (spit out from ffmpeg).
Can you paste your FFmpeg command and the full FFmpeg output?

---

### Post by truthseer0 on 2009-02-17
> **FakeOutdoorsman said:**
> Can you paste your FFmpeg command and the full FFmpeg output?

[flv @ 0xb7f62388]Unsupported video codec (7)
Input #0, flv, from 'arg.flv':
  Duration: 00:04:02.7, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: 0x0007, 1000.00 tb(r)
    Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
Output #0, mp2, to 'WOOT.mp3':
    Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec (id=0) for input stream #0.1


^ that is the ffmpeg output except one thing. that first line there? unsupported video codec? it spits that out so many times it fills the entire terminal except for anything that comes after it.

anyways, you're welcome to email me at [email]truthseer0@aim.com[/email] with new ideas, just put "ubuntu FLV" as the subject and i'll read it. beyond that, i'm going to go to new ways of downloading, because this temp cache thing isn't working :) thank you everybody for your time and ideas, and i'm sorry this post is a bit late... have had a lot of homework to do, still a student *sob*.

---

### Post by Leetbumble on 2009-03-01
I have the same problem. I get the following when i enter 

mplayer -dumpaudio Flashdpsxwr -dumpfile army.mp3


[flv @ 0xbe7a70]Could not find codec parameters (Video: 0x0007)
[flv @ 0xbe7a70]Could not find codec parameters (Audio: 0x000a, 44100 Hz, stereo)
[flv @ 0xbe7a70]skipping flv packet: type 97, size 7627016, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 158, size 3359616, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 148, size 11399319, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 27, size 702052, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 17, size 1672274, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 127, size 13588101, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 69, size 2030763, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 183, size 2385596, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 242, size 6111612, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 230, size 10700184, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 179, size 2095445, flags 0
[flv @ 0xbe7a70]skipping flv packet: type 194, size 12887072, flags 0
LAVF_header: av_find_stream_info() failed

Anyone got a solution? I'll keep looking if I find it Ill make up a full how2.

---

### Post by joshzam on 2009-03-05
I'm afraid I don't have a solution to your problem, but both of these methods worked flawlessly for me. I just wanted to add that the ffmpeg method appears to re-encode the audio, thus leaving you with an even more compressed version of the audio. The mplayer method just ripped the original audio out of my FLV and left me with a perfect MP3. Thanks to all who offered their help!

---

### Post by neu2buntu on 2009-03-05
for the problem with the "mplayer" command it may be possible that the package "mencoder" is required . and the "ffmpeg" problem could be down to needing the right "libav"-dev codecs ,try look at synaptic type in ffmpeg, make sure all reccomended and suggested packages are installed too... and maybe something alse to do is enable "medibuntu" repositories and install win32 codecs also.....  i am only more or less guessing here,but its worth a try!!!

---

### Post by FakeOutdoorsman on 2009-03-05
> **joshzam said:**
> I'm afraid I don't have a solution to your problem, but both of these methods worked flawlessly for me. I just wanted to add that the ffmpeg method appears to re-encode the audio, thus leaving you with an even more compressed version of the audio. The mplayer method just ripped the original audio out of my FLV and left me with a perfect MP3. Thanks to all who offered their help!
FFmpeg can also just copy the audio stream instead of re-encoding:
```
ffmpeg -i inputfile.flv -acodec copy outputfile.mp3
```
You will have to know what the audio format is for the input video to provide the proper output file extension, but you can find out easily with:
```
ffmpeg -i inputfile.flv
```
> **neu2buntu said:**
> for the problem with the "mplayer" command it may be possible that the package "mencoder" is required . and the "ffmpeg" problem could be down to needing the right "libav"-dev codecs ,try look at synaptic type in ffmpeg, make sure all reccomended and suggested packages are installed too... and maybe something alse to do is enable "medibuntu" repositories and install win32 codecs also.....  i am only more or less guessing here,but its worth a try!!!
The package **libavcodec-unstripped-51** for Intrepid users will enable most restricted encoders in FFmpeg.  Hardy users can enable the [Medibuntu](http://medibuntu.org/) repository and install FFmpeg from that.  Medibuntu doesn't offer much for FFmpeg in Intrepid.  If you want the bleeding-edge, access to libx264 presets, or just want to customize FFmpeg:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

