---
title: "pulse audio. What's the benefit?"
date: 2009-07-26
forum: Multimedia Software
---

### Post by martinbaselier on 2009-07-26
Since a lot of people seem happy with pulse audio (when they don't have problems with it), I decided to give it a try and installed it.

Apart from using 2-10% of my cpu and about 200MB of my virtual memory, I don't see any added funtionality. I can direct multiple sound sources to it, but I already was able to do that with my normal soundcard driver. The only difference is: With pulse I'm not able to set the volume of the different streams. I thought that was supposed to be one of the added features. 

If I look in synaptic, it seems pavucontrol is the tool for that, but it breaks up my install. I need to remove several essential things to give that a try, so I'm not going to do that. 

Could someone tell me what benefits pulse adds for normal usage?

---

### Post by martinbaselier on 2009-07-27
*bump*

---

### Post by martinbaselier on 2009-07-28
Is it such a hard question. I know it's supposed to be a network sound server. Doesn't anybody know what I can do with it on a single machine with a single sound card? I must be installed by default for some reason. I don't suppose the ubuntu creators think everybody wants to set up a network sound server by default.

---

### Post by martinbaselier on 2009-07-30
*bump*

---

### Post by cotcot on 2009-07-30
For me it is even a problem. I have de-installed pulse audio to be able to get sound in different apps that run at the same time (for instance audacity and blender).

---

### Post by binbash on 2009-07-30
Pulse audio is just a problem in my opinion, i always uninstall it on every distro i use.

---

### Post by markbuntu on 2009-07-30
The problem is not really pulseaudio but its crappy implementation in ubuntu. It works much better in Fedora and Mandriva and other distros.

---

### Post by igorzwx on 2009-07-30
Mark!
You are great!

"The idea was correct, but it was applied in a wrong way".
This is exactly how Russian Marxists explained the failure of 
the Communist Utopia.

---

### Post by binbash on 2009-07-30
> **markbuntu said:**
> The problem is not really pulseaudio but its crappy implementation in ubuntu. It works much better in Fedora and Mandriva and other distros.

Yes it is great at Fedora 11 and crap on Ubuntu but this does not change the topic.

---

### Post by markbuntu on 2009-07-30
If you only have one sound card I doubt that you will gain much, and probably lose a lot without installing pavucontrol which is necessary to actually control pulseaudio since it is the pulse audio volume control and the place where you can control the volume of individual streams. Installing pulseaudio without pavucontrol is really defeating the purpose of pulseaudio.

If you have more than one hardware sound device then pulseaudio can make your life a lot easier.

---

### Post by Katalog on 2009-07-30
> **markbuntu said:**
> The problem is not really pulseaudio but its crappy implementation in ubuntu. It works much better in Fedora and Mandriva and other distros.

Exactly right. It is not fully installed/implemented in Ubuntu (the developer actually admitted he dropped the ball on getting PulseAudio into 9.04 correctly), but it can be fixed:

				[**HOWTO: PulseAudio Fixes & System-Wide Equalizer Support**]("http://ubuntuforums.org/showthread.php?t=789578")

Fixed most of the problems I was having with Ekiga, and from what I understand the real benefit of PulseAudio is that it supports far more devices than the older Linux sound architctures.

---

### Post by markbuntu on 2009-07-30
> **Katalog said:**
> Exactly right. It is not fully installed/implemented in Ubuntu (the developer actually admitted he dropped the ball on getting PulseAudio into 9.04 correctly), but it can be fixed:

				[**HOWTO: PulseAudio Fixes & System-Wide Equalizer Support**]("http://ubuntuforums.org/showthread.php?t=789578")

Fixed most of the problems I was having with Ekiga, and from what I understand the real benefit of PulseAudio is that it supports far more devices than the older Linux sound architctures.

Device support is from the ALSA devs since they write the drivers except bluetooth which is from bluez.org and firewire from the ffado folks.

Pulseaudio does handle multiple hardware devices and applications better than the previous ALSA sound server kludge that included dmix and esound.

The biggest problem with ubuntu and pulseaudio is that ubuntu implements pulseaudio in the default desktop seed but does not include pavucontrol and a bunch of libs and other stuff needed to actually use it as the default sound server and have some control over it.

---

### Post by martinbaselier on 2009-07-31
Ok, if I want to have equalizer support or have multiple sound cards, pulse could add some functionality. I still think it's a rather odd solution to use a network sound server for that purpose, but at least I can now see what benefits it could bring. If only it would not take up so much resources.

---

