---
title: "Disabling restricted drivers w/o X environment"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by Nzer24 on 2007-09-23
I have a bit of a problem...

I just upgraded my video card from a nVidia 7300 GT to a nVidia 8800 GTS. Unfortunately, I completely forgot to disable the restricted driver for the old card before I replaced it, and now it won't allow me to use GNOME because the driver is wrong. I have a command line and root access, but I don't know which file I should change and how to change it to manually disable the driver. I already tried changing the name of my card in the xorg.conf file because it seemed that I had a universal nVidia driver set and the specific one being used might be wrong, but that didn't work.

Any help would be appreciated!

---

### Post by scrooge_74 on 2007-09-23
either change in xorg.conf to  "nv" so you have the open source driver and can work in Gnome to fix it or you can try sudo dpkg-reconfigure xserver-xorg

---

### Post by Nzer24 on 2007-09-23
Sorry it took so long to reply.

I tried both of those suggestions and neither worked. I was able to reinstall the old video card and disable the driver. However, when I put the new card in and installed it's restricted driver through GNOME, it restarted with the same error as before. I then downloaded a driver from the nVidia website, but it didn't seem to install correctly and now neither card works. I can't seem to get this new driver off and it says that there is a problem with it's kernel module. Is it possible to fix this or should I just copy over files and reinstall Ubuntu?

---

### Post by scrooge_74 on 2007-09-23
Maybe you need to offload a module (using the  **modprobe** command)or black listed, sorry I can be of much help, try changing the driver to either "nv" or "VESA" in the xorg.conf so you can at least get a working GUI back

---

### Post by Nzer24 on 2007-09-24
Well, I tried using modprobe but I couldn't really figure out how to. Instead I tried both the blacklists and the kernel module directories, but neither worked. If you really think modprobe will work, please explain how to use it, otherwise, I'll just reinstall linux.

---

### Post by scrooge_74 on 2007-09-24
if I am not mistaken (you can always check man modprobe)

the command would be sudo modprobe -r  (module name) to remove it

---

