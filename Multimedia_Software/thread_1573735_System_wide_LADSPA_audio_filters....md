---
title: "System wide LADSPA audio filters..."
date: 2010-09-13
forum: Multimedia Software
---

### Post by [STD]Ein on 2010-09-13
Based on the [PulseAudio equalizer]("http://ubuntuforums.org/showthread.php?t=1308838") I've tried to get my own LADSPA plugins inserted into pulseaudio's chain... and here's what I've got for a compressor


```
### BEGIN: Compressor configuration
load-module module-ladspa-sink sink_name=ladspa_output.dyson_compress_1403.dysonCompress master=alsa_output.default plugin=dyson_compress_1403 label=dysonCompress control=0,1,0.5,0.99
set-default-sink ladspa_output.dyson_compress_1403.dysonCompress
set-sink-volume alsa_output.default 65536
set-sink-mute alsa_output.default 0
### END: Compressor configuration

```

appended to the end of either /etc/pulse/default.pa or ~/.pulse/default.pa

then reset pulseaudio with killall pulseaudio

It properly loads the plugins (I think), it even shows up in the sound preferences as a new output (as "LADSPA Plugin Dyson compressor on Internal Audio"), however it has no effect on the audio output.

Any ideas what's going wrong, or where I can start to debug?
Trying to get a compressor and limiter inserted into my audio chain.

P.S. running Ubuntu 10.04 with all upgrades installed, ladspa-sdk and swh-plugins installed


-----------------------
Edit: It works! Now just to find a limiter that pulseaudio will stomach.

---

