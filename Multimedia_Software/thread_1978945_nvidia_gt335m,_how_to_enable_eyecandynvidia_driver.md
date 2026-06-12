---
title: "nvidia gt335m, how to enable eyecandy/nvidia driver?"
date: 2012-05-12
forum: Multimedia Software
---

### Post by tongjia19 on 2012-05-12
Hi all, I'm new to the forum, so if this is posted at the wrong place, sorry..


To start off, this is my setup:
 -- Ubuntu 12.04 32bit and Win7 64bit dual boot,  installed on different partitions.
 -- Asus k42jv/a42jv laptop, i5 processor,  4g ram, ...
 **
    -- Nvidia gt335m 1g graphics card, with the so called “Optimus” solution, which is having a dedicated nvidia card and an integrated intel card (which is sooooo useless and annoying).
 **
 

 I don't know how to state my problem fluently.. so let me just list everything in point form.
 

 -- So my ultimate goal is, to enable eyecandy: wobbly windows, 3D rotation, etc.  
 
-- I don't see "extra effects" under Appearance settings.

 -- I've tried using Compiz to do the setups, but nothing seems to happen after afterwards.
 

 -- I don't know if my nvidia card is used.
 

 -- Question 1:  Do I need to have the nvidia card used to have the eyecandy effecs?  
 

 -- I don't see anything in “Additional Drivers” after fresh installs. I used to see nvidia drivers with previous Ubuntu version installs.
 

 -- Question 2: Do I need properietary drivers for my nvidia card to enable eyecandy?  
 

 I've done research on the internet:
 -- followed tutorials on how to setup Compiz, nothing happens.

 -- followed various tutorials on how to install nvidia driver manually, things mess up..

    -- really low resolution after reboot, tried adding new resolution modes in xrandr, editing xorg.conf, nothing fixes the resoltution. 
    Reinstalled the system at least 5 times now due to this.
 
-- manually deleted all nvidia drivers installed, and can see drivers in the “Additional Drivers” (I think).   
 Installing from there results in the same resolution problem mentioned above.
 

 Guys, what else is there that I can do and try? I don't really want to use the nvidia card to play games or anything.. just want my wobbly wobbly windows..
 

 Thanks in advance.


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
FIX FOUND!!!!!!!!!!!!!!!!

The below seems to do the trick. Use Bumblebee for us dual graphics card users. Followed the instuctions, rebooted. Now drivers show up in the "Additional Drivers" thingy, and enabling wobbly windows is working after setting it up in Compiz.

I found it on another thread. Thanks to [jawilljr]("http://ubuntuforums.org/member.php?u=1006445") and all!

[http://ubuntuforums.org/showthread.php?t=1973025](http://ubuntuforums.org/showthread.php?t=1973025)

Have fun with Ubuntu!!
************************************************************************************************************

```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

```Don't know if it had any impact, but before installing bumblebee I removed NVIDIA stuff as well:

```

sudo apt-get purge nvidia*
sudo nvidia-uninstall

```************************************************************************************************************

---

### Post by tongjia19 on 2012-05-12
Look up.

---

### Post by jawilljr on 2012-05-12
[Install Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Instructions are in that link above.

Hope it helps.

Jerry

---

### Post by tongjia19 on 2012-05-12
> **jawilljr said:**
> [Install Bumblebee]("https://wiki.ubuntu.com/Bumblebee")
 
Instructions are in that link above.
 
Hope it helps.
 
Jerry
 
from my understanding, Bumblebee is for using the nvidia card when running specific programs that needs extra 3D power, such as graphic heavy games? Will it help me enable desktop effecs? I'll give it a try.. thanks

---

### Post by grahammechanical on 2012-05-12
I think that you misunderstand why Bumblebee is being developed. It is for set ups like this:

> Nvidia gt335m 1g graphics card, with the so called &#8220;Optimus&#8221; solution, which is having a dedicated nvidia card and an integrated intel card (which is sooooo useless and annoying).

You need a driver that can switch between the integrated Intel Graphic adapter and the Nvidia 1GB adapter as needed.

I do not know how far along the development of Bumblebee has got. 

Regards.

---

### Post by tongjia19 on 2012-05-12
..no one?

---

### Post by Mopar1973Man on 2012-05-12
Just got done do it on my own machine... Here is the article I used to enable the Compiz functions follow it and it will work for Ubuntu 11.10 so I'm not sure if anything has changed on the 12.04???

[http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-11.10-oneiric-ocelot](http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-11.10-oneiric-ocelot)

---

### Post by jawilljr on 2012-05-12
Your question was [already answered](http://ubuntuforums.org/showthread.php?t=1978945)


Please respond to the original thread.

Jerry

---

### Post by overdrank on 2012-05-12
Hi and welcome, please do not create multiple threads on the same issue. Threads merged and moved to Multimedia & Video

---

### Post by tongjia19 on 2012-05-15
:lolflag:

---

