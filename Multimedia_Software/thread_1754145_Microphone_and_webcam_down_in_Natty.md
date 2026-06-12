---
title: "Microphone and webcam down in Natty"
date: 2011-05-09
forum: Multimedia Software
---

### Post by tarahmarie on 2011-05-09
I have a Logitech desktop microphone and a Logitech webcam; neither work in Ubuntu, apparently. I run Kubuntu 11.04 and have been trying for about two months to figure out what the problem is, and so far, I've only seen threads asking about this problem with no solutions posted. Does anyone have a webcam or microphone working in Natty?

---

### Post by tarahmarie on 2011-05-10
bump

---

### Post by lidex on 2011-05-10
This may help with your webcam:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by tarahmarie on 2011-05-12
If any of the documentation would have helped, I wouldn't be having this problem. Assume I've read all the documentation for both webcams and mikes.

So, why would VLC work when I 'open capture device', but Cheese, Skype, and all other apps do not?

---

### Post by lidex on 2011-05-12
> **tarahmarie said:**
> If any of the documentation would have helped, I wouldn't be having this problem. Assume I've read all the documentation for both webcams and mikes.

So, why would VLC work when I 'open capture device', but Cheese, Skype, and all other apps do not?

So the mic does work?
You have pulse audio in your machine?

---

### Post by tarahmarie on 2011-05-12
No, the mic doesn't work; the webcam does, but only in VLC. Yes, I have PulseAudio; I believe it's part of Natty, but I could be wrong.

---

### Post by sparks40 on 2011-05-12
With an ethernet connection, I'm currently using a Logitech camera/microphone (Skype), with the latest updates to 11.04. Just tired it after reading your post and all is working well.

However, I tried to get the same mic/cam working on Xubuntu 11.04 this afternoon and was unable to do so.

Hope that helps.

---

### Post by tarahmarie on 2011-05-12
Are you in Ubuntu or Kubuntu with it working? I'm in Kubuntu.

---

### Post by madjr on 2011-05-12
hm, i've tested about 4 different webcams lately in natty and they all work well (some of them had issues in 10.10)

you could use an ubuntu live-cd or usb , install cheese on it and see if the problem is just with kubuntu.

also not so long ago i used a command to force a cam with skype, i'll see if i can dig that up since i forgot where i found it...

---

### Post by tarahmarie on 2011-05-12
> **madjr said:**
> 

you could use an ubuntu live-cd or usb , install cheese on it and see if the problem is just with kubuntu.


Now THAT is a good idea. I'll let you know how it goes.

---

### Post by lidex on 2011-05-12
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by no2498 on 2011-05-13
i tried my cam in vlc it changed the out put file type
thin cheese and wxcam could not find my cam
i had to reset it in gstreamer-properties 


open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

all of that comes from the cheese help FAQ'S

---

### Post by brandito on 2011-07-06
My mic is not working under Natty either.  Nothing is muted, pulse is showing all of my available input devices... but nothing.  I can listen to music all day, I just can't record anything.

[http://www.alsa-project.org/db/?f=6cc838f9edf091301e360f6d1ed80b9b352dc7ac](http://www.alsa-project.org/db/?f=6cc838f9edf091301e360f6d1ed80b9b352dc7ac)

It was all working in 10... not sure what happened.

---

### Post by no2498 on 2011-07-06
if you have mplayer installed try using guvcview
you need mplayer or it dont work
it finds the mic at least for me it did

---

