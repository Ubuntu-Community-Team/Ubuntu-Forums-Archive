---
title: "help enabling 3d acceleration, nvidia"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by AvalonSpirit on 2007-06-13
I didn't know whether to post this here or in the hardware forum.

Does anyone know how to enable 3d acceleration?

I am kind of new to Linux, so i dont know if i am installing the drivers correctly, currently i just do apt-get install [pkg name] with the driver pakages, is anyhting else required??

I have an nVidia GeForce MX 4000 GPU

I was having problems getting beryl to work and then google earth, and finaly figured out what was wrong,  the 3d acceleration is not enabled, and when i tried to run google earth or the beryl widow manager it said something about not having "GLX" and no screens to manage.(sorry i dont have the exact error maessage), I enabled the restrivted drivers thing, i tried installing new drivers (nvidia-glx-legacy, nvidia-glx-new and the one from the nvidia page) but they didn't work, it only messed up my x configuration. and my computer stopped loading the x server it said something about failure to initiate nvidia kernel module. it got to the point that even if i switched to nv instead of nvidia in the xorg.conf file it didn't want to work, i replaced the xorg.conf file with the backup and nothing. I reinstalled ubuntu out of frustration of not being able to load the GUI and here i am.

And what the hell is the "GLX"? any help here would be really appreciated as its driving me nuts.

Thanks,

AS

---

### Post by Bruegger on 2007-06-14
Hi,
As you mentioned, 3d and glx need to be enabled to play 3d games and to make beryl work.
They get enabled when you install the correct drivers for your card.

Depending upon your card, you may either need nvidia-glx-legacy or nvidia-glx or nvidia-glx-new for your card.
You can see on the nvidia site if your graphics card is supported for a particular driver or not.
To identify your graphics card, you can log into the terminal and run lspci.

Try using envy to install your drivers.It will select and install the proper drivers for your card.
For detailed help on installing nvidia-drivers you can refer to this excellent post.

[http://ubuntuforums.org/showthread.php?t=432056](http://ubuntuforums.org/showthread.php?t=432056)

Cheers!

---

### Post by AvalonSpirit on 2007-06-14
I'll try that thanx

---

