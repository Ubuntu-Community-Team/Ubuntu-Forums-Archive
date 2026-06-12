---
title: "How to use webcam microphone as default?"
date: 2013-08-13
forum: Multimedia Software
---

### Post by chilloutmo on 2013-08-13
Hi everyone, 

In order to use my usb webcam microphone with skype I have to go to sound settings and change the input source manually every time I plug it in. I intuitively tried rearranging the default sound card microphone and the webcam one via drag and drop in the hope of being able to define a priority, but with no luck. 

It's really annoying that instead of just plugging in the webcam and it sets itself automatically as sound input, I have to go through the settings every time. Is there any way to make my webcam microphone the default sound input? I can't do it within skype because skype just shows "pulse audio driver" whether I use the built-in mic or the webcam one, it basically just uses whatever the ubuntu system is currently using.

I searched a bit online and all I could find was a post from 2011 ([http://askubuntu.com/questions/31206/how-can-my-audio-input-always-be-the-webcam-microphone](http://askubuntu.com/questions/31206/how-can-my-audio-input-always-be-the-webcam-microphone)) (so I don't know if it's outdated) and honestly it's really a bit complicated and a big effort for a thing that should be relatively easy for the end user to change. 

Any help would be greatly appreciated!

Best,

chilloutmo

---

### Post by Yellow Pasque on 2013-08-13
Yes, it should be easier, but it's not...

Anyway, try the udev solution. You only have to do it once : [http://askubuntu.com/a/115575](http://askubuntu.com/a/115575)
If you need help, get the output of pacmd and lsusbr:
```
sudo update-usbids
***plug in webcam***
lsusb
pacmd list-sources
```

---

