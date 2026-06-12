---
title: "Ubuntu won't let my Stereo USB Microphone record in stereo."
date: 2011-05-19
forum: Multimedia Software
---

### Post by JpTiger0 on 2011-05-19
I'm using a CAD u37 usb condenser microphone for some semi-pro voiceover work. My clients insist on stereo audio. On my windows machine, my mic works just fine, but it's not in very very good place for recording (a bit too echoey). So I thought I'd use my netbook running ubuntu.

I can plug my mic in, and it does record sound, but there is no available sound profile that allows me to just have two-channels of input. I'm given the following options:

-analog mono input
-(currently selected) Digital Stereo Duplex (IEC958) 
-Digital Stereo (IEC958) Output + Analog Mono Input
-Analog Stereo Output
-Analog Stereo Output +  Analog Mono Input

Can I install a driver or edit a file somewhere that lets me have stereo input? Thanks!

---

### Post by JpTiger0 on 2011-05-23
...anyone?

---

### Post by lidex on 2011-05-25
Looks like your input is mono only perhaps. Not all mic inputs are stereo. But we can take a look. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

