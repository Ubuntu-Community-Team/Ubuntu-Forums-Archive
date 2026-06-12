---
title: "Winff"
date: 2012-02-15
forum: Multimedia Software
---

### Post by donsmouse on 2012-02-15
i am using recordmy desktop to record screencasts in ubuntu 11.10, i have a radeon hd 4250 graphics card with the latest drivers installed
now when i convert my screencast to avi the menus and other things in the video look garbled up you cant make out the menu items in the video
what is causing this is there a way to work around this?

Any help would be appericiated thank you

---

### Post by ron999 on 2012-02-15
> **donsmouse said:**
> now when i convert my screencast to avi the menus and other things in the video look garbled up you cant make out the menu items in the video
what is causing this is there a way to work around this?


Hi
WinFF/FFmpeg sometimes has a problem converting those ogv files:(
Try using MEncoder instead.:)
```
sudo apt-get install mencoder
```
This is a simple command to start with:-
```
mencoder filename.ogv -o filename.avi -ovc lavc -oac mp3lame
```

If it works OK, find a GUI program to use with MEncoder.
Such as this one ---> [http://code.google.com/p/foxoman/downloads/detail?name=divxconverter_2.0.1-1_all.deb&can=2&q=]("http://code.google.com/p/foxoman/downloads/detail?name=divxconverter_2.0.1-1_all.deb&can=2&q=")
but there are others.

---

### Post by donsmouse on 2012-02-15
ok i will try that,tahnk you so much

---

### Post by donsmouse on 2012-02-15
ok i tried the mencoder thing and the videos still look a little garbled in the menus and stuff

so now what can i do??

---

### Post by ron999 on 2012-02-15
> **donsmouse said:**
> 
so now what can i do??
I dunno.:confused:
Wait and see if somebody else has an idea.:)

---

### Post by donsmouse on 2012-02-15
ok thank you

---

### Post by bcarlowise on 2012-02-15
I tested recording a video with RecordmyDesktop and then attempting to convert the video to avi format using mencoder. I too find problems with the conversion no matter what type of format I try converting the video to. It seems to me that RecordmyDesktop is doing some strange things with the video. Conversion of teh ogv files always results in "duplicate frames" which get dropped and result in pixelated, crappy video conversions. My recommendation is to stop using RecordmyDesktop and use XVid instead. You can specify what format you want to recording to be saved in. The default is mpeg but my subsequent conversion from mpeg to avi using mencoder worked flawlessly. Hope this helps.

---

### Post by donsmouse on 2012-02-15
ok thank you i will give it a try

---

### Post by FakeOutdoorsman on 2012-02-16
> **donsmouse said:**
> what is causing this is there a way to work around this?

What version of Ubuntu are you using? What WinFF device and preset settings did you use? Does the ogv from recordmydesktop look bad before you convert it? Try playing it with ffplay and see what it looks like:
```
ffplay video.ogv
```

---

