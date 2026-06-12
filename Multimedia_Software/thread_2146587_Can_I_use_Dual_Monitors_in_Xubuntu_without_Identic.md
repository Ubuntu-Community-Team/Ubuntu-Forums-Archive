---
title: "Can I use Dual Monitors in Xubuntu without Identical Desktops?"
date: 2013-05-19
forum: Multimedia Software
---

### Post by Mahogan on 2013-05-19
I just installed Xubuntu 13.04 on my desktop with dual monitors.  To my surprise, both monitors display the same content rather than extend the desktop as in Windows.  I have messed around with the settings under Display, but only see settings to adjust resolution, refresh, rotate and reflection, none of which allow me to extend the desktop as one continous, non repeating workspace.  I do not want identical info on each monitor, it defeats the purpose.  

I would imagine this is possible, but cannot figure it out.  I have searched but found old posts and many commands for tech savvy users.  I'm not too savvy and don't understand.

Any suggestions?

---

### Post by QIII on 2013-05-19
Hello!

Could you let us know what graphics you are using and whether or not you have the default open source driver installed or a proprietary driver?

It appears that you accidentally misspelled "Windows", so I have corrected that for you.

Thanks!

---

### Post by Mahogan on 2013-05-19
Hi, thanks for your reply.  I am using the default drivers that Xubuntu installed.  I do not know how to even see what the driver name is that it used, or how to install a proprietary driver.  My video card is an NVIDIA GeForce 8600 GT.

Suggestions?

---

### Post by Mahogan on 2013-05-25
Does anyone have an idea of how to make this work?

---

### Post by sudodus on 2013-05-26
I have not tested Xubuntu 13.04, but I just tested Xubuntu 12.04.2 i386 LTS (live) and Ubuntu 12.04.2 amd64 LTS (installed) in a rather new Toshiba with intel i5 and intel graphics, so using the built in drivers.

It was possible to make Ubuntu show different desktops (side by side) with the standard monitor tool. But I could not make that work with Xubuntu. Either it showed low resolution (1024x768) with the same image, or both monitors showed their full resolution, the external one with a copy of the internal monitor's image at the top left corner. Funny!

I think you can to install an old proprietary nvidia graphics driver, reboot and use its monitor tool, which might work better than Xubuntu's built in tool for dual monitors.

In 13.04 the recommended proprietary graphics drivers are integrated into the package management, so you can install it with ***apt-get***, ***Synaptic*** or ***Software Center***.

I suggest that you try to install either ***nvidia-current*** or ***nvidia-173***, and that you use ***nvidia-settings*** to manage the two monitors. Remove them, if it does not work. Then the built-in drivers will be used again.

---

