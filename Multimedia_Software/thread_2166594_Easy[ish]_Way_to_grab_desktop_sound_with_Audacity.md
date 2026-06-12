---
title: "Easy[ish] Way to grab desktop sound with Audacity"
date: 2013-08-10
forum: Multimedia Software
---

### Post by shantiq on 2013-08-10
Easy[ish] Way to grab desktop sound with Audacity


Trying to suggest a foolproof way to record with audacity
from line-in ;  music or speech playing on your computer maybe from a music player or a site.

couple of years ago did similar [for sox]("http://ubuntuforums.org/showthread.php?t=1805550")  but many prefer to use a gui like Audacity; so see if this here helps

============

1.   open audacity
2.   set on ALSA  pulse   pulse: Line :0 [from drop down box]


[[IMG]http://s17.postimg.org/hz53oghez/1_audacity_settings_for_line_in_recording.jpg[/IMG]]("http://postimg.org/image/hz53oghez/")



3.   start pavucontrol   [sudo apt-get pavucontrol to install]   and click on recording


4.  Do a dummy run on Audacity to pick right settings on Pavucontrol [record say 10 or 20 seconds so you see settings on Pavucontrol] Pick where it says monitor maybe  "Monitor of internal audio stereo " or as you see in my case with external sound card something a bit different but pick "monitor"  [and do not forget to change it back at the end of your recording]


[[IMG]http://s17.postimg.org/e1htz1uln/2_line_in_audacity.jpg[/IMG]]("http://postimg.org/image/e1htz1uln/")



5. now play your sound source and press red button on Audacity  again do not forget to change pavucontrol setting back at the end of your recording




[URL="http://ubuntuforums.org/showthread.php?t=1805550"]Easy Way to grab desktop sound with Sox
[/URL]

---

### Post by Hylas de Niall on 2013-08-10
I'm not sure, but this old thread might be of help:

[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

Cheers

---

### Post by vedavrata on 2013-10-03
One more method to grab (to record) the screen (the video) and the  sound (the audio) by ffmpeg or by avconv.
The 'monitor' (not  'default' / 'pulse' / 'hw')  should be used as input device.

1. Find the name of the 'monitor':
```
 pactl list sources | grep analog-stereo.monitor
``` Name: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
or
```
 echo $(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)
``` alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
    
2a. **Audio**:
```
 ffmpeg -f pulse -i alsa_output.pci-0000_00_1b.0.analog-stereo.monitor  alsa-output_analog-stereo_monitor.wav 
```
or
```
 avconv -f pulse -i alsa_output.pci-0000_00_1b.0.analog-stereo.monitor  alsa-output_analog-stereo_monitor.wav 
```
2b. **Audio and video**:
```
 ffmpeg -f pulse -ac 1 -i  alsa_output.pci-0000_00_1b.0.analog-stereo.monitor -f x11grab -r 24 -s  1920x1080 -i :0.0 -vcodec libx264 -crf 22 -acodec libmp3lame -ar 22050  -ab 63k grab1.mp4
```
or
```
 avconv -f pulse -ac 1 -i  alsa_output.pci-0000_00_1b.0.analog-stereo.monitor -f x11grab -r 24 -s  1920x1080 -i :0.0 -vcodec libx264 -crf 22 -acodec libmp3lame -ar 22050  -ab 63k grab1.mp4
```

---

