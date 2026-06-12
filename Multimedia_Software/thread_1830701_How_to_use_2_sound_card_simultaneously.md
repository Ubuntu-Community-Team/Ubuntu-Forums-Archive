---
title: "How to use 2 sound card simultaneously"
date: 2011-08-22
forum: Multimedia Software
---

### Post by svkndv on 2011-08-22
My internal sound card is used for Youtube and normal movie watching. Second sound card M-Audio connected to amplifier and speaker which is in living room. 
Most of the time I need to use these sound card simultaneously. I want second sound card to be used with banshee or rhythom box to listen audio and keep the internal sound card for any other default audio usage.

I was able to configure this in windows but in Ubuntu I am unable to configure it. Any help is appreciated.

I have searched and red many thread on this topic none of those have a working solution for ubuntu 11.04

---

### Post by svkndv on 2011-08-22
Any help?

---

### Post by tjones00 on 2011-08-23
This is the "holy grail" it seems of most sound setups. To answer your question it should be possible. However you will have to get down and dirty with your alsa configuration files and probably eliminate pulseaudio.

[http://www.mythtv.org/wiki/Configuring_Digital_Sound](http://www.mythtv.org/wiki/Configuring_Digital_Sound)

Scroll down to 

*It is possible to configure ALSA to output PCM audio simultaneously on  both the analog and the digital outputs.  This means that any 2-channel  audio MythTV decodes will be sent to both outputs.  It does not mean  that you will get AC-3 or DTS through the digital output and analog  audio through the analog output.  To configure ALSA this way, add the  following at the end of the above /etc/asound.conf or .asoundrc file: *

To get an idea about how it should be setup.

---

### Post by svkndv on 2011-08-29
I want use analogue out from both card simultaneously can any one help?

---

### Post by svkndv on 2011-09-01
Now I know why any linux flavor is not popular, Last 5 years i am tried with various distributions of linux and realized one thing it is  not for versatile use. There will be one or other problem always come up and there wont be any solution until unless you get into code level.

May be i will be back in 1-2 years if i could convince myself. until then bye to all. Planning to upgrade to windows 7

---

### Post by hcforde on 2011-09-14
That's funny, I am here because I wan to use multiple sound cards in Windows 7 and can not find a way to do it.  There is no code level there.

---

