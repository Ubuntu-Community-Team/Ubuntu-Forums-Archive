---
title: "Pulseaudio and microphone input problem"
date: 2009-11-08
forum: Multimedia Software
---

### Post by janne_oksanen on 2009-11-08
I just upgraded to Karmic in order to get a certain webcam working. I read somewhere it was supported in the new kernel that comes with Karmic. Well, it's not, but that is not the point. With the upgrade Pulseaudio snuck its way back into my system and broke my Skype as usual. Only this time going back to ESD broke the rest of my apps too. 

Here's what I think it wrong. Pulseaudio isn't recognizing my mic input port as an audio capture devce (I have a Terratec 6Fire 24/96 sound card). As far as I can tell, no amount of tweaking with the GUI tools can fix that. So what are my options to make it work? How do I select a device that isn't being listed in the drop down boxes in the GUI?

---

### Post by waratah on 2009-11-12
You can try this for help.

[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

I switch pulse to the mic on the webcam and it works, my headset mic does not.

---

### Post by omunozsj on 2010-01-13
On a HP tx1220us, Karmic, you can't access important settings through Volume Control GUI (like ATAPI MIC). Instead you need to use alsamixer from a command line terminal:

% alsamixer -V all

Hope it helps...

---

### Post by mirzmaster on 2010-01-19
> **omunozsj said:**
> On a HP tx1220us, Karmic, you can't access important settings through Volume Control GUI (like ATAPI MIC). Instead you need to use alsamixer from a command line terminal:

% alsamixer -V all

Hope it helps...

Thank you, omunozsj.  I've been having trouble getting my microphone setup in Karmic for use with Skype.  It's unfortunate that sound setup is still such an arduous process in Ubuntu.

---

