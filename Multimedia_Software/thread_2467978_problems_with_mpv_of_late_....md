---
title: "problems with mpv of late ..."
date: 2021-10-14
forum: Multimedia Software
---

### Post by shantiq on 2021-10-14
....    getting this on most youtube HD videos   (fast broadband fine in other areas)

```
mpv https://www.youtube.com/watch?v=ojXqI5AjH-c (+) Video --vid=1 (*) (h264 1920x1080 59.940fps)
 (+) Audio --aid=1 --alang=eng (*) (opus 2ch 48000Hz)
     Subs  --sid=1 --slang=en 'vtt' (webvtt) (external)
     Subs  --sid=2 --slang=es 'vtt' (webvtt) (external)
     Subs  --sid=3 --slang=pt 'vtt' (webvtt) (external)
AO: [pulse] 48000Hz stereo 2ch float
VO: [gpu] 1920x1080 yuv420p
Title: DISCOVER RIO DE JANEIRO &#65533;&#65533;&#65533;&#65533; DOWNTOWN RIO IS UNDERRATED! (TRAVEL BRAZIL)
[COLOR=#800000][I](Buffering) AV: 00:00:00 / 00:36:46 (0%) A-V:  0.001 Cache: 1.0s/883KB
[/I][/COLOR]Saving state.
**[ffmpeg/demuxer] mov,mp4,m4a,3gp,3g2,mj2: Packet corrupt (stream = 0, dts = 84084).**
**[ffmpeg] NULL: Invalid NAL unit size (24758 > 18004).**
[ffmpeg] NULL: missing picture in access unit with size 18008



```

this is my mpv and ffmpeg versions

```
mpv --version

mpv 0.33.0 Copyright © 2000-2020 mpv/MPlayer/mplayer2 projects
 built on Thu Nov 26 06:59:44 UTC 2020
FFmpeg library versions:
   libavutil       56.60.100
   libavcodec      58.112.103
   libavformat     58.64.100
   libswscale      5.8.100
   libavfilter     7.90.100
   libswresample   3.8.100
FFmpeg version: git-2020-11-22-9208b72



```
```
ffmpeg --version

ffmpeg version N-104327-g1902a60dda Copyright (c) 2000-2021 the FFmpeg developers
  built with gcc 9 (Ubuntu 9.3.0-17ubuntu1~20.04)



```[from]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu")


any ideas?    anyone else?

---

### Post by SeijiSensei on 2021-10-14
Plays fine in Mozilla Firefox. In mpv it hangs every couple of seconds.

---

### Post by shantiq on 2021-10-14
> **SeijiSensei said:**
> Plays fine in Mozilla Firefox. In mpv it hangs every couple of seconds.


Exactly!   and going back 2 weeks or so it did not do that. So what could have changed?  it checks now. And if one tries to download it with the program which cannot be mentioned here it stays in &#8776;*883KB* and would take 5 hours instead of the 3 or 4 minutes it would take normally with my bandwidth

Really puzzling ...    thanx for testing SeijiSensei  ...    I use Brave as my main browser and ditto there plays fine ;    but through mpv AND vlc massive buffering and stuttering  

Mindboggling   :KS

---

### Post by DuckHook on 2021-10-14
The problem isn't isolated to *mpv*. I've been getting the same problem on a number of&#8230; ahem&#8230; alternate viewing platforms.

I suspect that Google has done something to its youtube data streams to disrupt alternate platforms. They've been engaged in a long running guerrilla campaign against those of us who value our privacy and I suspect that this is just another iteration of their tricks and subterfuges to force everyone into using only their tracking ecosystem.

---

### Post by TheFu on 2021-10-14
Uh .... ytdl is the issue.  Switching to an alternate version or getting the alpha pre-release version seems to correct this issue.  Saw this on a reddit thread.
So, you have a few choices, but not solved with an apt upgrade or ytdl -U.

---

### Post by shantiq on 2021-10-15
> **TheFu said:**
> Uh .... ytdl is the issue.  Switching to an alternate version or getting the alpha pre-release version seems to correct this issue.  Saw this on a reddit thread.
So, you have a few choices, but not solved with an apt upgrade or ytdl -U.

thank u Fu ....    sort of suspected that much
thanx

---

### Post by SeijiSensei on 2021-10-15
My guess is we might see a new Opus driver from the mpv folks in the near future.

