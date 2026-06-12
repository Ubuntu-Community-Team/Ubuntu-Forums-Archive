---
title: "HDDVD playback / no E-AC-3 audio with mplayer"
date: 2008-12-07
forum: Multimedia Software
---

### Post by spmurphy on 2008-12-07
Hi :)

I'm having some problems with HD DVD video and mplayer / ffmpeg. I have some HD DVD video files but can't seem to get any audio from mplayer.

I get perfect video providing I specify the ffvc1 codec and from what I understand, the audio should be E-AC-3 yet specifying ffeac3 doesn't work. If I specify -ac ffeac3, mplayer complains that it "Cannot find codec for audio format 0x2000." If I don't specify the audio codec, I get the same complaint which makes me think it's identified it but can't find it. From what I understand 0x2000 *is* E-AC-3.

$ mplayer -vc ffvc1 -ac ffeac3 PEVOB*EVO
MPlayer dev-SVN-r28108-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing PEVOB_1.EVO.
MPEG-PS file format detected.
Searching for VC1 sequence header... found
VIDEO:  VC-1  1920x1080, 29.970 fps, header len: 36
==========================================================================
Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Forced audio codec: ffeac3
Cannot find codec for audio format 0x2000.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
V: 632.3 897/897 61%  6%  0.0% 0 0 
Exiting... (Quit)

I've rebuilt both ffmpeg and mplayer from the instructions on this forum and from what I can tell, ffmpeg has eac3 built in :

$ ffmpeg -formats | grep ac3

FFmpeg version SVN-r16029, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 0 / 52. 6. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec  7 2008 11:18:53, gcc: 4.3.2
 DE ac3             raw AC-3
 DE eac3            raw E-AC-3
 DEA    ac3             ATSC A/52A (AC-3)
 D A    atrac3          Atrac 3 (Adaptive TRansform Acoustic Coding 3)
 D A    eac3            ATSC A/52B (AC-3, E-AC-3)

I guess "DEA" stands for decode, encode, audio? So according to that I should be able to decode eac3.

Does anyone have any ideas as to what's wrong and how I can fix it?

edit: sorry, this is in 8.10

---

### Post by spmurphy on 2008-12-08
Oddly if I take the samples from the mplayer site and play 7_pt_1.eac3 with smplayer, it works and correctly identifies it as EAC3 using ffeac3.

Which I guess leaves me with the question what's the 0x2000 it's complaining about? The files that don't play are the ones where it complains about 0x2000.

---

### Post by Peter Cordes on 2008-12-12
> **spmurphy said:**
> Oddly if I take the samples from the mplayer site and play 7_pt_1.eac3 with smplayer, it works and correctly identifies it as EAC3 using ffeac3.

Which I guess leaves me with the question what's the 0x2000 it's complaining about? The files that don't play are the ones where it complains about 0x2000.

0x2000 is the format id for regular AC3.  See mplayer's codecs.conf.  (the default compiled-in version is installed as /usr/share/doc/mplayer/examples/etc/codecs.conf.gz in the mplayer binary packages).

 I haven't totally figured out eac3 playback, but for eac3 in MKV, you need mplayer -demuxer lavf.  Then mplayer will use ffeac3.  I haven't had much luck with the E-AC-3 in a VC-1 .ts remuxed from an HD-DVD, though.


edit: Your .EVO probably has multiple audio streams, and mplayer is defaulting to one of the plain AC3 ones.  I can play my .ts with -aid 4133, which is the English AC3 in that file.  I haven't been able to play the E-AC-3 stream, but I can watch the movie.  (I also needed -fps 24000/1001 -tsprobe 16000000).

 BTW, mplayer -ac help  lists audio codecs that that mplayer binary has compiled in.  -vc help lists supported video codecs.

---

### Post by mikedep333 on 2008-12-13
Hey,

I thought I'd share with you that I got my copy of king kong playing fairly well under windows with an SVN build of mplayer. Here's my command for it:
```

mplayer -quiet -demuxer lavf -vc ffvc1 -ac ffac3 z:\HVDVD_TS\FEATURE_1.EVO -aid 3

```
Note that you need in general: -demuxer lavf
The ffeac3 audio has been merged into ffac3 so, run : -ac ffac3
Also, it seems like only 2-channel audio streams work. So when you are playing a main evo file, you need to switch through the AID (audio ID I think) streams to find the appropriate one. So run in order:
-aid 0
-aid 1
-aid 2
etc..

I will let you know if I can get a newer build of mplayer to run it on linux.

