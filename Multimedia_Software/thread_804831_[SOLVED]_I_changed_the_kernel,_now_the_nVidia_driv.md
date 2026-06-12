---
title: "[SOLVED] I changed the kernel, now the nVidia driver simply does not work... :("
date: 2008-05-23
forum: Multimedia Software
---

### Post by Repgahroll on 2008-05-23
Hello there :D

I was running Hardy with the standard generic kernel, but this kernel just randomly freezes my Notebook (Compaq V6000 series) as the Gutsy and Feisty default kernels... when i was using Feisty, i changed the kernel to the server one, then on Gutsy, i was using the 386 one, couse i dont need smp, and now on Hardy, im trying to use the "server" one again, but i dont know why the nVidia driver just dont work any more :(...

I installed the system using the LiveCD and everything was ohkay... to install the video card, i just had to activate it using the "hardware drivers manager" and reboot the system... everything was fine, but it began to freezes... so i installed via apt-get the server kernel and purged the nvidia drivers in the generic kernel, but when i reboot the video wasnt working, then i removed the generic kernel and everything from nVidia, rebooted and tried again... wasnt working again.

after it ive tried:

EnvyNG
nVidia beta drivers from webçite
nVidia drivers via repositories
nVidia driver from the nVidia website
Old Envy

No matter what i do... always after reboot if the nvidia driver is configured in xorg.conf the screen blinks 3 times and the message "ubuntu is running on low graphics mode" appears... if i try to configure the nvidia driver using the wizard an error happens. :(

I hope someone can help me, because I'm using the generic driver nv wich is a lot bad :(...

Thank you
[SIZE="6"]Sorry my English[/SIZE]

---

### Post by Repgahroll on 2008-05-24
Solved! :D

Thanks! But i solved it! :)

MP me if u want to know how to solve it, and ill post tha saluttion here.

---

### Post by Don_Paul on 2008-05-25
> **Repgahroll said:**
> Solved! :D

Thanks! But i solved it! :)

MP me if u want to know how to solve it, and ill post tha saluttion here.

I would be VERY interested in your solusition, as I (and a lot of others) have the same problem.

---

### Post by Repgahroll on 2008-05-26
Oh man! im glad! =D

Sorry my english...


First thing I did was configure the nv driver, and then I ran the command "dpkg-reconfigure xserver-xorg" as root, then the monitor was working properly, all compatible modes was listed in xorg and the video card was listed properly too.

Then i uninstalled the nvidia driver via EnvyNG, and purgged the relative packages using apt-get, and then installed again the generic kernel and using it with the nv driver I purged the server one, then i reinstalled the server one and when I booted on it, the nvidia driver was listed in the restricted driver manager (hardware drivers).

Then I just installed it and everything was fine after a simple reboot :)... i didnt believe when i saw the rotating cursor on the right resolution and then the wallpaper with a ton of colors :)...

I can be wrong, i really dont understand much about such things, but i think that the nvidia driver will not detect the monitor unless if it is properly configured in xorg. And if the nvidia driver dont detect properly the monitor the driver itself will not work properly...

[SIZE="6"]Sorry my English!!

Hope it help! :D[/SIZE]

---

