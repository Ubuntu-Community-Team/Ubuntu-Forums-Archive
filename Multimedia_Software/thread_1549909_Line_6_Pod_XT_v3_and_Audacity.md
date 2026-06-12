---
title: "Line 6 Pod XT v3 and Audacity"
date: 2010-08-10
forum: Multimedia Software
---

### Post by drsaamah on 2010-08-10
Hey there open-source recording artists!

So the past few days I've been trying to learn how to record my guitar parts onto Audacity using my Pod XT.  I've always used Audacity to do my audio recordings since its much more user friendly than Ardour and just as capable IMO.
However, I cannot get Audacity to work with the Pod.  I downloaded the "line6-usb-source" using apt-get.  Ubuntu seems to recognize the Pod and get a signal just fine (when I go to "Sound Preferences" it allows me to select the Pod XT as input hardware and even shows an incoming signal).  When I go to Audacity's preferences, it allows me to select the Pod as the "Recording Device", however when I go to record it gives me an error saying to check the Project Sample Rate.
Does the Pod not output at 44100 Hz?  Is there a way to change the sample rate the Pod puts out?  Is there another setting in Audacity I need to adjust?
I do not want to wine or emulate anything.  I feel I shouldn't have to use a specific audio recording software to use a piece of a hardware I paid good money for.
Any and all suggestions are much appreciated!!

---

### Post by cchhrriiss121212 on 2010-08-10
Some devices do not like 44100, so go to edit>preferences in Audacity and select 48000KHz under Quality. To check the pod sample rate , go to a terminal and type alsamixer. You should be able to adjust it from there.

Side note - Can't say I agree that Audacity is as capable as Ardour. Together with jack, Ardour is a powerful and stable audio recording tool. Audacity is a good editor, but if you start doing larger work involving multiple instruments and tracks then Ardour will be worth it.

---

