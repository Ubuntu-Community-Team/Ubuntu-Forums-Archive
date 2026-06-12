---
title: "Help getting the A52 plugin for pulseaudio working in 12.10"
date: 2012-10-27
forum: Multimedia Software
---

### Post by liamoshan on 2012-10-27
Hi,

In 12.04 (and probably previous versions), I have been using the a52 pulse plugin described in [https://help.ubuntu.com/community/DigitalAC-3Pulseaudio]("https://help.ubuntu.com/community/DigitalAC-3Pulseaudio") to allow me to output 5.1 channels over SPDIF from the ALC887 device. 

This was all working fine, but since the upgrade to 12.10, something has broken.

I attempted to follow the instructions in the link above (which is admittedly for 12.04) to rebuild the plugin, but the first line:
```
sudo apt-get build-dep libasound2-plugins
```
results in
```
Picking 'alsa-plugins' as source package instead of 'libasound2-plugins'
The following packages have unmet dependencies:
 libjack-dev : Depends: libjack0 (= 1:0.121.3+20120418git75e3e20b-2) but it is not going to be installed
E: Build-dependencies for libasound2-plugins could not be satisfied.
```
It seems a dependency for libjack0 is uninstalling the mplayer package, which doesn't seem like the right path.

I tried to forge ahead and build the plugin anyway, hoping it would work out, and it seemed to build OK - here's the output from ./configure
```
Plugin directory: /usr/lib/alsa-lib
ALSA_CFLAGS: -I/usr/include/alsa  
ALSA_LIBS: -lasound  
JACK plugin:        no
Pulseaudio plugin:  yes
  pulseaudio_CFLAGS: -D_REENTRANT  
  pulseaudio_LIBS: -lpulse  
Samplerate plugin:  yes
  samplerate_CFLAGS:  
  samplerate_LIBS: -lsamplerate  
Maemo plugin:       no
  Using Osso resource manager: no
A52, lavc plugins:  yes
  AVCODEC_CFLAGS:  
  AVCODEC_LIBS: -lavcodec  
  AVCODEC_HEADER: <libavcodec/avcodec.h>
Speex rate plugin:  lib
Speex preprocess plugin:  yes
```
It seems to have found what it needs to build the A52 plugin. I followed the rest of the instructions and replaced the A52 plugin, and it *almost* works.

Working: 
[LIST]
[*]The "Digital Surround 5.1 (IEC958/AC3) Output" hardware profile shows up under Sound Settings. 
[/LIST]
Sorta Working:
[LIST]
[*]The "Test Speakers" in Sound Settings works, apart from the "Front center" speaker, which outputs to the Front Left and Front Right speakers (I can live with this)
[*]Banshee / Rhythmbox / Firefox can play audio... for a while. After a couple of minutes, media players start skipping wildly through tracks. This sucks
[*]Totem / VLC can play videos with 2 channel MP3/whatever audio
[*]The volume randomly resets itself to maximum
[/LIST]
Not working at all:
[LIST]
[*]Totem / VLC will not play videos with AC3 sound at all. Totem locks up at the first frame, VLC plays video with no audio. The pulseaudio process goes crazy, maxing out a CPU core until the player is closed
[/LIST]

If I disable my /etc/asound.conf by renaming it, and don't use the A52 plugin, all these issues go away, but I'm left with only PCM Stereo as an output option, which sort of defeats the purpose of having a surround system.

I'm afraid I've hit the limit of my knowledge, any help is greatly appreciated! :)

---

### Post by DennisVis on 2012-11-21
I'm also struggling with installing the plugin on 12.10. I to have stereo sound over my spdif output. I followed the steps in the tutorial, building the plugin went fine and I did not recieve the errors you posted. 
I could not find the 2 files that needed to be copied to the alsa library however, so I had to extract one of the tar.gz packages and use make on that one. After that there was a a52/.lib folder with the two files. 
When editing the /etc/asound.conf file I actualy created a new one. This is probably the reason why it's not working for me as I did not get the extra settings after I restarted alsa and pulseaudio. Did you find the asound.conf file directly under /etc/ ?

Sorry I don't have your answer. If I can be usefull to you in any way, please let me know!

---

### Post by BicyclerBoy on 2012-11-21
This plugin is an alsa plug device that pulse audio can enumerate & use.

Note that you only need this a52 encoder plugin to create AC3 output from stereo or multi-channel PCM.

You don't need this plugin to output AC3/DTS from recordings with AC3/DTS etc.

This plugin is useful for gamers to get 5.1 over spdif from games that can not drive iec958 output directly..

A lot of players have this AC3 encoder built-in (VLC, mythtv, XBMC etc)

---

### Post by Fisslefink on 2013-02-18
The a52 plugin is now packaged separately on apt for 12.10.  This makes installation **MUCH EASIER** and no compiling needed.  It worked for me.

Try this:

```
sudo apt-get install libasound2-plugins-extra
sudo /sbin/alsa force-reload
```

If you want to force Dolby AC3 sound 100% of the time, as I did, check out this post:
[http://www.crutzi.info/xbmc-simultaneous-spdif-and-hdmi-surround-sound](http://www.crutzi.info/xbmc-simultaneous-spdif-and-hdmi-surround-sound)

After creating the asound.conf as described in that blog post, you should be able to test Dolby output with this command:
```
speaker-test -t wav -c 6 -l 1 -D pcm.a52encode
```
 or 
this command:
```
wget http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3
mplayer -ao alsa:device=spdif -ac hwac3 www_lynnemusic_com_surround_test.ac3 -loop 0
```
(the "Dolby Digital" light on your receiver should light up during both of these tests).

---

### Post by BicyclerBoy on 2013-02-19
> mplayer -ao alsa:device=spdif -ac hwac3 ...

Note that has no dependency on the a52 plugin..but is a good test that AC3 pas-thru' over S/PDIF is working.

---

