---
title: "ALSA and PulseAudio playing from different ports"
date: 2009-04-29
forum: Multimedia Software
---

### Post by Polk1986 on 2009-04-29
OK, I am a bit of a newbie, so I may have missed something here, but I have a problem that a week of perusing the forums has failed to solve. 

I have been building an HTPC and have run into an audio problem. I have an integrated nVidia 9300 card with HDMI out. The video out works on HDMI, and I can get sound from some programs (such as Songbird). However, flash based audio such as Pandora only comes out the regular audio jack. I have a pair of headphones plugged in at the moment to make sure I don't break functionality when editing audio settings. I have installed the newest ALSA (1.0.19), but cannot get the newest PulseAudio to compile properly. 

Is it a problem with Pulse? If I set my sound settings to use HDMI (ALSA) then Songbird works through the HDMI, but on Autoselect, both Songbird and Flash use the audio jack. My full specifications are as follows:

2.5GHz Pentium Wolfdale E5200
Zotac GF9300 D-E Motherboard
4 Gb RAM
Jaunty 32 Bit

Thanks.

---

### Post by markbuntu on 2009-04-29
No need to build those yourself, debs are here for Hardy, Intrepid and Jaunty. Just add the appropriate repo to your sources list and get them with synaptic or apt. (Directions for that are there too.)

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

The new volume control in pulse0.9.15 is way diffeent than previous ones, I think you will like it. 

If you have sound preferences set to autodetect then applications that do not have a native pulseaudio plugin will use either oss or alsa and bypass pulseaudio completely.

You can fix that problem by setting up your sound like this

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by Polk1986 on 2009-05-05
Followed the tutorial and at first nothing happened. I reinstalled 9.04 to undo any changes I had done previously to the audio I had not traced down. After reinstalling and following the tutorial, the audio only worked in the headphones. Finally, I went into 
```
~/.pulse/default.pa
```and changed 

```

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
.endif 

```to 

```
 
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=hw:0,3
#load-module module-alsa-source device=hw:1,0

```as my HDMI device was listed as 0,3.

Now I am enjoying my new Ubuntu HTPC. Thanks, Markbuntu!

---

### Post by mr_raider on 2009-05-22
This should be stickied as I had the same problem on a nvidia 8200 chipset. Pulse does not seem to load the HDMI output as default, even though everything is recognized and working. The fix is quite obscure and it took me 3 days to find.

---

