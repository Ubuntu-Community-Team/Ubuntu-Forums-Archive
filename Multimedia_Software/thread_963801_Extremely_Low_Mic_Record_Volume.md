---
title: "Extremely Low Mic Record Volume"
date: 2008-10-30
forum: Multimedia Software
---

### Post by jdeslip on 2008-10-30
I have a dell 1420n laptop (that was sold with ubuntu).  Since upgrading to intrepid, my internal microphone records my voice at extremely low volume in intrepid.  This happens in both audacity and skype (the only programs I have tested).  

My audio input device in skype is (hw,intel 0).  The output devices are set to 'pulse'.  I have tried maxing out all the settings in alsamixer but nothing seems to help. 

Anyone know how to fix this?  My mic is currently useless in intrepid.

---

### Post by koruptid on 2008-10-30
I'm having the same issue... just posted the same topic a few minutes after you. I have some more notes on what I have tried in the new thread.

---

### Post by jdeslip on 2008-10-30
Well glad I am not the only one.  I also found this bug report: [https://bugs.launchpad.net/ubuntu/+bug/282931/](https://bugs.launchpad.net/ubuntu/+bug/282931/)

---

### Post by koruptid on 2008-10-30
So far this seems to be an issue localized to the Intel HD Audio for RealTek audio... so it could be a while before either of us sees a solution.

---

### Post by loell on 2008-11-03
mine too..

---

### Post by muadnu on 2008-11-05
Same for me... And this is keeping me from switching to Intrepid (I need Skype).

---

### Post by ububaba on 2008-11-05
I could once solve the problem by simply switching the microphone
jack to the front of the machine. Somehow the problem has reverted.
So, I am also joining the club. Still using Hardy.

---

### Post by jdeslip on 2008-11-12
I can get my mic to record at reasonable levels by killing pulseaudio.  But, with pulseaudio running my mic records at extremely low volumes (even choosing the hw setting in skype).  

There is another thread here describing the problem:  [http://ubuntuforums.org/showthread.php?t=956565](http://ubuntuforums.org/showthread.php?t=956565)

It seems particularly prevalent in Dell laptops.

---

### Post by patrickballeux on 2008-11-12
I am using the "alsamixer -Dhw:0" to change some settings on the ALSA mixer.

On my card, I have two "Capture" volume, a "Digital" volume and 2 "Mux" volume.

For the internal microhpone, I have to play with the "Digital" volune.  "Mux" volume are kind of amplifiers, but they are set to 0.

When I use an external mic, I play with the "Capture 1" volume, this one is working with Pulseaudio...

Ah yeah, make sure that your capture Device is Digital, not Analog Input ...

Good luck!

---

### Post by jdeslip on 2008-11-13
On my Dell 1420, capture was set to digital and I maxed out every possible seetting in alsamixer.  Still no luck when pulseaudio was running (even when using the alsa hw device).

---

### Post by patrickballeux on 2008-11-13
> **jdeslip said:**
> On my Dell 1420, capture was set to digital and I maxed out every possible seetting in alsamixer.  Still no luck when pulseaudio was running (even when using the alsa hw device).

Have you tried without pulseaudio? (run pulseaudio -k).  This is how I did it.  Once setting were ok, I restarted pulseaudio (logout-login).

Tip:  To reset your pulseaudio setting, delete the folder ~/.pulse


I really hope that this sound issue will get fixed.

---

### Post by Washington Irving on 2008-11-28
I have the same issue on a Toshiba Satellite l300. Skype is unusable.

---

### Post by Washington Irving on 2008-12-02
[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

this thread solved it for me.

---

### Post by loneowais on 2009-05-23
I can confirm this on Jaunty

---

### Post by 8pla.net on 2009-08-25
patrickballeux said, "*I am using the "alsamixer -Dhw:0" to change some settings on the ALSA mixer.On my card, I have two "Capture" volume, a "Digital" volume and 2 "Mux" volume.For the internal microhpone, I have to play with the "Digital" volune. "Mux" volume are kind of amplifiers, but they are set to 0. When I use an external mic, I play with the "Capture 1" volume, this one is working with Pulseaudio... Ah yeah, make sure that your capture Device is Digital, not Analog Input ...*"

I had the same exact problem with the mic recording very low on Skype on AMD64. Using this post by patrickballeux as a guide... It solved my problem with a few slight differences. Analog Input (instead of digital) worked for me with an external mic. In general, I think once you find the check boxes to add more mux and capture volume sliders to play with in the volume control, that might let you pump up the volume. Thank you, patrickballeux

---

### Post by ramesh_cme on 2009-08-26
try this one open terminal in that type
 
"sudo alsa force-reload"
 
then it will ask you to reload it press reload k i think this will help you...

---

