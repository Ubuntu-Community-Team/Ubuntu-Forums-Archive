---
title: "microphone disappears when running webcam on HP, Lucid :("
date: 2010-05-10
forum: Multimedia Software
---

### Post by AleNavigator on 2010-05-10
Hey everyone,

I just installed ubuntu lucid x64 on an HP dv7-3065dx and even though the installation went pretty smoothly, every time I open cheese or anything else that uses the webcam, the microphone all of a sudden cuts off. It doesn't receive input. However if I use the microphone without camera then the microphone works.... Is the webcam somehow crashing the microphone?? Is there something wrong with pulseaudio? The webcam works great and is recognized as "HP Webcam".  I really need this to work for skype. Any suggestions would be much appreciated.

Thank you in advance

---

### Post by User3k on 2010-05-10
Do you mean a microphone plugged into your sound card? Does your webcam have a built in USB microphone? If it has a built in Microphone that may be where your problems are coming from. It could be choosing the webcam microphone first.

---

### Post by AleNavigator on 2010-05-10
Thank you for replying and yes it does have a webcam microphone. It works if I dont use the webcam. However if I start the webcam, neither the internal mic nor an external plugged in the microphone jack will work.Is that helpful?

---

### Post by no2498 on 2010-05-10
look in synaptic first i think this is in it

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

also comes in a deb file

read the page first install all it tells you to

---

### Post by AleNavigator on 2010-05-10
Unfortunately the deb file doesnt work because its only for x86 and the compilation gives


libtool: link: unsupported hardcode properties
libtool: link: See the libtool documentation for more information.
libtool: link: Fatal configuration error.
make[1]: *** [wxcam] Error 1
make[1]: Leaving directory `/home/user/Desktop/wxcam-1.0.5/src'

this output.... What does this program do anyway?

---

### Post by AleNavigator on 2010-05-10
> **AleNavigator said:**
> Unfortunately the deb file doesnt work because its only for x86 and the compilation gives


libtool: link: unsupported hardcode properties
libtool: link: See the libtool documentation for more information.
libtool: link: Fatal configuration error.
make[1]: *** [wxcam] Error 1
make[1]: Leaving directory `/home/user/Desktop/wxcam-1.0.5/src'

this output.... What does this program do anyway?

Got it installed with a simple reboot and recompilation.... Ran the program and then tested the mic. Still the problem persists :(
Are there any other suggestions?

---

### Post by AleNavigator on 2010-05-11
Bump...

---

### Post by no2498 on 2010-05-11
you just need to play with the sound some 
i have never had a problem with wxcam

i will say do not get rid of cheese it has all the settings for webcams ubuntu give it to them

hope you get it working

---

### Post by AleNavigator on 2010-05-14
I won't remove cheese however, I have installed alsamixer and played with the sound settings there..... I really cannot understand why the microphone dies out every time I decide to turn the camera on. For example, if I open cheese, the cam works fine... then when I try to see if the mic has sound in pulseaudio, it doesnt. How can they be related? Does anyone have any ideas? Thank you advance!

---

### Post by AleNavigator on 2010-05-16
Bump? :(

---

