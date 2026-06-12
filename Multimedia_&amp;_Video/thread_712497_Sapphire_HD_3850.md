---
title: "Sapphire HD 3850"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by TomBull on 2008-03-01
Does anyone have an ATI Radeon Sapphire HD 3850 video card that works in Ubuntu?

---

### Post by Melcar on 2008-03-01
I used to run one, and yes, it worked very well with the latest drivers (7.11 and later).

---

### Post by TomBull on 2008-03-02
I don't suppose you can tell me how to get it to work could you?

---

### Post by Melcar on 2008-03-02
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

Use Method 2.  One thing to note is that if you're running a 64bit OS, you will need an extra dependency, ia32-libs, for the driver to install properly.  Another thing is to not blacklist fglrx in linux-restricted-modules-common like the guide says, since I have found that when doing that fglrx would not load (regardless if you got it from the repos or not).

You can also just run the installer straight up, instead of building packages.;

```
sudo sh ati-driver-installer-8.02-x86.x86_64.run
```

 Just make sure you also have all the required dependencies (the ones listed in the guide) as well as ia32-libs (if running 64bit).  When the installer finishes, just initialize the driver the same way the guide specifies:

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

---

### Post by TomBull on 2008-03-02
Thanks I followed the guide and didn't work so I will try again and follow your advice.
I see a lot of post for ATI problems so I'm not the only one having trouble.

---

