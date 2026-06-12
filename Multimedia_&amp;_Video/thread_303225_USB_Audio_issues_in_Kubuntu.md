---
title: "USB Audio issues in Kubuntu"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by groggyboy on 2006-11-19
I have Logitech V20 external usb speakers for my laptop.  I installed them in Ubuntu, and they were recognized easily.  I've since uninstalled Ubuntu and switched to Kubuntu.  When I plug them in now, nothing happens.  System sounds and amarok still play through the laptop's built-in speakers.

I've poked around Kmix and Sound System in KControl.  I've gotten as far as being able to select USB Audio in Kmix, but it doesn't seem to affect anything.

Any ideas?

---

### Post by groggyboy on 2006-11-19
quick update: i can get sound in amarok by a) setting system sound in KControl to OSS, and b) switching amarok's sound engine to oss and setting the device to /dev/sound/dps.

i wish i didn't have to use OSS tho.  ubuntu was so easy...

---

### Post by groggyboy on 2006-11-20
*bump*

any ideas how to get my usb speakers working in KDE without having to switch to OSS in all my apps?

---

### Post by groggyboy on 2006-12-01
*bump*

i still haven't found any adequate solutions.  anyone have any idea how to configure Kubuntu to use USB speakers?

---

### Post by deltafoxtrot on 2007-01-29
Check out this link: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard").  Worked for me (I'm also using the Logitech V20 speakers). 

```
$ sudo asoundconf list
Names of available sound cards:
ICH6
Speaker

$ sudo asoundconf set-default-card Speaker
```

Presto chango...  Restart any apps requiring a soundcard that may have been open prior to changing the default.

Good luck!

---

### Post by groggyboy on 2007-02-13
sorry for the late reply...

thanks!  that's solved it!

---

### Post by GadgetsGuy on 2007-05-14
> **deltafoxtrot said:**
> Check out this link: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard").  Worked for me (I'm also using the Logitech V20 speakers). 

```
$ sudo asoundconf list
Names of available sound cards:
ICH6
Speaker

$ sudo asoundconf set-default-card Speaker
```

Presto chango...  Restart any apps requiring a soundcard that may have been open prior to changing the default.

Good luck!

That worked for me!  (Logitech V20s)

Gracias!!    :)

---

### Post by eternalfire129 on 2007-05-19
that code worked great, however everytime i boot up i have to enter in the code for it to work, is there a way to make this permanent? thanx

---

### Post by GadgetsGuy on 2007-05-19
Hmmmm .... it should only have to be written once to the asound config file.

Are you sure you are using sudo or have proper permissions to write to asoundconf?

---

### Post by Kalden on 2007-07-06
Great, now I can use my Altec Lansing USB speakers.

---

### Post by stir-crazy on 2007-12-27
Very cool!  My Yamaha YST-MS55D's now are going.

Huge improvement over my laptop speakers, not sure if they get as ridiculously loud as they did in Win2K, but hey! they're working!  Strange thing was, was that the only soundcards I had listed were "Intel" and "default".  Guess the default was from when I was playing around with the settings, put the USB Yamaha's down as default...didn't take until the asoundconf command though.

THANK YOU!

---

### Post by Kenniej on 2008-01-21
> **deltafoxtrot said:**
> Check out this link: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_default_soundcard").  Worked for me (I'm also using the Logitech V20 speakers). 

```
$ sudo asoundconf list
Names of available sound cards:
ICH6
Speaker

$ sudo asoundconf set-default-card Speaker
```

Presto chango...  Restart any apps requiring a soundcard that may have been open prior to changing the default.

Good luck!

Worked for me aswell :D (ordinary JS usb adio speakers)

Thnx bro !!

---

### Post by vbhide on 2008-05-09
Works! (Ubuntu 7.04 + Logitech V10)

---

