---
title: "Can't manage to get my mic to work"
date: 2009-04-04
forum: Multimedia Software
---

### Post by hppavmx704 on 2009-04-04
I have a HP Pavilion dv9000 series laptop and I can't manage to get my mic to work.  I have searched numerous pages on the Internet and even asked some friends.  I have the same set up as they do for the most part and nothing will seem to get it to work.  I think it might be my sound card.  I am new to the Linux system so any help would be appreciated.

---

### Post by lavy on 2009-04-04
Hy,

A little inside information on your system will be helpful :) such as ubuntu version  and what set up you are talking about ( you said you have the same setup like your friends). You should explain what you have tried.
My first idea is to ask you if you opened the microphone from the sound volume? I'm pretty sure you did that...
So how I was saying give more details about your system, the setup you are talking and what else you tried.

---

### Post by hppavmx704 on 2009-04-05
I run unbuntu intrepid 8.10.  I went into my volume controls and turned everything up and I also went and played around in skype.  I have all of my switches turned on and i use the alsa sound mixer.

---

### Post by xc3RnbFO8P on 2009-04-05
In Options do you have Front mic and Mic, sometimes you have to choose Front mic and then Mic to get it to work.

---

### Post by hppavmx704 on 2009-04-05
No, there are no front mic or mic options in my options menu.

---

### Post by xc3RnbFO8P on 2009-04-05
Did you go to Preferences and check all the capture, input and mic , in Volume Control?

---

### Post by peterqb on 2009-04-05
If that doesn't work, try the Pulse Audio Applet, set its icon to appear in the top bar of the screen, then try selecting different default sources until the microphone works.

If using Skype, go into prefs and select "pulse" for all sound, then save prefs.
--
pqb

---

### Post by hppavmx704 on 2009-04-05
I did set everything in the volume control...and I'm really new so could you explain how to do the pulse applet please.

---

### Post by peterqb on 2009-04-12
> **peterqb said:**
> If that doesn't work, try the Pulse Audio Applet, set its icon to appear in the top bar of the screen, then try selecting different default sources until the microphone works.

If using Skype, go into prefs and select "pulse" for all sound, then save prefs.
--
pqb


I continued to try to solve this, and I think the following is working for me: in Skype Options > sound, choose sound in and select the correct item from the drop down menu. In my case it is the USB input (the microphone on the web cam, which is connected via USB.)

I have tested this, and it seems to be working smoothly.
--
pqb

---

### Post by peterqb on 2009-04-19
> **hppavmx704 said:**
> I did set everything in the volume control...and I'm really new so could you explain how to do the pulse applet please.


Use add remove (in programs) or synaptic package manager (in system > administration) to instal this, then follow instructions.

I'm pretty new to Linux as well, and find the installation of new progs can be difficult, but sometimes they install fine.
--
pqb

---

