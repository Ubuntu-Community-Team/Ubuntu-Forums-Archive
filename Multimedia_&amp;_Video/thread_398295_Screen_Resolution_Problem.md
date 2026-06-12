---
title: "Screen Resolution Problem"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by jar3232 on 2007-03-31
Okie, I searched all the "how to" sections and nothing worked for me.  Sorry if this has been answered a million times, but I couldn't find a post regarding my problem.  

So what's the problem?  Well my screen resolution is set at 800x600 and won't go any higher.  I am having flash backs to WIN95.  I went through, and believe I installed the legacy driver, but I am really not sure.  It didn't solve the problem, so I am assuming I did something wrong.  

Video card specs: 
Nvidia GeForce 2 intergrated - 32 mb (I know it's old)
01:00.0 0300:  10de:01a0

Monitor is a compaq 5017 LCD

I am "trying" to run Ubuntu version 6.10 - 2.6.17.10-generic

Thanks in advance...

---

### Post by Majorix on 2007-03-31
Have you configured X?

```
dpkg-reconfigure xserver-xorg
```

---

### Post by jar3232 on 2007-03-31
> Have you configured X?

I come up with this:

/usr/sbin/dpkg-reconfigure must be run as root

??

---

### Post by willzofsteel on 2007-03-31
You need to run it as root like this
```
sudo dpkg-reconfigure xserver-xorg
```

I tryed using the above command, it runs the setup and although it looks like it updates
xorg.conf successfully(driver says nvidia instead of nv), i restart x. but im stuck in 800x 600 and nothing else.

---

### Post by willzofsteel on 2007-03-31
also Im running

i686 build ubuntu
Geforce7900 Gs
Athlon 64
ViewSonic PF790 monitor

whats your setup like? let me know if the above was successful to you.
also another thing i forgot to mention is that i had successfully set the resolution past 800x600 before but i installed Beryl, it worked, something later happened and system crashed and all the settings x settings went back to 800x600 and i havent been able to get them past. I can get the resolution past 800x600 with the nv driver but that driver doesnt contain the glx acceleration needed for Beryl.
:(

---

### Post by jar3232 on 2007-04-01
> dpkg-reconfigure xserver-xorg

Okie, I ran it, and now ubuntu won't start...

](*,)

Edit: Had to run recovery mode, then it worked...

YEAH FIRST THING TO WORK...

---

