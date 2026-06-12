---
title: "X window server goes belly up after installing beryl"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by ScottMac on 2007-07-08
hi

i installed beryl and messed around with the settings, it worked fine. i then shutdown and the next time i started  up x cannot boot up and it says that there is an error with the nvidia module.

heres how i think i could solve the problem: boot using livecd and replace the current xorg.conf with the unedited version from the livecd. ill uninstall and then reinstall envy so that my nvidia support is in the new xorg.conf. after this everything should be back to normal???

has anyone else had this problem and do you think my way of fixing it would work??

thanks
scott

---

### Post by ScottMac on 2007-07-09
well no one answered.... im a bit dissapointed

anyway i did what i outlined above and it worked fine. the only problem is that when working purely in the gui, you dont have enough rights to copy the xorg.conf into your filesystem directory from the livecd file system.

i tried this and it worked:

sudo cp /etc/X11/xorg.conf /wherever your hard drive is

it didnt ask me for a password but copied the file.

i then rebooted and x worked fine. i had to reinstall the nvidia drivers using envy so that i could use nvidia-settings again to get my resolution and refresh rate right.

well problem solved but i am a bit bummed that NO ONE replied

scott

---

