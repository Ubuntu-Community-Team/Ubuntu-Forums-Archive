---
title: "Microphone not working"
date: 2008-06-24
forum: Multimedia Software
---

### Post by ljalg on 2008-06-24
I've been unable to use my Sound Card's microphone for almost a year now, ever since I installed Ubuntu on this computer.  Everything worked fine with Windows.  Here are the facts as best as I can provide and any help would be appreciated.

Sound card: onboard a ASUS M2R32-MVP motherboard
Speakers work fine
Currently on 8.04 but did not work on 7.10 either
Tried with several different speakers and microphones - same issue
double checked everything is plugged into the right ports, green to green and pink to pink (don't need surround sound)
I have enabled EVERYTHING in ASLA audio settings (see attached images)
With Analog Mix enabled I can hear the audio into the microphone out of the speakers
I've checked my Multimedia settings (see attached file - sound preferences.png)
Microphone on USB camera works in Skype only
output from dmesg attached (dmesg.txt, zipped because of size) but I'm not sure which line(s) are sound card related
I've searched the forums with not luck getting this to work

Any suggestions/help you can provide is appreciated.  I will only be able to reply with more information in the evenings as my computer is at home.

Thank you,

Louis

---

### Post by Phosphoric on 2008-06-25
have you had a look at alsamixer in the terminal?  It will show you which inputs and outputs are enabled.  I found that despite what I did with the sound card options, alsamixer showed the mic as disabled.
I was able to enable it in Alsamixer.  I don't have the deatils on me at the moment, I suggest you search or google Alsamixer.

 a further very important point for me:
In Alsamixer you can choose to look at the inputs and outputs seperately or have them displayed altogether.  I could only enable microphone recording when both recording and playback functions were displayed together.  Odd but true for me.

Good luck.

---

