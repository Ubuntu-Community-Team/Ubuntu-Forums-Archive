---
title: "if you grab(record) screen(video) and sound(audio) by ffmpeg/avconv and no sound then"
date: 2013-10-03
forum: Multimedia Software
---

### Post by vedavrata on 2013-10-03
if you are triyng to grab (to record) the screen (the video) and the sound (the audio) by ffmpeg or by avconv and there no speaker sound (and only sound from microphone), then you should record the 'monitor', not 'default'/'pulse'/'hw':

1. Find the name of the 'monitor':
```
 pactl list sources | grep analog-stereo.monitor
```
    Name: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
or
```
 echo $(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)
```
alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
    
2a. Audio:
```
 ffmpeg -f pulse -i alsa_output.pci-0000_00_1b.0.analog-stereo.monitor  alsa-output_analog-stereo_monitor.wav 
```
or
```
 avconv -f pulse -i alsa_output.pci-0000_00_1b.0.analog-stereo.monitor  alsa-output_analog-stereo_monitor.wav 
```
2b. Audio and video:
```
 ffmpeg -f pulse -ac 1 -i alsa_output.pci-0000_00_1b.0.analog-stereo.monitor -f x11grab -r 24 -s 1920x1080 -i :0.0 -vcodec libx264 -crf 22 -acodec libmp3lame -ar 22050 -ab 63k grab1.mp4
```
or
```
 avconv -f pulse -ac 1 -i alsa_output.pci-0000_00_1b.0.analog-stereo.monitor -f x11grab -r 24 -s 1920x1080 -i :0.0 -vcodec libx264 -crf 22 -acodec libmp3lame -ar 22050 -ab 63k grab1.mp4
```

---

