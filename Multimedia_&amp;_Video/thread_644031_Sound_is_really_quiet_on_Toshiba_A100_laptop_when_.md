---
title: "Sound is really quiet on Toshiba A100 laptop when running Ubuntu 7.10 Gusty"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by ahart8 on 2007-12-18
Hey guys im running Gusty 7.10 on my toshiba A100 laptop and i cant figure out why my sound is so quiet. I installed ubuntu about a month ago and have been trying to work out all the bugs and things it but i can't find a definate solution to my sound problem. I have gone through tons of forums and tried many things to fix it like getting alsamixer and making sure the volume was maxed but nothing seems to solve it. My computer did have sound working properly for a while but then after a restart it went back to being really quiet. If anyone has a good idea how help me it would be greatly appreciated. 
Sound card: Realtek ALC861

---

### Post by Poizhan on 2008-03-16
Hey, try this!

```
cd /etc/init.d
```
Create a new text file:
```
sudo gedit soundstartfix
```
Text to stick in:
```
#!/bin/bash
kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*)
sudo modprobe -r snd-hda-intel && sudo modprobe snd-hda-intel model=auto
```
Save, then close the text editor.

Now you need to make it start by chmoding it.
```
sudo update-rc.d soundstartfix defaults

(Wait for it to finish, then:)

sudo chmod +x soundstartfix
```

---

### Post by mssg131187 on 2008-04-19
I had the same problem now its working just fine just go the following link and follow the instructions:
[http://ubuntuforums.org/showthread.php?t=373287&highlight=toshiba+a100+sound&page=4](http://ubuntuforums.org/showthread.php?t=373287&highlight=toshiba+a100+sound&page=4)

---

