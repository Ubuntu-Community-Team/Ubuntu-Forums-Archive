---
title: "Microphone not working after upgrade to Ubuntu 10.10 Maverick"
date: 2010-10-10
forum: Multimedia Software
---

### Post by fiercedrake on 2010-10-10
Hello, I updated my ubuntu today from 10.04.1 to 10.10 and my microphone stopped working. There is no connector option in the input tab to choose the microphone. I checked everything in alsamixer and still nothing. I had no problems in 10.04.1. Anyone has suggestions how to fix this ?

---

### Post by linux4me on 2010-10-10
I'm not sure from your description about what you're trying. 

Try clicking on the sound icon on your panel and choose Sound Preferences. Then choose the Hardware tab. In the Profile drop-down, you'll want to select an option that includes Analog Stereo Input along with the type of output you're using (digital or analog). Then go to the Input tab and select the input device in the bottom section. You should then have the controls up top on the Input tab to mute/unmute the microphone and adjust its input volume.

---

### Post by fiercedrake on 2010-10-10
My hardware profile is Duplex. When I click on the input tab the signal measuring bar is always staying lit on the first section and does not move further. This means that the mic is not capturing sound. In 10.04.1 there was a dropdown menu in the input tab from which I could choose the default microphone and thus choose an option that works. In 10.10 there is no such thing. I kind of fixed it by adding  "options snd-hda-intel model=3stack" in alsa-base.conf. Now I have the dropdown menu and my microphone works for now. The problem is that I did not have to do this in 10.04.1 ...

---

### Post by linux4me on 2010-10-10
I think it might be that Duplex profile. If I select Duplex, I don't have any inputs, either. Glad you got it working.

---

### Post by daltore on 2010-10-10
I did have to do this in 10.04.  It seems to be a hit-or-miss kind of problem as to whether PulseAudio will recognize the microphone on a particular installation.  For instance, my microphone usually works when running liveCD's, but not on the installations (since they started forcing PulseAudio).

---

### Post by svasi on 2010-10-26
> **fiercedrake said:**
> My hardware profile is Duplex. When I click on the input tab the signal measuring bar is always staying lit on the first section and does not move further. This means that the mic is not capturing sound. In 10.04.1 there was a dropdown menu in the input tab from which I could choose the default microphone and thus choose an option that works. In 10.10 there is no such thing. I kind of fixed it by adding  "options snd-hda-intel model=3stack" in alsa-base.conf. Now I have the dropdown menu and my microphone works for now. The problem is that I did not have to do this in 10.04.1 ...
Thanks! Your solution solved the problem for me.

---

### Post by neon2k8 on 2010-10-28
where can i find the alsa-base.conf file and which program to use to add that line?

---

### Post by vdubhack on 2010-10-29
/etc/modprobe.d/alsa-base.conf

You can also just do locate alsa-base.conf

---

### Post by shadrack111 on 2010-11-13
> **vdubhack said:**
> /etc/modprobe.d/alsa-base.conf

You can also just do locate alsa-base.conf
i went to the file manually. but when i tried to type it in it said it couldn't be found. but when i opened the file i couldnt type anything in it. i need help im new at this and i need to use my mic since im overseas military

---

### Post by luca.marinosci@gmail.com on 2010-11-21
alt+f2
then type gksu gedit /etc/modprobe.d/alsa-base.conf

at the bottom of the file add the line

options snd-hda-intel model=3stack

Dunno yet if it works thou...

---

### Post by luca.marinosci@gmail.com on 2010-11-21
> **luca.marinosci@gmail.com said:**
> alt+f2
then type gksu gedit /etc/modprobe.d/alsa-base.conf

at the bottom of the file add the line

options snd-hda-intel model=3stack

dunno yet if it works thou...

works! Thx guys!!

---

### Post by Finn bjerke on 2010-11-26
Try this
[http://isallmaroon.wordpress.com/2010/05/08/no-microphone-input-in-skype-ubuntu-10-04/](http://isallmaroon.wordpress.com/2010/05/08/no-microphone-input-in-skype-ubuntu-10-04/)
 
worked 4 me

---

### Post by rfs1970 on 2011-04-01
> **fiercedrake said:**
> My hardware profile is Duplex. When I click on the input tab the signal measuring bar is always staying lit on the first section and does not move further. This means that the mic is not capturing sound. In 10.04.1 there was a dropdown menu in the input tab from which I could choose the default microphone and thus choose an option that works. In 10.10 there is no such thing. I kind of fixed it by adding  "options snd-hda-intel model=3stack" in alsa-base.conf. Now I have the dropdown menu and my microphone works for now. The problem is that I did not have to do this in 10.04.1 ...

Dude... I was trying to fix my microphone for ages.
Your solution work 100% for me.
Thank you for sharing!

---

### Post by Wilbefast on 2011-04-30
I had this problem, but it turns out that in the input tab of System > Preferences > Sound, the box marked "mute" is ticked by default for the standard Ubuntu 10.10 Desktop edition. As for why, I have absolutely no idea :confused:

---

