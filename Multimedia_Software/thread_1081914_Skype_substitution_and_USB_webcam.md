---
title: "Skype substitution and USB webcam?"
date: 2009-02-27
forum: Multimedia Software
---

### Post by msohn88 on 2009-02-27
My family members are all over the places and everybody has Skype account.

But I am having a hard time installing Skype, so I am thinking about if there is a substitution for it. I mean if there is an application that can link my Skype account...

Also, how does USB webcam works?

---

### Post by Crafty Kisses on 2009-02-27
You shouldn't be having problems installing Skype, have you followed this guide? [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295).

---

### Post by msohn88 on 2009-02-27
Thanks, but I see that webcam is not supported...

Any applications for using same account for Skype?

---

### Post by meho_r on 2009-02-27
Webcam through Skype on Linux is supported. Unfortunately, it's a little bit tough to set brightness and contrast since there are no controls for it in Skype, but apart of that works fine.

Gizmo recently started offering a service to talk directly to your Skype buddies, but only 5 mins are free, for more you have to pay :(

BTW, the easiest way to install Skype is to add [Medibuntu](https://help.ubuntu.com/community/Medibuntu) repository and then simply install from Synaptic (as noted in the tutorial you were suggested by Codename).

---

### Post by lordbux on 2009-02-27
> **msohn88 said:**
> Thanks, but I see that webcam is not supported...

Any applications for using same account for Skype?



try this frnd
```
sudo gstreamer-properties 
```

a window will appear select .... **Video tab**

set
>>default output   as** Auto detect**
and
>> change default input properties ..
plugin>>> to  Video for linux (v4l)

keep cam connected

---

### Post by msohn88 on 2009-02-27
> **lordbux said:**
> try this frnd
```
sudo gstreamer-properties 
```

a window will appear select .... **Video tab**

set
>>default output   as** Auto detect**
and
>> change default input properties ..
plugin>>> to  Video for linux (v4l)

keep cam connected

It does not work... Should I restart my computer?

---

### Post by msohn88 on 2009-02-27
Videos on Skype won't work. 

Cheese application shows my Webcam, but it doesn't on aMSN or Skype.

Does Pldgin support webcam for MSN?

---

