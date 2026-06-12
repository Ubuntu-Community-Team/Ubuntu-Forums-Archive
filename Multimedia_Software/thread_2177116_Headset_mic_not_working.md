---
title: "Headset mic not working"
date: 2013-09-27
forum: Multimedia Software
---

### Post by tnanek on 2013-09-27
I'm having trouble getting my headset (not usb, meant for cellphones) to work with my Xubuntu 13.04 desktop. It works fine on my Android phone as both speakers and mic, but I generally spend much more time in front of my computer and it would be more convenient for me to use that over my webcam's microphone to combat voip feedback. The problem is I can't seem to get it to recognize the microphone exists. At the moment, it is plugged into both the headphone and the microphone slot, through a physical Y-cable and extension cord.

I can get the headphones to output sound (though I generally have to switch the Profile from the current one of "Digital Stereo (HDMI) Output + Analog Stereo Input" to "Analog Stereo Output + Analog Stereo Output", through pavucontrol (menu --> Multimedia --> PulseAudio Volume Control).

Whats worse is my LinPhone doesn't seem to be recognizing either input at the moment. And the only options it has for capture device  selections are "PulseAudio: default" and "ALSA: default device". It seems by those output settings that the ALSA: HDA Intel is my HDMI speakers, and PulseAudio: default is my headset, so for now its set to the PulseAudio one.

Through Google Chat settings, I see an explicit option for my webcam as a microphone. Yet not in LinPhone, and no option works for my headsets mic, which is my preferred option here.

On reading other messages, people seem to be pointed to alsa-project.org for a system analysis, so if it helps, [here]("http://www.alsa-project.org/db/?f=890b58ed7421478a661fd4c70b579c497a09e270")'s those results for me.

---

### Post by Kirboosy on 2013-09-27
What kind of laptop are you using? I believe your laptop will need a combo jack in order to properly work with that type of headset. (Meaning you will need a traditional 3.5 mm one for headphone and 3.5mm one for mic)

Hope that helps!
~Caboose

PS I found this adapter that might do the trick: [Headset Buddy Smartphone to PC adapter]("http://www.amazon.com/Headset-Buddy-Adapter-Smartphone-01-PH35-PC35/dp/B00332DPDG/ref=pd_sim_pc_18")

---

### Post by tnanek on 2013-09-27
This is a mini-tower desktop; Gateway SX2801-01e.

On looking up more specifics about headset issues, someone [here](http://forums.astrogaming.com/archive/index.php/t-20205.html) mentions it is a 4-pole 3.5mm cable that their trying to convert from, so a standard Y-cable won't work, need to get one of those adaptors which you linked to, thanks Caboose.

I don't see any way of setting this as solved...

---

### Post by Kirboosy on 2013-09-28
You should be able to mark it as solved under the thread tools at the top of the thread.


Glad I could help!
~Caboose

---

