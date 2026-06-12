---
title: "Gutsy ivtv 1.0.2 package available?"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by android19 on 2007-09-16
I installed Mythbuntu 7.10 Public Alpha 4, which uses Gutsy's linux-image-2.6.22-10-generic kernel.  I need the ivtv-fb module so that I can run X through the framebuffer on my Hauppage PVR-350.

For kernels 2.6.22 or greater, the main ivtv drivers are baked into the kernel but the ivtv-fb module is not included.  On ivtvdriver.org, there is a new 1.0.x driver that supplies the ivtv-fb driver missing in the core kernel.  Is there any plan to provide a package for the 1.0.x ivtv drivers in Gutsy?

Does anyone have any pointers on installing ivtv 1.0.2 from source?  I tried building it and got nowhere fast. . .

```

~/ivtv-1.0.2$ make
make -C driver all
make[1]: Entering directory `/home/xxxx/ivtv-1.0.2/driver'
make -C /lib/modules/2.6.22-10-generic/build M=/home/xxxx/ivtv-1.0.2/driver modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.22-10-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/xxxx/ivtv-1.0.2/driver'
make: *** [all] Error 2

```

---

### Post by dawson64 on 2007-09-30
I'm looking to do the same thing & found your post while searching around.  Did you figure it out?

I'm going to keep looking...

---

### Post by kkonradd on 2007-11-19
You should read some docs about module building... the error message is quite clear, you're missing the kernel headers...

Type "aptitude search linux-headers" and pick up the package corresponding to your kernel ("uname -r" will give you the kernel version you're running) and install it via aptitude install

Once the headers are installed make sure that you have a symlink /lib/modules/<your kernel version>/build that points to /usr/src/linux-headers-<your kernel version>. If you don't, use ln -s to make it.

---

### Post by jakemonO on 2007-11-20
same problem. any luck? I'm in the middle of attempting to compile using the moudle asistant, as generally outlined in an older FAQ [here]("http://ubuntuforums.org/showthread.php?p=3807669&posted=1#post3807669") I'll update this post with more info...

---

