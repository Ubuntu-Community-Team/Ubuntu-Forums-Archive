---
title: "AUDIO problems after upgrade to 8.10"
date: 2008-11-06
forum: Multimedia Software
---

### Post by TeoK on 2008-11-06
I'm completely confused here - there are no less than 5 sound control panels in Ubuntu Intrepid Ibex:
(the windows of these panels don't even fit on my screen all at once!)
- PulseAudio Manager
- PulseAudio Volume Control
- Sound Preferences
- Volume Control
- Volume Control Preferences

If anyone can record in flash-based environments (like youtube),  AND in Skype AND in Audacity - can you pretty PLEASE post the screenshots of your settings ??? Thanks

~
ThinkpadR52
Intel ICH6 sound card

[[IMG]http://img118.imageshack.us/img118/1577/56729445xm8.gif[/IMG]](http://img118.imageshack.us/my.php?image=56729445xm8.gif)

---

### Post by Lgo on 2008-11-06
Yeah I also have problems .. when scrolling a page in Firefox and listening to music the same time with Rhythmbox, the audio stops while scrolling the page for a while .. then when I stop scrolling the page, the music resumes.

Quite annoying! I removed pulseaudio, but didn't seem to solve the issue :(

SHould have sticked with 8.04 ..

---

### Post by TeoK on 2008-11-06
> **Lgo said:**
> 

SHould have sticked with 8.04 ..

you bet, same sentiment here.


~
problem solved tho - by solution from other forum:

1. In System->Preferences->Sound , set everything to ALSA instead of pulseaudio
2. in terminal:
killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
4.  delete "/etc/X11/Xsession.d/70pulseaudio" 
5.  unselect  pulseaudio in System>Preferences>Session
6.  Restrart

After reverting to Flash plugin 9 everything works -  voice recording, Skype, flash A/V
~~~~~~~~~~~~~~~~~~~~~~~~~~~

8.10, Intrepid Ibex seems to be very rushed, ill-conceived release - i've seen people calling it Idiotic Imbecile](*,):-P

---

### Post by raedbenz on 2008-11-06
believe the best thing is to backup your data and reinstall Ubuntu8.04.
thats what i did and i am working smoothly now.

---

