---
title: "Logitech USB Headset Problems"
date: 2008-10-03
forum: Multimedia Software
---

### Post by carlos1 on 2008-10-03
I searched the forum but couldn't find a good answer for this, or anything that addresses my specific problem.

I'm running Kubuntu 8.04, with KDE 3.X, and am trying to use a Logitech USB headset.

I've got it running fine with Skype and Amarok - both the headphones and microphone work. 

However, when I try to enable sound for anything else - internet Audio, system notifications, etc., I cannot get any sound out. 

According to my system settings, I have ALSA selected, and it seems to be working for some apps.

Can anyone tell me how I can get the headset to work as the default audio device?

Thanks!

---

### Post by hansdown on 2008-10-03
Hi carlos 1.

Ther is one solved thread. [http://ubuntuforums.org/archive/index.php/t-563670.html](http://ubuntuforums.org/archive/index.php/t-563670.html)

I hope it has something helpful for you.

---

### Post by markbuntu on 2008-10-03
You could just get PulseAudio. Then you could use it to move playing apps to and from your sound card and headset. And it works with skype. I have a zillion page guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Otherwise you can just change your default sound to the usb device but I am not sure how you would go about that in kbuntu. There has to be some sort of sound control device. Alsa has a little gui app called asoundconf-gtk that lets you choose your default sound card. Like I said, I am not familiar with kbuntu but if it is in their repos it should work for you.

---

