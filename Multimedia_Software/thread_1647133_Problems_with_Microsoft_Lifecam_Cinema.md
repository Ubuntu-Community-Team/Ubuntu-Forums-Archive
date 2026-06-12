---
title: "Problems with Microsoft Lifecam Cinema"
date: 2010-12-16
forum: Multimedia Software
---

### Post by elendilnl on 2010-12-16
I've bought a Microsoft Lifecam Cinema webcam and I have a few problems with it.
In Skype, the build-in microphone does not work. 
Input level in Sound Preverences - Input shows that it detects sound, but it does not leave my system.
And there is another problem.
Image quality in Cheese as well as Skype is good, but if I connect with, for instance with ww.com, the images are very coarse :(

In Skype I have only one sound device; PulseAudio server, I have the latest version of Adobe Flash.
I'm running Ubuntu 10.10 and my kernel version is 2.6.35.23 generic-pae.

Has anyone a solution for these problems?
Thanks in advance!

---

### Post by Rodney9 on 2010-12-16
[http://www.jupitercolony.com/viewtopic.php?f=7&t=2201](http://www.jupitercolony.com/viewtopic.php?f=7&t=2201)

---

### Post by elendilnl on 2010-12-17
> **Rodney9 said:**
> [http://www.jupitercolony.com/viewtopic.php?f=7&t=2201](http://www.jupitercolony.com/viewtopic.php?f=7&t=2201)Thanks for the link Rodney, but it's not that the sound quality is bad, the other side of the connection does not hear anything at all.

---

### Post by gobbles414 on 2010-12-17
These may be foolish questions, but have you selected the Lifecam's mic in Sound Preferences, set it to maximum volume, and unmuted it? Also, have you "called" Skype's automated connection feature to verify lack of mic input? Note, Skype's automated mic verification system will take several moments to process your mic input and play it back in your speakers/headphones.

I've been helping a friend to get her Lifecam (don't remember model number) working in Skype in Ubuntu 10.04, and the steps mentioned above appear to have solved her mic issues.

---

### Post by elendilnl on 2010-12-17
> **gobbles414 said:**
> These may be foolish questions, but have you selected the Lifecam's mic in Sound Preferences, set it to maximum volume, and unmuted it? Also, have you "called" Skype's automated connection feature to verify lack of mic input? Note, Skype's automated mic verification system will take several moments to process your mic input and play it back in your speakers/headphones.

I've been helping a friend to get her Lifecam (don't remember model number) working in Skype in Ubuntu 10.04, and the steps mentioned above appear to have solved her mic issues.There's no foolishness in your question Gobbles. It happened before that I made a stupid mistake. But the answer is yes to all questions :(

---

### Post by AKADAP on 2010-12-17
Don't bother with Cheese to test your web cam, Cheese is currently broken.

I don't know what is wrong with your system, but I can tell you that the Microsoft LifeCam Cinema does work with skype as that is what I use.

---

### Post by elendilnl on 2010-12-17
> **AKADAP said:**
> Don't bother with Cheese to test your web cam, Cheese is currently broken.

I don't know what is wrong with your system, but I can tell you that the Microsoft LifeCam Cinema does work with skype as that is what I use.It's not the the camera is not working Akadap, it's the mike that refuses it's job :)

---

### Post by fjm03 on 2010-12-17
For me the fix was simple
1) Open Skype
2) Go to the Skype icon in the lower left corner of the splash screen
3) Open the Options menu
4) Open Sound Devices
5) Uncheck the default "Allow Skype to automatically adjust the mixer level" box

---

### Post by elendilnl on 2010-12-18
> **fjm03 said:**
> For me the fix was simple
5) Uncheck the default "Allow Skype to automatically adjust the mixer level" boxThat was the first thing I did when I installed Skype and using my old cam. It's an option they'd better left out :)
But thanks for the tip fjm!

---

### Post by gobbles414 on 2010-12-18
Maybe the Skype mixer level option wasn't compatible with your old webcam, but is essential to the proper functioning of your Lifecam in Ubuntu's Skype? Seems to me that it couldn't hurt to try...

---

### Post by AKADAP on 2010-12-18
> **elendilnl said:**
> It's not the the camera is not working Akadap, it's the mike that refuses it's job :)

The mike is physically part of the camera, and works fine for me.

---

### Post by VonSpyder on 2013-01-16
is it recording audio in other apps like gucview? This may help you ascertain whether its a skype issue or an ubuntu issue or even a hardware issue.

---

