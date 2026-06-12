---
title: "Strange thing? or not? (video drivers)"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by Hyssar on 2007-08-09
I am new to Linux and I'm proud of my choice.
But sometimes, its hard to do simple things...such as installing a video card driver!

My video card is a nVidia GeForce 7800 GS (AGP)
My system is Kubuntu 7.04 64-bit

That's why I'm posting a new thread, my case is quite particular.

I've been on nvidia.com ( just like what I've been doing every month on windows), go to Download Drivers, I select Graphic Drivers->GeForce 7->Linux x64

I download the 'NVIDIA-Linux-x86_64-100.14.11-pkg2.run' file.

When it is done, I open a Konsole and type 'sudo sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run'
the Konsole gets some colors, blue, green, red (its normal) and it asks me that I must shut down my X server to continue.

I open an other Konsole session and type 'sudo /etc/init.d/kdm stop'
everything is normal, I am now in text-only mode.
I retype 'sudo sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run' and now it asks me if I accept the license agreement...of course, I do. Then it tries to recover things from the internet and it asks me something like if I want to let it modify the kernel or something like that. It wants to do it in 32-bit. Then it verifies if something is blocking its way and it modifies xorg.conf

That's it.

It looks like I haven't done something needed before entering 'sudo sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run'

And it looks like that X.org does 'restarts' (when I type  'sudo /etc/init.d/kdm restart') but nothing appears (except a '_' symbol) in tty7 (supposed to be graphical)

What's happening?

Thanks, Ubuntu community!

---

### Post by Hyssar on 2007-08-11
I got no answer, so I will reinstall kubuntu..... :(

---

### Post by Steveway on 2007-08-11
NO!
Do a:
sudo nano /etc/X11/xorg.conf
and look for something saying nvidia.
You can change it to nv and do a ctrl+x then press y and enter.
Then you can go back to the graphical interface.
Then uninstall the driver, get envy and use that.
(Google if you can't find out howto uninstall or howto find envy.

---

