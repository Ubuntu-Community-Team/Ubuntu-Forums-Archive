---
title: "Gaps on Audacity soundwave when recording cassette or lp"
date: 2017-03-08
forum: Multimedia Software
---

### Post by shantiq on 2017-03-08
Noticed this recently on 16.04 0n version 2.1 2.1 repo also on Audacity 2.1.3-alpha-Mar 4 2017 cracks appear on the soundwave which means you have a check each time you playback and it reaches there.
Does not do it every time but most times
This on a new computer/new 16.04 install
also tried it on a dual-boot Mac/16.04 and ditto there; then when i use Audacity on the mac portion gaps do no appear.
As already mentioned it does this at times not always but mostly always


Any of you come across this and know how to rectify? What could be/is the cause?
Thanx in advance

[COLOR=#800000] **and the answer was: **set to 48000 at the recording stage if you want to export in 44100 do that **after **recording is done   ....  **It should really be explained by Audacity**[/COLOR]



[[IMG]https://s10.postimg.org/bojoimlc5/gaps.png[/IMG]]("https://postimg.org/image/bojoimlc5/")

---

### Post by Autodave on 2017-03-08
I have had this before and it has always been that the HD is not being able to keep up with the recording speed asked of it.  The newer Audacity was a nightmare for me and I never did it to work correctly. I finally went back to 2.0.5 and have no probs with that.  (And I am recording 18 channels via USB cable.)  How many back ground programs do you have running? Close all of them before recording. Also, if you are running Ubuntu, you may want to try a "lesser" version that uses less memory: like Xubuntu.

What are the specs of your machine?

---

### Post by shantiq on 2017-03-09
Thanx Auto
is there a way to slow recording speed without changing version
This on a new computer/new lxde 16.04 install   8GB RAM  500 hours of recording   not a hardware issue surely


PS    how did you manage 2.0.5 on 16.04 ?   tried that here but no luck thus far  [too many dependencies issues]

---

### Post by Autodave on 2017-03-09
> **shantiq said:**
> Thanx Auto
is there a way to slow recording speed without changing version
This on a new computer/new lxde 16.04 install   8GB RAM  500 hours of recording   not a hardware issue surely

In Audacity, *Edit -> Preferences -> Quality.  *Under Real time conversion: you can reduce that as well as the Real time conversion.  You probably want to keep the 32 bit float setting. You could lower the Default sample rate to 32,000 hz: the quality of what you are recording from probably would not exceed that rate, so you wouldn't hear a real difference.


PS    how did you manage 2.0.5 on 16.04 ?   tried that here but no luck thus far  [too many dependencies issues]

I am sorry for confusing you on that: my fault. I too had problems with the dependencies and went back to 14.04. The machine I use for recording is used at my church for recording the services. It is not hooked up to the internet.  I installed 14.04 and Audacity 2.0.5 that was in the 14.04 repositories. I updated everything, disabled everything not needed for recording, and then turned off the automatic updating. I do update it sometimes, but from the command line.

If you have a some room on your HD, you may want to install 14.04 and 2.0.5 along side your 16.04.

---

### Post by shantiq on 2017-03-09
ha ok ....  makes sense on 14.04


PS   now also running Slackware on an earlier machine and the gaps are not there on a new install; machine specs way lower and running Audacity 2.1.2 there too  ....    go figure :]

---

### Post by shantiq on 2017-03-12
hmm    funny your last message has not appeared here but it is in my email   [also it said Ubuntuforums had nor encrypted it so it went to my trash/found it by accident]

> In Audacity, Edit -> Preferences -> Quality.  Under Real time  conversion: you can reduce that as well as the Real time conversion.   You probably want to keep the 32 bit float setting. You could lower the  Default sample rate to 32,000 hz: the quality of what you are recording  from probably would not exceed that rate, so you wouldn't hear a real  difference.


I had only looked under Recording and not Quality so i played around with Real Time Conversion settings and High Quality conversion settings only to find out that *the culprit was setting 44100kHz AT THE RECORDING* [see my pic above]stage *instead of doing it at the exporting stage* ...    this is how the cracks appear    ...    you probably can replicate that on any machine

Anyway ...   thanx for input   ...   that led to correction


Marked as solved
Thank you again

---

