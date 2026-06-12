---
title: "NVIDIA card not working"
date: 2008-04-25
forum: Multimedia Software
---

### Post by America's Sweetheart on 2008-04-25
I managed to get 8.04 to boot on my system by selecting the older kernel (6.22.14) from the boot menu. My video card (GE Force 7300) won't work at all now, though. I tried using EnvyNG, but that didn't work. I then tried running NVIDIA's installler. I pressed CTRL + ALT + F1 and then shut down the X server (/etc/init.d/gdm stop). Now it says that it can't build from source because my compiler is too new. I have 4.2, but since the kernel was built with 4.1, the installer won't work. I dowloaded the source code for 4.1 and typed ./configure, but it says, "cannot find install-sh or install.sh in . ./.. ./../.." Miraculously, though, I found gcc 4.1 in Synaptic. (It wasn't there before.) So, I installed 4.1, but I can't uninstall 4.2. Doing so removes gcc. If I re-install gcc, 4.2 re-appears. I read somewhere about typing "cc=export-4.1" and then "export cc." But that doesn't work, either.

If someone could respond to this, that'd be great.

---

### Post by davidsrsb on 2008-04-26
I have two very different machines with 7300LEs
One uses the nv driver, no problems as it does not need OpenGL performance.
The other I have just upgraded from 7.10 to 8.04 and found compiz effects still had the loss of Windows controls problem
I had a look at the packages and found that it was running nvidia-glx.
I removed this and installed nvidia-glx-new
After a reboot everything seems top work properly

I think you need to back up /home and do a clean re-install, you should not need EnvyNG etc

---

