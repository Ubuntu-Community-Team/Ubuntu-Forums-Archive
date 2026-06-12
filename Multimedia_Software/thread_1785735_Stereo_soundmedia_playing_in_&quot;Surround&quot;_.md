---
title: "Stereo sound\media playing in &quot;Surround&quot; U11.04"
date: 2011-06-18
forum: Multimedia Software
---

### Post by Gustradamus on 2011-06-18
New to forums and fairly new to Ubuntu (been experimenting since 9.04, finally took the plunge for 11.04) and have searched forums and google for answers, to no avail.

My "issue" is that i have a 5.1 system (Logitech X540) connected to my Asus P45ql via Analog inputs (1 for FL FR, 1 for RR RL, 1 for Center and 1 for LFE), yet my Stereo(2 channel) media such as some Videos and some Music, play in Surround through all speakers, as if i were to flip the Simulated Surround "Matrix" switch on my Logitech controller.

My 5.1 audio and video play fine with these settings, but id like to know if i could possibly have my Stereo media outputted in Stereo thru only FR and FL speakers?

I'm using VLC with Restricted Extras package to play All Media, when i check Audio Channels on Stereo files, it says Stereo, but has 5.1 output.

My Sound Preferences are: 
Hardware : Internal Audio, 1output, Analog Surround 5.1 Output
Output: Internal Audio Analog Surround 5.1, Surround 5.1

Thank you all.

---

### Post by lidex on 2011-06-18
Couldn't you just change your profile to stereo duplex or similar?

---

### Post by Gustradamus on 2011-06-21
Even with Stereo Duplex the Entire signal is a simulated surround output, i have to force VLC to use ALSA, so i can use Audio devices to turn on true 5.1, but then there is a conflict when i play FLV videos from youtube etc. because i think Firefox is using Pulse Audio, so i get a freezeup either VLC or Firefox.

Maybe disabling Pulse Audio?

---

### Post by lidex on 2011-06-25
> **Gustradamus said:**
> Even with Stereo Duplex the Entire signal is a simulated surround output, i have to force VLC to use ALSA, so i can use Audio devices to turn on true 5.1, but then there is a conflict when i play FLV videos from youtube etc. because i think Firefox is using Pulse Audio, so i get a freezeup either VLC or Firefox.

Maybe disabling Pulse Audio?

Actually firefox is directly accessing alsa:
[http://ubuntuforums.org/showthread.php?t=1412153](http://ubuntuforums.org/showthread.php?t=1412153)
Maybe the reverse of this procedure:
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)
More info:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/2/)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10058679](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10058679)
[http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules)
[http://pulseaudio.org/wiki/ModulesTOC](http://pulseaudio.org/wiki/ModulesTOC)

---

