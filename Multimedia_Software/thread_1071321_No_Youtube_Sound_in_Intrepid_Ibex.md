---
title: "No Youtube Sound in Intrepid Ibex"
date: 2009-02-16
forum: Multimedia Software
---

### Post by scytheye on 2009-02-16
No youtube sound after numerous attempts to fix this.  It works EVERYWHERE but youtube...even metacafe - 
I tried this: [http://ubuntuforums.org/showthread.php?p=5931543]("http://ubuntuforums.org/showthread.php?p=5931543") I even tried turning off java add-ons in firefox 3.0.6 but it made no difference. :guitar: (exactly...where's the sound?)

*LSCPI output*: 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

*$ dpkg -l | grep flash output*: 
ii  flashplugin-nonfree   10.0.15.3ubuntu1~intrepid1 Adobe Flash Player plugin installer

---

### Post by gandaran on 2009-02-16
maybe you need to fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Veratyr9 on 2009-02-16
I subscribed to this thread. i'm equally interested to find the outcome of this.  (this is rip_ from irc)  Good luck with this.  I'd like to say if theres anything i can do to help.... but i think we tried that approach last night hehe.  Thanks for keeping me updated on this :)

P.S welcome to the forums, tons of valuable information archived here.  that search bar at the top is pretty powerful when you get stuck somewhere in ubuntu.

---

### Post by BLTicklemonster on 2009-02-28
Me too. I got nothing when it comes to youtube audio. Running Intrepid.

---

### Post by SeePU on 2009-02-28
You might need to provide more info.  32-bit or 64-bit Ubuntu?  Intrepid at what kernel ver.?

Are you using ALSA?  Installed Pulse Audio?

I don't know why you would have sound for everything else but Youtube?

Maybe it is audio related to Flash?   When you say for everything else, what do you mean?  Other applications?  Are any flash-based?

Sounds like an audio codec not installed or some sort of broken package (related to audio ...duh, I know, stating the obvious).  Maybe try re-installing Flash if all else fails?

---

### Post by BLTicklemonster on 2009-03-02
Oddest thing. I changed everything to pulse, and still had nothing, so I changed back to sblive alsa. Clicked a link in email shortly thereafter, and lo and behold, audio in youtube works. Dangedest thing...

---

### Post by scytheye on 2009-03-05
I have resolved the problem.  It didn't work the first time I did it, but the second time it did.  

Here's what I did: System > Preferences > Sound

Then the first two options I set at ALSA.  
The Default I also set at ALSA. 

Under audio conferencing, I selected HD Intel ALC883 Digital and Analog for the second option. 

Worked after a reboot!  :popcorn:

---

### Post by Protocol3734 on 2009-03-07
I am having the same problem with no sound in youtube, actually it is more like no sound on mozilla I am running firefox 3.0.7 and ubuntu 8.10 intrepid.  My system is an HP pavillion a6300f.  Integrated soundcard ALC 888S chipset.  I am currently running sound on the OSS option the ALSA doesnt seem to work, I have video on firefox, just no audio.  Audio works with DVDs and music though.  Please help if you can I have been working on this for 2 weeks.

---

