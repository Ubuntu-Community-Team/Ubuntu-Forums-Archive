---
title: "MPEG-1 issues?"
date: 2011-01-25
forum: Multimedia Software
---

### Post by Viper187 on 2011-01-25
I've got a pile of old video files here that identify as MPEG-1 video, MPEG-1 Layer 2 audio. They're ~30 minute vids. They play fine on WMP/MPC under windows, but all 3 players I've tried on linux think the damn things are like a minute long. I don't get it. Totem/SMPlayer/VLC all screw up on these. They play fine for just under a minute and that's it. The info I've retrieved from the files says they were created with TMPGEnc, not that it should matter.

---

### Post by BicyclerBoy on 2011-01-25
Try ffplay..

If it works better then consider fixing by running the files thru' ffmpeg with copy codecs into a new container/file like .mkv

The wmv container is really bad for seeking etc.

---

### Post by Viper187 on 2011-01-25
> **BicyclerBoy said:**
> Try ffplay..

If it works better then consider fixing by running the files thru' ffmpeg with copy codecs into a new container/file like .mkv

The wmv container is really bad for seeking etc.

Nope. ffplay thought the test video was 58 seconds too, as opposed to the 26 minutes it really is.

---

### Post by BicyclerBoy on 2011-01-25
Well ffplay is not a capable as ffmpeg (that is what ffmpeg devs say not me).

Try running one video through ffmpeg into a mkv container.

mkv is probably the best container format as it has the least restrictions on content.

The only wmv stuff I have seen is junky email clips/UTube type stuff. Short & sh#$.
Maximum length was only 3mins.

HandBrake is very capable & nice to use.

---

### Post by FakeOutdoorsman on 2011-01-25
> **Viper187 said:**
> Nope. ffplay thought the test video was 58 seconds too, as opposed to the 26 minutes it really is.

Might be worth trying a recent FFmpeg/ffplay. Development is very active and there may have been a bugfix since the version in the repo.

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Viper187 on 2011-01-26
> **BicyclerBoy said:**
> Well ffplay is not a capable as ffmpeg (that is what ffmpeg devs say not me).

Try running one video through ffmpeg into a mkv container.

mkv is probably the best container format as it has the least restrictions on content.

The only wmv stuff I have seen is junky email clips/UTube type stuff. Short & sh#$.
Maximum length was only 3mins.

HandBrake is very capable & nice to use.

It's only nice to use, if there's a version I don't have to compile myself. Last I saw, that wasn't the case for 10.04

---

### Post by JohnAStebbins on 2011-01-26
> **Viper187 said:**
> It's only nice to use, if there's a version I don't have to compile myself. Last I saw, that wasn't the case for 10.04

It's been available all along for 9.10 thru 10.10 in our nightly build PPA. An announcement for this and links to it have been available in the HandBrake forums.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

A new 0.9.5 release was announced last month
[http://handbrake.fr/](http://handbrake.fr/)

The release PPA also supports 9.10 thru 10.10
[https://edge.launchpad.net/~stebbins/+archive/handbrake-releases](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases)

---

### Post by Viper187 on 2011-01-26
> **JohnAStebbins said:**
> It's been available all along for 9.10 thru 10.10 in our nightly build PPA. An announcement for this and links to it have been available in the HandBrake forums.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

A new 0.9.5 release was announced last month
[http://handbrake.fr/](http://handbrake.fr/)

The release PPA also supports 9.10 thru 10.10
[https://edge.launchpad.net/~stebbins/+archive/handbrake-releases](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases)

Ah. Thank you


> **BicyclerBoy said:**
> Try ffplay..

If it works better then consider fixing by running the files thru' ffmpeg with copy codecs into a new container/file like .mkv

The wmv container is really bad for seeking etc.

How does one use a "copy codec" on Handbrake?

---

### Post by JohnAStebbins on 2011-01-26
> **Viper187 said:**
> How does one use a "copy codec" on Handbrake?
Can you clarify what you mean by "copy codec"?

---

### Post by Viper187 on 2011-01-26
> **JohnAStebbins said:**
> Can you clarify what you mean by "copy codec"?

That's what I was kind of asking the guy who said it. I assume copy the streams without re-encoding.

---

