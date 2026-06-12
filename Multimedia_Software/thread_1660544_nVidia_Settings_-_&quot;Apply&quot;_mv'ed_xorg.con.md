---
title: "nVidia Settings - &quot;Apply&quot; mv'ed xorg.conf"
date: 2011-01-05
forum: Multimedia Software
---

### Post by Cyclops_ on 2011-01-05
Hey all...

I have two different config files for xorg, basically for two different setups.  In order to switch setups I have to do something like this:

$ cd /etc/X11/
$ sudo mv xorg.conf.setup1 xorg.conf  (or xorg.conf.setup2, whichever the case)
... logout, and then log back in

Is there any way to have the video "reset" to the other config without having to logout and log back in?  I *know* there MUST be a way, since you can pull up nVidia settings, change stuff (as long as it's twinview only and not a new X), and then just click "Apply" and it will change the config... but since I'm manually changing the xorg.conf, is there a way to just apply it, provided that it's still twinview?

MANY thanks for the help!!!

---

### Post by BicyclerBoy on 2011-01-05
I believe you can set multiple "option" one at a time ..
e.g.
 nvidia-xconfig --mode 1600x1200 --something

I think you have to restart the X server to reparse the xorg.conf file.

---

### Post by Cyclops_ on 2011-01-05
So how does nvidia-settings do it?  I mean, it can change configuration on the fly!  (That's what I'd like to do.)

---

### Post by BicyclerBoy on 2011-01-06
I imagine it does exactly what I showed as an example..
That does not restart the X server.

 nvidia-settings warns you if the X server must be restarted to complete the changes.

You need to find the command options & if they will do what you need.

Twinview could be more of a problem than solution..

Have you read dynamic twinview & metamodes ?

[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/configtwinview.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/configtwinview.html)

---

### Post by Cyclops_ on 2011-01-06
Thanks for sending that!  It got me thinking, and I tried just using the nVidia settings again, and I was able to just go back and forth with that without having to change xorg files, which is just fine with me!

So, while I didn't find a way to answer the original question, I'm still quite happy :)

Thanks very much for the help! :)

---

### Post by coxtor on 2011-11-04
Hello, although this thread is very old, could you please post what exactly you used to acquire your desired result?
I am new to linux and haven't managed to get this working via sh script or commandline.
Thank you

---

### Post by Cyclops_ on 2012-04-21
coxtor - 

Did you ever get it to work?  I think nvidia-settings has been working for me, more or less, for a while now (maybe around Unity?).

Anyway, let me know, I may be able to help.

Thanks.

---