---

### Post by DuckHook on 2021-10-15
Please note that this thread is dangerously skirting the Forum's prohibition against rendering aid with youtube-dl.

Discussion is acceptable. Links to sites or outright instructions are not.

Rather than closing the thread outright, I've already edited some posts to eliminate such links/references, but please don't push the thread further into unacceptable territory.

Thanks to all for your cooperation.

---

### Post by DuckHook on 2021-10-15
Incidentally, I could be wrong but, to my knowledge, mpv does not use youtube-dl, so there is no need to bring it into the discussion.

---

### Post by monkeybrain20122 on 2021-10-15
> **DuckHook said:**
> Incidentally, I could be wrong but, to my knowledge, mpv does not use youtube-dl, so there is no need to bring it into the discussion.

It doesn't if you only watch videos locally. If you stream online it does, but the said python script despite its name works on many sites which don't have eula restrictions.

---

### Post by shantiq on 2021-10-16
> **DuckHook said:**
> Please note that this thread is dangerously skirting the Forum's prohibition against rendering aid with youtube-dl.

Discussion is acceptable. Links to sites or outright instructions are not.

Rather than closing the thread outright, I've already edited some posts to eliminate such links/references, but please don't push the thread further into unacceptable territory.

Thanks to all for your cooperation.


thank you for the editing DuckHook; yes did not realize asking original question it might "stray"  ;     still not got an answer that fixes mpv playing youtube videos properly in 20.04 so my original question remains.   Any other ideas?   Surely one of you knowledge-masters :)

---

### Post by monkeybrain20122 on 2021-10-16
> **shantiq said:**
> thank you for the editing DuckHook; yes did not realize asking original question it might "stray"  ;     still not got an answer that fixes mpv playing youtube videos properly in 20.04 so my original question remains.   Any other ideas?   Surely one of you knowledge-masters :)

Actually it just happened the last couple of days, the issue is not mpv but the app whose name we can't mention and it is only on Youtube (mpv streaming on other sites work fine). I am currently trying to compile mpv from source since there is a way to use an alternative hook for streaming in master but run into a problem because it requires libplacebo >= 3.104.0 :) I will try to compile that or extract it from a .deb :)

---

### Post by shantiq on 2021-10-16
> **monkeybrain20122 said:**
> Actually it just happened the last couple of days, the issue is not mpv but the app whose name we can't mention and it is only on Youtube (mpv streaming on other sites work fine .... :)


yes Monkeybrain on other sites for me Arte Iplayer   no problem   only YT

---

### Post by DuckHook on 2021-10-16
It isn't mentioning youtube-dl that offends forum policy. It is the posting of *any* workarounds that skirt YouTube's Terms of Service. We are not lawyers on this forum and, whether we agree or disagree with YouTube's ToS is immaterial. We cannot risk getting the forums entangled in takedown notices and cease and desist orders. Historically, the only app that worked in this way was youtube-dl, but our policy also extends to other, more esoteric workarounds, so please, everyone, stop dropping hints and dangling alternatives.

Let's not play at semantics just to ignore the spirit of the prohibition.

Incidentally, I know that youtube-dl is useful for downloading from a number of sites that do not prohibit such downloading, so it is to some extent unfortunately named.

@shantiq

Time to stop fishing for solutions/workarounds. Suffice it to say that, to get back the full functionality of mpv for *all* media streams, you will just have to wait until that functionality gets restored in a future upgrade.

---

### Post by shantiq on 2021-10-16
Loud and clear. Fair dues. Thanx Duckhook :)

---

### Post by TheFu on 2021-10-19
> **SeijiSensei said:**
> My guess is we might see a new Opus driver from the mpv folks in the near future.

Opus isn't the preferred audio encoder. Vorbis is with a noticeable difference in sound quality at lower bit rates.  In the last month, I did a bunch of research around this trying to decide which format would best suit my needs (and wither to encode 1200+ audio CDs again).

My goal was to have the best quality, at the smallest file size, which supported my different media catalog systems and playback devices.  Everyone says to rip to FLAC, but then transcode as needed for playback devices and portable devices.  I really wanted to find a container for vorbis files that would read all the metadata tags. Alas, that doesn't appear possible.

