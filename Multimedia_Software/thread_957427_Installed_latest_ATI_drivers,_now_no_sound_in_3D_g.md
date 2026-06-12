---
title: "Installed latest ATI drivers, now no sound in 3D games."
date: 2008-10-24
forum: Multimedia Software
---

### Post by desicratn on 2008-10-24
I followed the [http://wiki.cchtml.com/index.php/8.10](http://wiki.cchtml.com/index.php/8.10) way to install the latest ATI drivers and it went well, except I now have no sound in ET, ETQW, Supertux cart etc. Amarok still works, I have sound just not  in a 3D game...

Under the sound panel I now have an HDA ATI HDMI( Alsa mixer) device that I did not have before. It is blank but I have no idea how to get rid of it.

Any ideas or help would be appreciated.

---

### Post by desicratn on 2008-10-27
Wow, nothing???

<sigh>

---

### Post by markbuntu on 2008-10-28
Until the latest drivers, the hdmi output was not working but now it is which is great if you are using HDMI but not so good when you are not and it becomes the default for your games. But, this is pretty easy to fix and there are many ways to do it. Porbably the easiest is to get

asoundconf.gtk

from the repos. Once it is installed it will be in System/Preferences/Default Sound Card. Open it and choose your sound card that is not the HDMI. You may have to reboot for that to work.

If these applications play through pulseaudio you can change the default output device in the pulseaudio volume control by right clicking on it in the Output Devices tab. 

pavucontrol

If you want to use pulseaudio to control these applications you can change the default sound card from above to pulseaudio. 

NOTE: this may or may not work depending on your sound configuration. If you are not confused yet and you have nothing else to do for a few hours you can go to my 10,000 page guide to setting up sound and either get totally confused or become an expert:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by desicratn on 2008-10-30
Wow. That worked like a charm.
 Got the 1st one and that solved it for me in every game except Wolfenstein ET. 
Thank you. I think I will bookmark that thread and read up on it someday when I have more time to kill.

Thank you so much.

---

