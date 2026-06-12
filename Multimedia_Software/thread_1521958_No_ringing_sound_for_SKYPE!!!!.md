---
title: "No ringing sound for SKYPE!!!!"
date: 2010-07-01
forum: Multimedia Software
---

### Post by dzwestwindsor on 2010-07-01
Hey guys,

I installed skype, and all the sound works, except for the fact that it doesn't ring when someone calls me!!! All i see is a little pop up that says someone is calling me, but I cannot hear the ringtone. When i pick up, i hear the other end clearly, there's just no ringtone with someone calls me


Does anyone else have this problem? Does anyone know how to fix it?:confused::confused::confused::confused:


Thanks!

-David

---

### Post by PeterFue on 2010-07-02
It seems removing pulseaudio would help:
[http://forum.skype.com/index.php?showtopic=465571](http://forum.skype.com/index.php?showtopic=465571)
and [http://ronnietucker.co.uk/blog/2010/06/19/ubuntu-skype-pulseaudio-success/](http://ronnietucker.co.uk/blog/2010/06/19/ubuntu-skype-pulseaudio-success/)

I have the same problem (but hoping to find a better solution...)

---

### Post by dzwestwindsor on 2010-07-02
now i dont have a volume slider/icon.

Adding the indicator applet didn't work...

BUT HEY! SKYPE HAS A RING! :D:D:D:D:D:D:D

Thanks a heap!

---

### Post by tibike on 2010-07-06
Here is what I did...
I installed PulseAudio Volume Control from Ubuntu Software Center. In PAVC, in the playback tab I set System Sounds to some value (it was set to 0). 
I hope that helps.

Later edit: actualy, the system sounds can be changed in the Sound Preferences. It's called Alert volume...  :p

---

### Post by cosine352 on 2010-07-09
> **tibike said:**
> Here is what I did...
I installed PulseAudio Volume Control from Ubuntu Software Center. In PAVC, in the playback tab I set System Sounds to some value (it was set to 0). 
I hope that helps.

Later edit: actualy, the system sounds can be changed in the Sound Preferences. It's called Alert volume...  :p

thanks. 
the Alert volume ....the Alert volume ....the Alert volume ....the Alert volume ....:P:P:P:P
it is working now

---

### Post by yannoo on 2013-01-06
I confirm that

  *apt-get install pavucontrol*

then

  *pavucontrol*

(in the terminal) fixes the problem when setting system sounds (first tab, first slider) to 100%.

In fact, in the normal situation, you can hear the skype sounds very faintly when having your volume incredibly high (that's how I got that it was just a question of volume, but I didn't know there was an app specific to pulse audio. Great, many thanks!

---