I did lots of listening tests from FLAC to mp3, aac, opus, vorbis at a number of different bitrates to determine where my ears could actually here the differences.
I looked at m4a, ogg, mp3, oga, mka, and a few other containers too - mainly for tagging and support by the different library systems.
I dislike apple stuff, so really prefer to avoid m4a and aac. Many people wouldn't care.

FLAC > vorbis >  opus > aac > mp3
I'm seeking indistinguishable from FLAC as my goal for the other encodings and tried to use popular bitrates.  Our ears aren't the same. Our music/audio content tastes are different.
For me, I can't tell the difference between 192kbps and 256kbps mp3, so that's the upper end. I can tell the difference between 160 and 192 mp3 files.
Ok - 192Kbps mp3 is my "gold standard" (though I can hear the difference from FLAC with mp3).
128Kbps opus is just as good as 192Kbps mp3.  Vorbis isn't massively better, but 96Kbps vorbis, can, for some audio types, be heard as different from 128Kbps opus AND 192Kbps mp3.  That means 128Kbps for vorbis is my minimal "perfect" and just in case my ears have issues that others don't have, 160Kbps is what I'll use.  Vorbis and opus both sound "richer" to me than mp3. Higher highs and richer lows. That's probably my bias showing.

I didn't test aac for reasons stated above. Sorry.

As for the containers that were supported, which I would allow on my systems, there was only 1.  mp3.  That is just sad.  So, like many other people, I'm stuck with "good enough, but wasteful mp3.

I didn't bother with .oga or .mka files because they were badly supported for tagging in some system I considered very important. Probably my android players.
Jellyfin supports .opus .ogg .flac and .mp3  Opus seems better supported than vorbis, but the webapp does play vorbis music in .ogg containers.
Plex only supports .mp3.
mpd supports all the encoded types and .opus .ogg .flac and .mp3 containers from what I can tell.
I don't expect Android players to be hiFi - mainly used for car trips, so it isn't like I'll notice the difference (though my car does have a better than nice sound system) with a Memphis Amp and Polk speakers.  

I think the best way for scientific comparisons would be to use frequency analysis for the decoded audio files from the different audio codec encodings.
[https://sound.stackexchange.com/questions/40222/show-the-differences-between-two-similar-audio-files-using-graphical-method](https://sound.stackexchange.com/questions/40222/show-the-differences-between-two-similar-audio-files-using-graphical-method)

For some size information ... sorted 'du' output:
```

5224    ./Brothers_in_Arms/ogg/vorbis/160/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-vorbis-160k.ogg
7696    ./Brothers_in_Arms/mp3/160/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-160k.mp3
8920    ./Brothers_in_Arms/ogg/opus/160/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-opus-160k.ogg
8920    ./Brothers_in_Arms/opus/160/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-160k.opus
9236    ./Brothers_in_Arms/mp3/192/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-192k.mp3
10556   ./Brothers_in_Arms/ogg/opus/192/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-opus-192k.ogg
10556   ./Brothers_in_Arms/opus/192/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-192k.opus
12312   ./Brothers_in_Arms/mp3/256/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-256k.mp3
13820   ./Brothers_in_Arms/ogg/opus/256/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-opus-256k.ogg
13820   ./Brothers_in_Arms/opus/256/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick-256k.opus
30388   ./Brothers_in_Arms/flac/Dire_Straits-Brothers_in_Arms-04-Your_Latest_Trick.flac

```
So ... to me, the smallest file (160Kbps vorbis in an ogg container) sounds identical to the largest file - FLAC.
I like this specific track because it has a mix of rock, jazz, and pop.  You'll note that .ogg and .opus files with Opus encoding are identical sizes.
The FLAC file was the source for all the others, as you may expect.  I used **lame** for mp3 files, **oggenc** for vorbis.  **vorbiscomment** was used for tagging in batch as needed. I used ffmpeg/libopus to create opus/ogg files.

Anyway, hope something finds this helpful.  Got vorbis if you can.  webm video uses vorbis and it supports multi-channel audio nicely, BTW. I know Kodi and VLC have no issue with video that has vorbis audio, but I also know that many video editors refuse to load files that don't have mp2 or aac or mp3 or ac3 audio tracks, so we may need to keep those in the video file while editing.  YMMV with your video editor.

---

### Post by SeijiSensei on 2021-10-20
As the original posting shows, YouTube videos use Opus because it's Google's variant of Ogg Vorbis.

I use flac.

---

