---
title: "simple query in the definition of sound"
date: 2010-10-12
forum: Multimedia Software
---

### Post by mountdiat on 2010-10-12
Peace, mercy and blessings of God
 
I have a simple query in the definition of sound
 
when I have installed Ubuntu10.4  for the first time is not defined sound
And followed these steps::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
 1-Removing PulseAudio
   sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
 2-Removing ALSA packages
 sudo /etc/init.d/alsa-utils stop sudo apt-get remove alsa-base alsa-utils 3-Blacklisting ALSA Kernel Modules sudo dpkg-reconfigure linux-sound-base 

 4-[SIZE=2]Installing OSS    [/SIZE] 
  [SIZE=2]5-Configuring Applications to Use OSS[/SIZE]
 [SIZE=2]gstreamer-properties[/SIZE] [SIZE=2]::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::[/SIZE]
It was then the definition of sound, [SIZE=6]but[/SIZE] .......
*Can not open the volume control
**sound icond does not appear
***Low sound almost
            *****************************************************
But when install virtualbox and  install  fresh Ubuntu 10.4
Only you choose the appropriate definition of the sound &#8221;&#8221; oss  or    PlseAudio&#8221;&#8221;'did not show any of the previous problems
[SIZE=4]Question 1:-[/SIZE]How do Iselect  the sound driver  directly as in virtualbox??
 Question 2:-  if failed:-how can i solve  previous problems??
 

 my motherboard is gigabyte g41  
 

 please help .................

---

### Post by mountdiat on 2010-10-12
please help .................

---

### Post by cchhrriiss121212 on 2010-10-12
If you have installed OSS then you need to use OSSmixer to control sound levels.

---

### Post by mountdiat on 2010-10-12
> **cchhrriiss121212 said:**
> If you have installed OSS then you need to use OSSmixer to control sound levels.
from where.............:confused:

---

### Post by cchhrriiss121212 on 2010-10-12
Software center is the tool to use to install anything. Open it up and search for "oss mixer" and you should see plenty of options. I think the original ossmixer may be outdated now, but I'm not sure as I don't use OSS.

---