Here are the win32 builds:
[http://mulder.dummwiedeutsch.de/home/?page=projects](http://mulder.dummwiedeutsch.de/home/?page=projects)

---

### Post by mikedep333 on 2008-12-13
Yes! I got it working.

Here is a repo with the latest mplayer:
deb [http://ppa.launchpad.net/rvm/ubuntu](http://ppa.launchpad.net/rvm/ubuntu) intrepid main
[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)

Here is a page describing it, and linking to the (more) experimental packages.
[http://smplayer.berlios.de/forums/viewtopic.php?pid=3554#p3554](http://smplayer.berlios.de/forums/viewtopic.php?pid=3554#p3554)

Once again, if you are playing King Kong, here is a sample command:
```
mplayer -quiet -demuxer lavf -vc ffvc1 -ac ffac3 ~/KK/HVDVD_TS/FEATURE_1.EVO -aid 3
```
And you need to look at the output to find which AID (audio stream) to use. If you want a simple test, run the logo video and it will default to a working audio stream:
```
mplayer -quiet -demuxer lavf -vc ffvc1 -ac ffac3 ~/KK/HVDVD_TS/DELOGO.EVO
```

I got a lot of my info from here:
[http://forum.doom9.org/archive/index.php/t-133901.html](http://forum.doom9.org/archive/index.php/t-133901.html)

Oh, and expect this to go slow unless you have like a 2.3 ghz core 2 processor. Neither -lavdopts fast:threads=1 nor lavdopts fast:threads=2 worked.

---

### Post by spmurphy on 2008-12-15
Ok, thank you both for your replies.

I noticed that the repository has updated a couple of times since I last built ffmpeg and mplayer, so I'll SVN update, rebuild and have a play with lavf. I thought I'd tried lavf and discarded it as it seemed to lead to jerky playback, that said I don't know what demuxer it uses if you don't specify it.

---

### Post by spmurphy on 2008-12-17
Ok, I rebuilt ffmpeg and mplayer so they're both current.

If I use "-demuxer lavf" I get a very visible pause roughly every second. Perfect frames, it just pauses regularly. I do get audio and can specify the track to listen to. Thinking about it again, I'm pretty sure I had *some* audio before but went a different route because of the, for want of a better label for the semi-regular pause, "stutter."

If I don't specify the demuxer, I get perfect smooth video and no audio. If I specify the demuxer as lavf and specify "-ac ffac3" I get audio and the video stutter.

Any ideas? The machine doesn't look flat out. CPU is at about 27%. If I had to guess, maybe disk throughput? The disk meter seems fairly busy. This is a core duo 8400 @ 3 gig with 4 gig of RAM and striped SATA disks on an AMCC RAID controller.

Anybody have any ideas what kind of horsepower HD DVD decode takes? The film is just under 20 gig for about 2 hour 20 minutes. Isn't that only about 3 meg/s? That doesn't seem earth-shattering! Any idea what's occuring?

---

### Post by mikedep333 on 2008-12-19
You say you're getting 27% CPU Usage. Is that on a quad-core CPU? If it's only using up one core, it would naturally use up roughly 25%.

It seems like based on my experience you would need a fast (2.5 ghz) core 2 processor or so to decode it. I only have a 2.1 ghz and it comes close to it. This is with the audio. Unfortunately it is only using up one CPU core. Decoding it on windows uses a total of 67% CPU power out of 2 cores on my 2.2 ghz athlon 64 x2 system.

---

### Post by spmurphy on 2008-12-23
It's a dual core 3 gig Intel. It doesn't look like it's out of CPU but my experience of Unix (not Linux) says it's usually I/O bound so I was guessing there was something bottlenecking somewhere but I have no idea how to find it :)

There doesn't appear to be any tearing or mangled frames, the audio sounds OK too. I suspected the lavf demuxer but know very little about how mplayer actually works. My suspicion was based purely on the pauses in the video and the fact that if I don't specify it, the picture plays beautifully, *something* just fails to identify what audio it's supposed to play.

---

### Post by spmurphy on 2008-12-23
double post ftl

---

### Post by DudeGreg on 2009-01-17
I am having the same problem as spmurphy. The video briefly pauses every second or so when using the -demuxer lavf option. Without that it runs smoothly. Does anyone have any ideas why?

---

### Post by fenton06 on 2009-03-04
I am also having the same problem, no stutter without specifying the demuxer, but no audio.

---

### Post by devurandom77 on 2009-03-26
The libavformat demuxer is having issues, possibly with the timestamps in the file, resulting in delayed frames.  libavformat can properly demux the eac3 audio though.

The mpegps demuxer mplayer selects by autodetect handles the timing correctly, but can't seem to demux the audio correctly. :(  Forcing the codec to feac3 for format 0x2000 still gives framing errors and no audio.

ffmpeg uses libavformat and reproduces the pausing every ~2 seconds even when recoding.  I've been tinkering with splitting the video stream off with mencoder and remuxing, but I'm having trouble getting the audio to sync.

BTW: playback of full HD at <50% CPU is quite doable if you have an mplayer with vdpau support and a supported NVidia video card + recent OEM drivers.  Some cards support full vc1 decode which could get you to ~5% or less CPU, while others only support partial acceleration, giving you 20-50% single-core CPU usage.  Many of the NVidia cards will support full mpeg and h.264 hardware decode at ~ 5% or less CPU, with h.264 requiring vdpau.  Stock mpeg acceleration has been present in X and the NVidia OEM drivers for well over a year.

> **DudeGreg said:**
> I am having the same problem as spmurphy. The video briefly pauses every second or so when using the -demuxer lavf option. Without that it runs smoothly. Does anyone have any ideas why?

---

### Post by andrew.46 on 2009-03-27
Hi spmurphy,

> **spmurphy said:**
> 

```
$ ffmpeg -formats | grep ac3
```



There is an equivalent syntax that MPlayer uses to identify audio codecs:

```

andrew@skamandros~$ mplayer -ac help | grep ac3
ffatrc      ffmpeg    working   FFmpeg Atrac 3 audio  [atrac3]
ffmac3      ffmpeg    untested  Macintosh Audio Compression and Expansion 3:1  [mace3]
ffac3       ffmpeg    working   FFmpeg AC-3  [ac3]
ffeac3      ffmpeg    working   FFmpeg E-AC-3  [eac3]
hwac3       hwac3     working   AC3 through S/PDIF
hwdts       hwac3     working   DTS through S/PDIF
atrac3      acm       problems  Sony ATRAC3  [atrac3.acm]

```

A couple of false positives in there but you can see the idea :-).

Andrew

---

### Post by dhscaresme on 2009-08-01
> **devurandom77 said:**
> The libavformat demuxer is having issues, possibly with the timestamps in the file, resulting in delayed frames.  libavformat can properly demux the eac3 audio though.

The mpegps demuxer mplayer selects by autodetect handles the timing correctly, but can't seem to demux the audio correctly. :(  Forcing the codec to feac3 for format 0x2000 still gives framing errors and no audio.

ffmpeg uses libavformat and reproduces the pausing every ~2 seconds even when recoding.  I've been tinkering with splitting the video stream off with mencoder and remuxing, but I'm having trouble getting the audio to sync.



Hey d77 and all,

Have you had any luck since the last post here in March?

I'm having the same issues as you--a consistent stutter in the video whenever libavformat is used. I also tried a transcode (from vc-1 evo files to x264 mkv) but to no avail (the evil stutter remained). I was going to demux into two sources like you have done, but I wonder how many times it'll take before I figure it out right!

I'm super new at this so I may not have any good results, but I'll post them anyway. 

Has anybody made any progress?

--dh

Update 08/02/09: I ran just this single EVO file through mkvmerge, taking the english eac3 audio and vc-1 video streams, and putting them into an mkv. So, same streams, but in the mkv container. Playback of the merged mkv is smooth on my 3gig Core 2 without vdpau, still using lavf as the demuxer (obviously). However, on my slower laptop, the stutter is still visible with and without vdpau. Syncing was pretty good, fixed with just delaying the audio about 300ms in mplayer. So maybe strip the eac3 from the evo, convert it to ac3 then merge the orig vc1/new ac3 into an mkv. Then learn all about syncing and the time stuff. Or try to help out the libavformat project! 

Funny thing though on the laptop, with vdpau enabled I have some x264/DTS/mkv files which play very well, a cursory glance at top says that mplayer is using about the same CPU as pulse -- 5%-6% -- with jumps to about 15%. Those are encoded in x264 at 1920x800, profile [email]High@L4.1...and[/email] lots more details... Laptop is Core 2 Duo, 1.5Ghz, 8400M 128MB, nvidia 185.18.14.

---

### Post by devurandom77 on 2009-08-03
Sorry for not following up back to the forum.  The problem with the stuttering video looks to have been a result of an incorrect frame rate.  The code seems to make assumptions about the framerate given the file type, but doesn't compute it from the timestamps.  This seems to wreak havoc with the A/V sync and cause the stuttering problem.

Try adding -fps 24000/1001 to force the 23.97... framerate, or -fps 25 if it's detecting the former but it should be the latter.

Good luck!

---

### Post by dhscaresme on 2009-08-03
> **devurandom77 said:**
> 

Try adding -fps 24000/1001 to force the 23.97... framerate, or -fps 25 if it's detecting the former but it should be the latter.

Good luck!


Hey, thanks for the reply! I came to the same conclusion yesterday afternoon! There sure is a lot to learn about all this stuff, but it's super cool. I've learned a ton in the last two days. 



--dh

---

### Post by Woodpecker83 on 2010-07-26
I just had the same problem and stumbled upon this thread using Google.  Later I found a solution for this:

[PHP]mplayer -nocorrect-pts -demuxer lavf -fps 24000/1001 filename[/PHP]

See also [https://roundup.ffmpeg.org/issue1349](https://roundup.ffmpeg.org/issue1349)

---

