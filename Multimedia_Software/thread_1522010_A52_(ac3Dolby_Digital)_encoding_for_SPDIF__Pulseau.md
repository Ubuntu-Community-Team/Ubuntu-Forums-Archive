---
title: "A52 (ac3/Dolby Digital) encoding for SPDIF / Pulseaudio"
date: 2010-07-01
forum: Multimedia Software
---

### Post by mcarans on 2010-07-01
I am using Lucid 10.04 LTS.

I have managed to get A52 encoding through SPDIF to work with Alsa following broadly this guide: [http://www.johannes-bauer.com/linux/dolby/?menuid=3](http://www.johannes-bauer.com/linux/dolby/?menuid=3)

I have struggled to get this to work with Pulseaudio. I have tried a custom default.pa without the hardware autodetection and adding lines like:
load-module module-alsa-source device=WebCamMic source_name=WebCamMic
load-module module-alsa-sink device=HDMI sink_name=HDMI
load-module module-alsa-sink device=Filter_RateConvert sink_name=SPDIF

But the Pulseaudio server complains because of the Filter_RateConvert line with:
E: alsa-sink.c: Assertion 'err != -11' failed at modules/alsa/alsa-sink.c:395, function try_recover(). Aborting.

Please can someone tell me how to get Dolby Digital encoding through SPDIF working with Pulseaudio on Lucid.

---

### Post by mcarans on 2010-07-02
Or put another way, has anyone got A52 (Dolby Digital) encoding through SPDIF working with Pulseaudio in Lucid and if so, how?

---

### Post by tartanpion on 2010-07-31
[http://forum.ubuntu-fr.org/viewtopic.php?id=393194](http://forum.ubuntu-fr.org/viewtopic.php?id=393194)
Need review and some help.

---

### Post by mcarans on 2010-07-31
Hi, I had quick look at your page and it seemed pretty complete, but unfortunately my French is not good enough to understand the detail. I saw that you found the pages I had posted first questions and eventually solutions like [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/348353](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/348353)

The Pulseaudio devs are integrating the code fixes to work with the Alsa A52 plugin that I mentioned into a future release. They also have completed work on AC3 passthrough again for a future release.

---

### Post by tartanpion on 2010-07-31
In short term just for pulseaudio with lucid :
1) ```
sudo add-apt-repository ppa:ricotz/unstable
```2) compile libasound2-plugins
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
download alsa-plugins
```
cd /home/$USER/Downloads/alsa-plugins-*
sudo apt-get install checkinstall
sudo apt-get build-dep alsa-plugins
sudo apt-get install libavcodec-dev
./configure
make
sudo checkinstall --pkgversion "1.0.23+`date +%Y%m%d`-0ubuntu0" --pkgname=libasound2-plugins --showinstall --default

```3) create .asoundrc
```
#####
# Description: To use a52 plugin with PulseAudio. Default value are channels 6 (possibly 2,4,6), bitrate 448 kbit/s by default et sampling fréquency 48000 Hz (possibly 44100 or 48000).
#                Just include this in your ~/.asoundrc .
pcm.a52 {
   @args [CARD]
   @args.CARD {
       type string
       default 0
   }
   type rate
   slave {
       pcm {
           type a52
           bitrate 640
           rate 48000
           channels 6
           card $CARD
       }
       rate 48000
   }
}

```and that all
comment : passthrough not functional yet with pulseaudio

---

### Post by mcarans on 2010-08-01
I think what you posted would work assuming the ricotz unstable repository has the Pulseaudio fixes (I don't know if it does). 

A simpler way though, might be to use the repository that Dan Wood made, described here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/348353/comments/35](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/348353/comments/35)

The  libasound2-plugins will still need to be recompiled either by the way you described or using the Lucid source package which might be a bit easier.

---

### Post by oblib on 2010-11-02
The two responses above me are good, but [here's another thread](http://ubuntuforums.org/showthread.php?t=1608804) I've made with similar instructions (before I found this thread).

---

