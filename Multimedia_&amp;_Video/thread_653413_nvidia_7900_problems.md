---
title: "nvidia 7900 problems"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by Ponomous on 2007-12-29
Hi, I am new to ubuntu and am having some problems (by some i mean two)

First i cant figure out how to install the drivers for my graphics card, a nvidia 7900 gs.  i have checked out a bunch of tutorials, grabbed the drivers for linux from the nvidia site and no luck.  The card is definitely recognized, its showing up in the restricted drivers but as one that cannot be used.  I am multibooting ubuntu 7.10 and windows xp right now.  Any help would be much appreciated.  Let me know what information you would like me to post up.

Thanks

---

### Post by overdrank on 2007-12-29
> **Ponomous said:**
> Hi, I am new to ubuntu and am having some problems (by some i mean two)

First i cant figure out how to install the drivers for my graphics card, a nvidia 7900 gs.  i have checked out a bunch of tutorials, grabbed the drivers for linux from the nvidia site and no luck.  The card is definitely recognized, its showing up in the restricted drivers but as one that cannot be used.  I am multibooting ubuntu 7.10 and windows xp right now.  Any help would be much appreciated.  Let me know what information you would like me to post up.

Thanks

Hi and you may look at Envy, [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
And why do you say that you cannot use the restricted drivers? Have you tried to reconfigure your xorg after you enable the restricted drivers?

---

### Post by Ponomous on 2007-12-29
Thanks i will try envy tomorrow when i can move my comp over to where my router is for a direct connect, up in my room right now and only wireless connection available which is my other problem lol.

as for the restricted drivers, i didnt do anything with them, when i double click to see the restricted drivers in use, the graphics card is in there but it says its not in use and cant be turned on.  i will grab a screen shot or type exactly what it says later, in the middle of some work that i really want to get done.

Thanks again

---

### Post by overdrank on 2007-12-29
> **Ponomous said:**
> Thanks i will try envy tomorrow when i can move my comp over to where my router is for a direct connect, up in my room right now and only wireless connection available which is my other problem lol.

as for the restricted drivers, i didnt do anything with them, when i double click to see the restricted drivers in use, the graphics card is in there but it says its not in use and cant be turned on.  i will grab a screen shot or type exactly what it says later, in the middle of some work that i really want to get done.

Thanks again

Ok if you would like to try before Envy by going to synaptic package manager and search for nvidia-glx-new and make sure that it is install then you can reconfigure you xorg after the installation. Good luck!

---

### Post by Ponomous on 2007-12-29
>  Ok if you would like to try before Envy by going to synaptic package manager and search for nvidia-glx-new and make sure that it is install then you can reconfigure you xorg after the installation. Good luck! 

How do i do this?  I am new to ubuntu and still havent figured everything out.  Also is the nvidia-glx-new the drivers that came with ubuntu?  if so they are out of date and wont actually allow me to run the card (i saw this somewhere else in the forum)

Thanks for all you help

---

### Post by overdrank on 2007-12-30
> **Ponomous said:**
> How do i do this?  I am new to ubuntu and still havent figured everything out.  Also is the nvidia-glx-new the drivers that came with ubuntu?  if so they are out of date and wont actually allow me to run the card (i saw this somewhere else in the forum)

Thanks for all you help

Hi and I have not used that model of card as of yet but did help someone yesterday to get it going. If you are looking for synaptic manager it is located under system, administration. Then as stated search for that driver and install. Then you can reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` This should configure you xorg then use the keys ctrl, alt, backspace and that will restartx. Hopefully this will return you to the GUI.

---

### Post by Ponomous on 2007-12-30
Thanks a bunch ill let you know if that works.

---

### Post by Ponomous on 2007-12-31
Ok so i got it working after i connected to the internet and downloaded directly from the nvidia site and installed some updates.  dont kno why copying the origional linux drivers over didnt work but oh well.  I never got around to using envy since i didnt need to.

Thanks for the help

---

### Post by overdrank on 2007-12-31
> **Ponomous said:**
> Ok so i got it working after i connected to the internet and downloaded directly from the nvidia site and installed some updates.  dont kno why copying the origional linux drivers over didnt work but oh well.  I never got around to using envy since i didnt need to.

Thanks for the help

Great glad to hear, Please mark the thread as solved under thread tools and Good luck! :popcorn:

---

