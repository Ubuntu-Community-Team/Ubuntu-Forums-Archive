---
title: "no usb audio in feisty fawn"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by treeby on 2007-04-30
Hi i just got a new computer and installed feisty fawn. a lot of things work okay but
one big thing is that i can't get the sound to work. in the settings, when i do a test beep,
it will beep. but if i play an audio file or make any other sounds...nothing. i installed the mp3
codecs and everything so i know that's not a prob. i get sound in my vista dual boot and i had
sound on feisty with my old computer and the same speakers. so i'm not sure what the prob. is.
anyone have any ideas? thanks much!

---

### Post by treeby on 2007-04-30
bump

please i swear to god if you can help me to get these working i'll mail you a present or something...
anything...

i've tried both of these guides to no avail
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/archive/index.php/t-297835.html](http://ubuntuforums.org/archive/index.php/t-297835.html)

it recognizes the usb audio (and my other sound cards) i can get the beep...but no other sound 
from anything...not even system sounds

if you can help me i will be SO SO thankful..i've spent already around 2 hours or more trying to get
this..i don't want to give up on ubuntu...but if i have no sound..i don't really have a choice.
thanks
here's what it says when i do the apllay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: speak [Saitek A-250 wireless 2.1 speak], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


THANK YOU:confused:

---

### Post by kaede on 2007-05-01
try to install automatix and install all the multimedia codec :D

---

### Post by treeby on 2007-05-01
i did that....like i said..i get no system sounds either. it's not just an mp3 thing. thanks for your help, though. any other ideas?

---

### Post by treeby on 2007-05-01
ok solved my own problem if anyone's curious...
i went into bios and disabled the HD Audio Controller....
unfortunately now i can't control the volume from my computer only from the speaker
but whatever..i have sound!

---

