---
title: "pulseaudio server on multiple ubuntu computers in local network"
date: 2010-12-05
forum: Multimedia Software
---

### Post by muzikjock on 2010-12-05
I will cut to the chase. I am running three ubuntu computers on my local network:my desktop which runs ethernet, and two laptops which run wireless on the same network, and all from the same router. For purpose of this thread, I am concentrating on this one issue with pulse(assuming its pulse doing this). When I have two computers running at the same time, or even all three,  I can hear bursts of sound coming from the other computer, not all the time, but consistently. I don't know what is causing this. I've searched hi and low in all ubuntu pulse audio forums and those mentioning pulseaudio and I have not seen this issue posted anywhere. Most threads deal with issues of not being able to get pulse to recognise audio from one computer to the other...mine is just the opposite...I'M TRYING TO STOP THIS FROM HAPPENING!...... If I'm listening to my music on my desktop, I don't want to hear what my son is playing on his laptop...and vice versa. it is frustrating and any help would be appreciated. . all the computers at my home are running lucid lynx, latest updates and latest approved kernel as of the date of this post. 2.6.32-26-generic. I would be more than happy to add additional information that is necessary to solve this. Thank you to anyone.

---

### Post by muzikjock on 2010-12-05
ok I'm going to try this. In the pulseaudio applet, I went to "configure local sound server" and then "network server". unchecked "enable network access to local sound devices". I will see if this works as a work around . but I shouldn't have to do this if my default server is from my own computer....I can see if I switched the default sink to one of the other computers, but I haven't. I'll see if this works.

---

### Post by MarkoCro on 2011-04-13
Your problem is that sound output over LAN is being triggered somehow even if you don't want it. Application you are mentioning called "paprefs" isn't installed on modern Ubuntu distros by default. You should install it from repository.

For people who want this what you don't want :) - enable sound output from one PC to any pc inside LAN can check out my PulseAudio network server guide:

[[www.techytalk.info] Using PulseAudio as network sound server]("http://www.techytalk.info/2011/04/pulseaudio-network-sound-server/")

---

