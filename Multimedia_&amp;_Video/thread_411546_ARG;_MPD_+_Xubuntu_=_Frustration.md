---
title: "ARG; MPD + Xubuntu = Frustration"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by digbybare on 2007-04-17
So, I'm relatively new to linux. I decided to install Xubuntu because it seemed light and user-friendly. With the help of various internet guides and such, I've been slowly getting everything to work.

Except MPD. At first, I was following: [http://ubuntuforums.org/showthread.php?t=320469&highlight=mpd](http://ubuntuforums.org/showthread.php?t=320469&highlight=mpd) . When I executed "./autogen.sh", I got the following: ```
########### MPD CONFIGURATION ############

 Playback Support:
 libao support .................disabled
 OSS support ...................enabled
 ALSA support ..................disabled
 JACK support ..................disabled
 OS X support ..................disabled
 PulseAudio support ............disabled
 Media MVP support .............disabled
 Shout streaming support .......disabled

 File Format Support:
 ID3 tag support ...............disabled
 mp3 support ...................disabled
 Ogg Vorbis support ............disabled
 FLAC support ..................disabled
 OggFLAC support ...............disabled
 Wave file support .............disabled
 MP4/AAC support ...............disabled
 Musepack (MPC) support ........disabled
 MOD support ...................disabled
configure: error: No input plugins supported!
```
I didn't really pay much attention to these error messages, and kept following the guide. Make and make install both seemed to work. I followed the rest of the guide for MPD up until it told me to run MPD. I executed "sudo mpd" and got the following: ```
unable to bind port 6600: Address already in use
maybe MPD is still running?

```
I looked around, and in the process of finding the solution, I ran into [http://mpd.wikia.com/wiki/Install#Ubuntu_Install_Procedure](http://mpd.wikia.com/wiki/Install#Ubuntu_Install_Procedure) and tried doing that. It did not fix the problem. However, "sudo killall mpd" did. But when I tried to run mpd again, it alternately gave me ```
cannot setgid for user "mpd" at line 188: Operation not permitted

``` if I didn't run as superuser, or if I executed "sudo mpd" it gave me ```
No audio_output specified and unable to detect a default audio output device

```

I tried playing around with the mpd.conf, uncommenting the secion on alsa drivers, etc. but it did nothing except show me a wide variety of error messages. Finally I went into Synaptic, removed mpd, and tried following [http://ubuntuforums.org/showthread.php?t=31763&highlight=mpd](http://ubuntuforums.org/showthread.php?t=31763&highlight=mpd) . But, when I typed "sudo dpkg-reconfigure mpd" into console, it just paused briefly, before returning me to the command prompt. I'd very much like to get this up and working, but as it is, I have no idea what to do.

I'm running Xubuntu 6.10, I have a Creative Audigy 2 ZS Notebook soundcard with alsa drivers installed, which as far as I can tell are working. I have gxine and rhythmbox currently installed, and both work after I followed [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to install the codecs.

Any help would be GREATLY appreciated.

---

### Post by 3dxtrip on 2007-04-21
You need dev packages for compile audio support, when you install this packages, you should see ENABLE where says DISABLE.

Else, you can use Synaptic for install easily MDP compiled, ready to use

---

### Post by digbybare on 2007-04-22
Alright, thanks, I got mpd up and running now.

---

