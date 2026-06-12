---
title: "Sound Coming from Internal and External Speakers"
date: 2010-08-19
forum: Multimedia Software
---

### Post by adam22 on 2010-08-19
I've had this problem with both my newly acquired Logitech headset, and Logitech LS21 2.1 Speakers, as well as regular headphones for listening to music.

I plug the 3.5mm jack in, and the sound comes from the external speakers when they are turned on. But if I turn the volume down from Ubuntu or on the laptop, it turns the external speakers down as well, which wouldnt be a problem, but leaving the master volume max, and turning the external speaker volume with the remote all the way down leaves me with music still coming from the internal speakers.

```
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

```

Using 10.04 64 bit, Gateway NV52

Any advice?

---

### Post by adam22 on 2010-08-19
shamless bump

---

### Post by adam22 on 2010-09-05
For some reason, this no longer happens, but if I turn off the external speakers, then the internal no longer work.

---

### Post by adam22 on 2010-12-30
Answer was provided [here](http://ubuntuforums.org/showthread.php?t=1420711).

---

### Post by pouchette on 2011-01-09
[COLOR=Blue][SIZE=3]
  [/SIZE][/COLOR][COLOR=Blue][SIZE=3]:sad:  Not solved... 
[/SIZE][/COLOR]
[COLOR=Blue][SIZE=3]     
the post was about speakers sound problem : external and internal  sources working together ; external speakers and internal headphones  output playing sounds...
    
and the post 'there' was about micro device not working..
    
or maybe I didn't well understand the issue of the process indicated in this post there related to this one ?
    
which invites to do :
    
  [/SIZE][/COLOR]  gksudo gedit /etc/modprobe.d/alsa-base.conf  
 [COLOR=Blue][SIZE=3]
  [/SIZE][/COLOR]  options snd-hda-intel model=laptop position_fix=1 enable=yes  
 [COLOR=Blue][SIZE=3] I have a pb of output devices (internal and external spk) not a pb of input with microphone device, so what should I do ?
    
usually when you plug micro in the jack entry, external sound from  speakers should automatically shut down.. which is not happen to my  computer and so I don't know how to solve that pb..
  
thanks for your help..
[/SIZE][/COLOR]

---

