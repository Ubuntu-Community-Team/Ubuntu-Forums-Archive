---
title: "different sound streams direction to microphone and speakers"
date: 2009-04-19
forum: Multimedia Software
---

### Post by Berduchwal on 2009-04-19
What I want to achieve is as follows:

Use Skype with headset (microphone + headphones) and at the same time my daughter watching DVD with sound coming from my laptop speakers.

At the moment when I plug in headphones speakers are switched off automatically.

I have no clue how this is called and where to start so I would appreciate direction to some reading about the subject.

---

### Post by markbuntu on 2009-04-19
There is a switch in the headphone jack. Depending on how old your machine is it could be a hardware switch or a sense switch. Either way you are looking at some fairly difficult tweaking. Your best bet would be to get a usb headset. They are cheap and easy to configure.

---

### Post by Berduchwal on 2009-04-20
I do not mind if it is difficult.

If it is possible that would be sufficient :)

If you could direct me to some reading I would be grateful.

---

### Post by markbuntu on 2009-04-20
After thinking about it a little I do not believe that you can have two different streams going to two different outputs within the same device. Speakers and headphones use the same DAC and it is just switched. You would need to have a sound chip with two separate DACs and then the low level alsa driver would need to accomodate switching them around. I have never seen this in a laptop.

There are a few pci cards with this capability but really, I think your best bet would be either a usb headset or a cheap usb sound card with mic and headphone jacks.

alsa.org

has a lot of information about stuff like this.

If you are worried about getting it set up, there is plenty of help for that right here.

---

### Post by Berduchwal on 2009-04-20
thanks I am sure you meant:

[http://www.alsa-project.org/](http://www.alsa-project.org/)

will try to see what options are there.

---

