---
title: "Not able to install Natty Narwhal"
date: 2011-02-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by poonforce on 2011-02-16
i m trying to install Ubuntu Natty Narwhal from Live CD.
But after some ie after splash screen, my screen just goes wierd, i m not able to read anything on that.

Earlier i upgraded 10.1 to Natty but again during start up my monitor shows error "Out of Range". After that again i m not able to read anything on the screen.

so i decided to install from live CD, but that is also not working.

my mother board is ASUS M2N MX SE PLUS
Processor AMD Athlon 4600+
Ram 2GB

Please help 
Thanks in advance

---

### Post by howefield on 2011-02-16
Moved to *Natty Narwhal Testing and Discussion*

---

### Post by sikander3786 on 2011-02-16
First of all, remember that Natty is not the stable version of Ubuntu at present. The stable 11.04 will be out in late April this year.

The current versions of Ubuntu are 10.04 and 10.10. Download any of them unless you know how to deal with alpha and beta stage Operating System and if it is not a production machine.

That weird screen, blank screen problem is common with 'X' these days due to some bug I think. You need to put in the nomodeset boot parameter. See here.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

It is also mentioned here and also some other common boot problems.

[http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html](http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html)

If you decide to install Natty, you might need to follow manual/advanced partitioning if you need to dual boot.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

Keep us posted ;-)

---

### Post by VMC on 2011-02-16
> **poonforce said:**
> i m trying to install Ubuntu Natty Narwhal from Live CD.
But after some ie after splash screen, my screen just goes wierd, i m not able to read anything on that.

...

Weird like [_**this**_]("http://ubuntuforums.org/showpost.php?p=10446196&postcount=1") ?

---

### Post by cariboo on 2011-02-16
> **VMC said:**
> Weird like [_**this**_]("http://ubuntuforums.org/showpost.php?p=10446196&postcount=1") ?


Did you try installing nouveau to see if that helps at all?

---

### Post by VMC on 2011-02-16
> **cariboo907 said:**
> Did you try installing nouveau to see if that helps at all?

I just did a few hours ago. It didn't work.
 I haven't run nouveau for quiet a while now - normally use nvidia drivers.. I choose the first choice. I see three choices, and the "3D" selection is on the bottom. Should I have chosen that one?

---

### Post by kerry_s on 2011-02-16
unity uses compiz, so yes you need 3d.
i wouldn't install it right now in it's current state, i just got finished trying it & it's not good. best to wait till after march 24 when they do the ui freeze, if it's not ready by then forget about it.

---

### Post by cariboo on 2011-02-16
I was a bit distracted when I wrote my previous post, it should have said nouveau-firmware, instead of just nouveau.

---

### Post by poonforce on 2011-02-23
i installed natty narwhal but i have to run it in failsafe graphic mode every time, then only i can read my monitor. 

when i start it normally it boots up without any errors but after booting, my screen goes wierd, i just cant read and make out anything on the screen. 
when i install restricted driver, then even failsafe graphic mode doesnt run.
please help

---

### Post by cariboo on 2011-02-23
It would help if you told us what graphics adapter your system has.

---

### Post by Harry33 on 2011-02-23
> **poonforce said:**
> i installed natty narwhal but i have to run it in failsafe graphic mode every time, then only i can read my monitor. 

when i start it normally it boots up without any errors but after booting, my screen goes wierd, i just cant read and make out anything on the screen. 
when i install restricted driver, then even failsafe graphic mode doesnt run.
please help

Restricted drivers (nvidia-current and fglrx) do not work with the new xserver 1.10 development series (now rc2).
So are you using xserver-xorg-video-nouveau (nvidia card) or xserver-xorg-video-ati (amd/ati card)?

---

### Post by rburkartjo on 2011-02-24
yea harry nvidia is still toast

---

