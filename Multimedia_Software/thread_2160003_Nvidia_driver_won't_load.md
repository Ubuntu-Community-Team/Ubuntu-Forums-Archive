---
title: "Nvidia driver won't load"
date: 2013-07-05
forum: Multimedia Software
---

### Post by dannyboy79 on 2013-07-05
I am running Xubuntu 12.04 64bit, kernel 3.7 from a custom PPA I believe (not at home at the moment to check exact kernel). I have an Nvidia 8400GS (PCIe) and was running nvidia-current module, i was notified of some updates which installed but then prompted me to restart. 
I restarted but it hangs at the Xubuntu Splash screen with the 4 white dots blinking in succession, I thought maybe it was due to my Logitech Webcam because when I turned off the splash I saw "could not set frequency 16000 blah blah" but even when I unplugged it, it would still hang at bootup, I forget what the last message is that I see when I turn off the splash screen (again I'll update the post when I get home, I just wanted to get this posted to see if anyone had any ideas).
So i thought, hey i'll just boot to the previous kernel 3.6.2 and it got me to lightdm so I could login BUT it's running the VESA gfx driver. I went to Nvidia website and noticed that 319.32 was released so I went to tty1 and stopped lightdm, I ran the installer with sudo adn it said it installed successsfully. I double checked my xorg.conf file and it does call for driver "nvidia" so I then issued sudo service lightdm start and it brought me to lightdm to login BUT again it's only running VESA graphics driver.

Can anyone tell me why the nvidia driver isn't being used?

---

### Post by gordintoronto on 2013-07-05
The normal way to install a video driver is by using Additional Drivers. Off the top of my head, I'm not sure where that is in Xubuntu. Perhaps you can run Synaptic and search for nvidia-current.

---

### Post by dannyboy79 on 2013-07-05
additional drivers does show nVidia Riva/TNT/GeForce driver activated BUT not in use.

---

### Post by dannyboy79 on 2013-07-06
additional drivers does show nVidia Riva/TNT/GeForce driver activated BUT not in use when I boot into kernel 3.6.2-030602-generic and no matter what jockey just keeps failing to load any of the nvidia drivers.

I went back and tried kernel 3.7.0-030700-generic and everything is working again. it booted up and I am running Nvidia driver from jockey 304.88

---

