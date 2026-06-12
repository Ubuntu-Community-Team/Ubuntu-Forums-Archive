---
title: "Xfi XtremeMusic (Creative Soundcard) issues with Surround Sound"
date: 2011-03-09
forum: Multimedia Software
---

### Post by Lazy_stoner on 2011-03-09
I recently installed Ubuntu for the first time, but have been having  some issues getting my sound to work properly. One of the things I read  while googling for a solution led me to create this  [http://www.alsa-project.org/db/?f=d328fd3a58b178a39317fe4689ae97ae08405c15](http://www.alsa-project.org/db/?f=d328fd3a58b178a39317fe4689ae97ae08405c15)  which I believe should have all the relevant information about my  hardware, but please tell me if there is something else you need to  know. 

When I go to System > Preferences > Sound  I see  that my sound card is being correctly (I assume) recognized and have set  the profile under hardware to Analog Surround 5.1 Output. When I click  "Test Speakers" I am able to hear the sound correctly for the front  right speaker, the button for the front left speaker creates sound from  my center speaker, and the rest of the buttons produce no sound at all.  When I play media from the web the sound comes quite heavily from the  front left speaker, the middle and front right operate at a very low volume, and the rear speakers do not operate at all.

I have read through the top post, made sure nothing is muted in alsamixer, etc. 

I'm loving Ubuntu so far and would love to continue using it but having my sound work improperly is a deal breaker for me.

---

### Post by johntaylor1887 on 2011-03-09
Try using alsamixer to get your settings right. Just open a terminal and:
```
alsamixer
```
You will have to use your arrow keys and space bar to use it. There are more settings revealed if you keep hitting the right arrow key.

---

### Post by Lazy_stoner on 2011-03-10
I have been through alsamixer previously and gone all the way over, but tried again just now per your suggestion. The spacebar does not appear to do anything, I have double checked that all channels are not muted and have the volume levels all the way up. 

Is there something I should be doing, specifically, to get the sound out of the appropriate speakers? I know that all the connections are wired properly as the sound worked just fine on Windows XP the day before I had switched over to Ubuntu. 

From what I've read thus far there used to be a lot of issues with the x-fi drivers but they should, supposedly, work right out of the box now? 

Any help would be greatly appreciated here, I'm a little out of my depth with this as a new user.

---

### Post by johntaylor1887 on 2011-03-10
Is it a USB card?

---

### Post by Lazy_stoner on 2011-03-10
No, it is an internal sound card. PCI, I believe?

---

### Post by johntaylor1887 on 2011-03-10
I found this: [https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

---

### Post by Lazy_stoner on 2011-03-13
Sorry it took so long to get back this last time, been a bit busy. I tried the steps outlined in there as well now without any luck, still getting single, sometimes dual, channel audio. I'm beginning to suspect it's an issue with the driver, which is unfortunate as I don't think there's much I can do about it.

Thank you very much for the help though.

---

