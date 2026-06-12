---
title: "PPA for installing latest version of Gphoto2"
date: 2016-06-26
forum: Multimedia Software
---

### Post by joverstreet1 on 2016-06-26
What is the PPA for installing the latest version of Gphoto2 ?

Thanks.

---

### Post by vasa1 on 2016-06-26
Which version of Ubuntu are you using? Launchpad is the place most of us get ppas from. Type "gphoto2 ppa" in the search box and click search.

I don't see any recent ppas for gphoto2 there. 

Why do you need a ppa? Maybe someone has a workaround to your problem?

[https://sourceforge.net/projects/gphoto/files/](https://sourceforge.net/projects/gphoto/files/) shows libgphoto2-2.5.10.tar.bz2 (7.0 MB) as the latest version if you really have to go that route.

---

### Post by joverstreet1 on 2016-06-26
> **vasa1 said:**
> Which version of Ubuntu are you using? Launchpad is the place most of us get ppas from. Type "gphoto2 ppa" in the search box and click search.

I don't see any recent ppas for gphoto2 there. 

Why do you need a ppa? Maybe someone has a workaround to your problem?

[https://sourceforge.net/projects/gphoto/files/](https://sourceforge.net/projects/gphoto/files/) shows libgphoto2-2.5.10.tar.bz2 (7.0 MB) as the latest version if you really have to go that route.

Thanks.

Have downloaded 2.5.10 but for the life of me I can not figure out how (what terminal commands) are used to install this thing.  Have read the readme files and tried following instructions given there but they do not seem to work.

Reason for possibly needing is that Canon EOS Rebel T6 1300 D camera will not work with Linux "Camera.app" application with earlier version of Gphoto2.

Thanks.

---

### Post by Dennis N on 2016-06-26
libgphoto2 in your quote in post #3 is just a library, not an application. If that is what you have, you also need gphoto2 (or gtkam) obtained from the same place as a gui. These packages are source files and have to be compiled.

---

### Post by Dennis N on 2016-06-26
I see gphoto2 version 2.5.9 in the Xenial repository. Will that not suffice?

---

### Post by uwe-bungto on 2016-07-01
> **joverstreet1 said:**
> What is the PPA for installing the latest version of Gphoto2 ?

Thanks.
The latest downloads [gphoto2-5.10]("https://sourceforge.net/projects/gphoto/files/") is here

---

### Post by Linuxisfast on 2016-07-02
```
[COLOR=#333333][FONT=Consolas] wget https://raw.githubusercontent.com/gonzalo/gphoto2-updater/master/gphoto2-updater.sh && chmod +x gphoto2-updater.sh && sudo ./gphoto2-updater.sh[/FONT][/COLOR]
```

---

### Post by joverstreet1 on 2016-07-03
> **Linuxisfast said:**
> ```
[COLOR=#333333][FONT=Consolas] wget https://raw.githubusercontent.com/gonzalo/gphoto2-updater/master/gphoto2-updater.sh && chmod +x gphoto2-updater.sh && sudo ./gphoto2-updater.sh[/FONT][/COLOR]
```

  O.K. - I finally figured it out how to install this BUT, the gphoto2 was apparently not the cause of the problem that I am having.

Once I got this installed, I still had the problem of the Linux Camera.app not being able to recognize the fact that my Canon EOS Rebel T6 1300D camera has photos stored on it.  Apparently, the hardware listing file that stores the USB parameters for various digital cameras is created by the Linux program called "CAMERA.APP".

Now if I can figure out who to contact about getting the Canon EOS Rebel T6 1300D included on that listing.  Any ideas as to who that might be ???

Thanks.

---

### Post by Linuxisfast on 2016-07-03
> **joverstreet1 said:**
> O.K. - I finally figured it out how to install this BUT, the gphoto2 was apparently not the cause of the problem that I am having.

Once I got this installed, I still had the problem of the Linux Camera.app not being able to recognize the fact that my Canon EOS Rebel T6 1300D camera has photos stored on it.  Apparently, the hardware listing file that stores the USB parameters for various digital cameras is created by the Linux program called "CAMERA.APP".

Now if I can figure out who to contact about getting the Canon EOS Rebel T6 1300D included on that listing.  Any ideas as to who that might be ???

Thanks.


Did you try changing USB mode in your camera? From MTP to PTP?

---

### Post by joverstreet1 on 2016-07-03
> **Linuxisfast said:**
> Did you try changing USB mode in your camera? From MTP to PTP?

I do not see any USB mode setting, am I missing it ?

Thanks.

---

### Post by Linuxisfast on 2016-07-04
> **joverstreet1 said:**
> I do not see any USB mode setting, am I missing it ?

Thanks.

Go to connection mode in your camera and see what options you have.

---

