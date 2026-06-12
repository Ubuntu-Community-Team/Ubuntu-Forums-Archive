---
title: "Problems skipping through wma files even with restricted formats installed."
date: 2010-11-23
forum: Multimedia Software
---

### Post by Dáire Fagan on 2010-11-23
I can play WMAs with MPlayer but when I try to skip forward a few minutes it plays for a split second, and then plays at another random part of the video making it impossible to play a WMA from anywhere but the beginning. 

```

mplayer -demuxer lavf ccent01.wmv
```The above command opens the video but there is no menubar, scroll bar, or any reaction to right click although strangely scrolling my mouse wheel seems to randomly skip through the video.

In VLC when trying to play the same file I get the error:

```
No suitable decoder module:
 VLC does not support the audio or video format "wmas". Unfortunately there is no way for you to fix this.
 No suitable decoder module:
 VLC does not support the audio or video format "MSS2". Unfortunately there is no way for you to fix this.

```After converting the .wma file to .mpg, and also .avi using a command similar to:

```
mencoder ccent01.wmv -ofps 23.976 -ovc lavc -oac copy -o ccent01.mpg
```There is no change playing the file with mplayer and in VLC it now only gives one error:

```

No suitable decoder module:
  VLC does not support the audio or video format "wmas". Unfortunately there is no way for you to fix this.
 
```I'm preparing for a Cisco exam later in the week and would like to spend tomorrow watching hours of computer based training videos but would rather not have to do it in Windows. Already tried using Media Player Classic in WINE but it crashed. Is there a workaround?

Oh and I already have ubuntu-restricted-extras installed.

Thoughts, comments, suggestions?

---

### Post by mc4man on 2010-11-24
Pretty simple - though in this case you should be posting what ubuntu release you're using and as far as vlc what vlc.

For MSS2 your best and most likely only option is a 32 bit mplayer. As far as navigating MSS2, probably not going to happen, if necessary then use windows

As far as wmas(voice), at this point almost all players can decode thru ffmpeg (libavcodec

If you're using maverick support is default enabled in gstreamer and vlc. If on lucid then for gstreamer support adding this ppa and updating the gstreamer plugins (the ffmpeg one in particular) will add wmas support.
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

(noting that if on 32 install one must remove the the gstreamer0.10-pitfdll plugin if installed or it will prevent wmas decoding

As far as vlc and wmas - any version from 1.0.X and up can decode wmas thru avcodec but it needs to be built to do so and off of a libavcodec that supports

Ex. vlc 1.0.6 in lucid, rebuilt here for support
> 
VLC media player 1.0.6 Goldeneye
..........................
[0x9a795a0] asf demux debug: added new audio stream(codec:0xa,ID:1)
0xb7106420] avcodec decoder debug: libavcodec initialized (interface 0x344200)
[0xb7106420] avcodec decoder debug: ffmpeg codec (Windows Media Audio Speech) started
[0xb7106420] avcodec decoder debug: Using 192000 bytes output buffer
[0xb7106420] main decoder debug: using decoder module "avcodec"

Don't know about any lucid or before vlc ppa's, the ubuntu repo vlc's prior to maverick will not support wmas, probably the same for any ppa that doesn't replace your shared ffmpeg libs.

---

### Post by Dáire Fagan on 2010-11-24
> **mc4man said:**
> Pretty simple - though in this case you should be posting what ubuntu release you're using and as far as vlc what vlc.

For MSS2 your best and most likely only option is a 32 bit mplayer. As far as navigating MSS2, probably not going to happen, if necessary then use windows

As far as wmas(voice), at this point almost all players can decode thru ffmpeg (libavcodec

If you're using maverick support is default enabled in gstreamer and vlc. If on lucid then for gstreamer support adding this ppa and updating the gstreamer plugins (the ffmpeg one in particular) will add wmas support.
[https://launchpad.net/~gstreamer-developers/+archive/ppa]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa")

(noting that if on 32 install one must remove the the gstreamer0.10-pitfdll plugin if installed or it will prevent wmas decoding

As far as vlc and wmas - any version from 1.0.X and up can decode wmas thru avcodec but it needs to be built to do so and off of a libavcodec that supports

Ex. vlc 1.0.6 in lucid, rebuilt here for support

Don't know about any lucid or before vlc ppa's, the ubuntu repo vlc's prior to maverick will not support wmas, probably the same for any ppa that doesn't replace your shared ffmpeg libs.

Thanks for the response.

I use VLC 1.0.6 Goldeneye and Ubuntu 10.04.

I just installed the PPA for gstreamer plugins and updated, still getting the WMAS error in VLC when trying to play the video and audio. Because I'm using a 32 bit system before trying I removed pitfdll via synaptic package manager by clicking on 'remove' rather than 'completely remove'.

I'm not sure where to go from here, if I upgrade to maverick do you think it will just work?

---

### Post by mc4man on 2010-11-24
> I just installed the PPA for gstreamer plugins and updated, still getting the WMAS error in VLC
vlc does not use gstreamer, for wmas on vlc, *as mentioned*, you'll need to either to build your own or use a ppa that updates your ffmpeg libs, typically backporting them from maverick (ffmpeg 0.6.1

Using the backported ffmpeg libs may break some support on existing apps.
(though that can be addressed for the most part, some of these ppa's do also offer updated packages that could be affected.

(your current gstreamer ffmpeg plugin from the dev's ppa no longer depends on lucid's ffmpeg shared libaries and would not be affected

The MMS2 that you converted to .mpg should be now be playable in totem, though navigation will most likely be no better than mplayer and playback would possibly be worse

---

### Post by Dáire Fagan on 2010-11-25
> **mc4man said:**
> vlc does not use gstreamer, for wmas on vlc, *as mentioned*, you'll need to either to build your own or use a ppa that updates your ffmpeg libs, typically backporting them from maverick (ffmpeg 0.6.1

Using the backported ffmpeg libs may break some support on existing apps.
(though that can be addressed for the most part, some of these ppa's do also offer updated packages that could be affected.

(your current gstreamer ffmpeg plugin from the dev's ppa no longer depends on lucid's ffmpeg shared libaries and would not be affected

The MMS2 that you converted to .mpg should be now be playable in totem, though navigation will most likely be no better than mplayer and playback would possibly be worse

VLC was giving the wmas and mms2 error for the same single .wma file. I am a novice and would not know where to begin to build my own. Do you know where I can find a ppa that updates ffmpeg libs, backporting them to maverick ffmpeg 0.6.1? Or again, would simply upgrading solve this problem? If it's going to risk breaking existing apps should I just not do this? Is it more trouble than it's worth and should I just log onto Windows for the day to study?

The mms2 i converted to .mpg is again the same single file I've addressed in the past, there is only one original file the .wma, to which I have tried converting to .mpeg. Playing it in totem now and the sound is distorted and you're right, navigation is no better.

---

### Post by no2498 on 2010-11-25
try this it loads some more 264 ff files
type smplayer in a terminal
it tells you how to install it

hope that helps with no hoops

---

