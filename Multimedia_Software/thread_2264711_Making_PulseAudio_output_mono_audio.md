---
title: "Making PulseAudio output mono audio"
date: 2015-02-09
forum: Multimedia Software
---

### Post by claesworm on 2015-02-09
I found an earlier 'solved' post in this forum (linked below) that didn't give a satisfying solution to the problem of remapping a stereo output to become a mono output. I found another seemingly better solution, making use of only pulseaudio, and only requiring a one-time change of a config-file (at least concerning your main internal soundcard). 

Original thread: [http://ubuntuforums.org/showthread.php?t=1049371](http://ubuntuforums.org/showthread.php?t=1049371)
Answer based on [https://wiki.archlinux.org/index.php/PulseAudio/Examples#Remap_stereo_to_mono](https://wiki.archlinux.org/index.php/PulseAudio/Examples#Remap_stereo_to_mono) 

**Solution: **

   For every soundcard you want to enable a mono option for - get the pulseaudio registered name of it. This can be done by writing the following in your shell:
```

pacmd list-sinks | grep name:

``` 

Next, for all the soundcards chosen, add the following line to your "/etc/pulse/default.pa" (e.g. use gedit or nano), where you replace the word 'foo' with the soundcards name (seen inside angle-brackets in the previous output):
```

load-module module-remap-sink master=foo sink_name=mono channels=2 channel_map=mono,mono

``` 

The reason for separating these two steps instead of having them in a single command, is to be able to choose the relevant soundcards to enable remapping for. There will emerge one more audio-output per soundcard in your sound-settings (e.g. pavucontrol), and you possibly don't wan't this for all your soundcards. 
Another reason for one not to want this, is if some of the soundcards are external - then they won't neccesarily be connected to the computer all the time; where the pulseaudio server will *fail to start*. 

Other answers, avoiding this last problem are very wellcome..

---

