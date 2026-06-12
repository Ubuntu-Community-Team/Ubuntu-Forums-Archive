---
title: "laptop and external speaker problem"
date: 2009-10-28
forum: Multimedia Software
---

### Post by finmanrushfan on 2009-10-28
i was having a problem with having sound only from external jacks(headphones and external speakers) but getting nothing from the laptop speaker.  i found a solution at 

[http://rforge.wordpress.com/2009/08/22/no-sound-on-hp-elitebook-with-ubuntu-jaunty/](http://rforge.wordpress.com/2009/08/22/no-sound-on-hp-elitebook-with-ubuntu-jaunty/) 

which basically says to

Open alsa-base.conf with any texteditor (here ‘gedit’) by typing
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
in the terminal.

Then add a line
```
options snd-hda-intel enable_msi=1 single_cmd=1 model=laptop
```

at first this seemed to solve the problem, however, after this ONLY the laptop speaker worked, whenever an external device was plugged in, only the laptop speaker continued to function. is there a way to configure ubuntu to switch back and forth between external/internal speakers (as one would expect it to)?

---

