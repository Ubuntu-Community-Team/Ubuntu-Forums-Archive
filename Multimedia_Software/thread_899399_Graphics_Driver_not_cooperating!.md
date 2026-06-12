---
title: "Graphics Driver not cooperating!"
date: 2008-08-24
forum: Multimedia Software
---

### Post by Wickd on 2008-08-24
Hi there

I currently have the Asus Nvidia Geforce 8500GT Graphics Card. If I enable the generic Nvidia drivers that comes supplied with the Hardy Desktop Cd I cannot increase my resolution to above 1024 x 768. If I disable it then I can go higher

How is this possible? Please help

Thanks in Advance

---

### Post by overdrank on 2008-08-24
> **Wickd said:**
> Hi there

I currently have the Asus Nvidia Geforce 8500GT Graphics Card. If I enable the generic Nvidia drivers that comes supplied with the Hardy Desktop Cd I cannot increase my resolution to above 1024 x 768. If I disable it then I can go higher

How is this possible? Please help

Thanks in Advance

Hi and welcome, after you enable the drivers you can install nvidia-settings via synaptic manager and then use the command ```
gksu nvidia-settings
``` and adjust your resolution there.

---

### Post by Wickd on 2008-08-24
Ok I might have gone and actually worsen the situation. I went to the official Nvidia website and downloaded the linux version of 8 series card. I then followed the installation instructions as given here: [http://samiux.wordpress.com/2007/06/15/geforce-8500gt-on-ubuntu-704/](http://samiux.wordpress.com/2007/06/15/geforce-8500gt-on-ubuntu-704/)

And I basically screwed up something. Now everytime I restart it informs me that I am running at low graphics and that it cannot detect my screen or graphics card.  I think it may be the two drivers conflicting.

Help....

Thanks in advance

PS: You cannot set your resolution in nvidia settings, only gamma and a few other things.

---

### Post by Wickd on 2008-08-24
Ok nevermind. I just uninstalled the generic version. And then the nvidia settings command worked perfectly

Thank You!

---

