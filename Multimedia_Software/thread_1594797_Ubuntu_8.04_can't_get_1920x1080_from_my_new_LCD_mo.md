---
title: "Ubuntu 8.04 can't get 1920x1080 from my new LCD monitor"
date: 2010-10-12
forum: Multimedia Software
---

### Post by xp_newbie on 2010-10-12
I finally decided to replace my monitor. I got a HANNspree HF225 with a native resolution of 1920x1080.

Alas, my Ubuntu 8.04 only allows me to select the 1400x1050 (50Hz) as the highest resolution.

I tried using **gksudo displayconfig-gtk**, to no avail. (yes, I also tried selecting Generic LCD display 1920x1080).

The strange thing is the monitor itself (via its OSD information) says it is running 1680x1050 (at H: 65.6KHz V: 60.3Hz).

Clearly, Ubuntu 8.04 can't see the real hardware capabilities of my system. My graphics card is "nVidia Corporation NV44 [**GeForce 6200 LE**] (rev a1)". I know it is capable of delivering the 1920x1680 because it has been previously driving 1920x1600 on a DELL P1110.


Any idea how to get 1920x1080 on my system?

Thanks

---

### Post by wkulecz on 2010-10-12
Are you using DVI or analog cable?  If you are using DVI, thy switching to analog as there are bugs in the resolution detection when using DVI.  I've got a Sony 1920x1200 LCD that only works as 1600x1200 uisng DVI.  Get the full 1920x1200 automatically with the analog input.  

DVI appears a total rip-off to me, no visible image improvement, much more expensive cables, and bugs that make it not work right.

---

### Post by xp_newbie on 2010-10-12
> **wkulecz said:**
> Are you using DVI or analog cable?
Of course I am using analog VGA. :)

Any idea how I go from here?

---

### Post by AJayDuhh on 2010-10-12
> **xp_newbie said:**
> I finally decided to replace my monitor. I got a HANNspree HF225 with a native resolution of 1920x1080.

Alas, my Ubuntu 8.04 only allows me to select the 1400x1050 (50Hz) as the highest resolution.

I tried using **gksudo displayconfig-gtk**, to no avail. (yes, I also tried selecting Generic LCD display 1920x1080).

The strange thing is the monitor itself (via its OSD information) says it is running 1680x1050 (at H: 65.6KHz V: 60.3Hz).

Clearly, Ubuntu 8.04 can't see the real hardware capabilities of my system. My graphics card is "nVidia Corporation NV44 [**GeForce 6200 LE**] (rev a1)". I know it is capable of delivering the 1920x1680 because it has been previously driving 1920x1600 on a DELL P1110.


Any idea how to get 1920x1080 on my system?

Thanks

> **wkulecz said:**
> Are you using DVI or analog cable?  If you are using DVI, thy switching to analog as there are bugs in the resolution detection when using DVI.  I've got a Sony 1920x1200 LCD that only works as 1600x1200 uisng DVI.  Get the full 1920x1200 automatically with the analog input.  

DVI appears a total rip-off to me, no visible image improvement, much more expensive cables, and bugs that make it not work right.

I CAN see a noticeable improvement in the screen. DVI has way better quality. Also, DVI cables are only a few bucks more expensive these days.

At the topic starter, have you tried Nvidia's drivers?

---

### Post by xp_newbie on 2010-10-12
> **AJayDuhh said:**
> At the topic starter, have you tried Nvidia's drivers?
Yes, I have been using proprietary NVIDIA accelerated graphic driver (instead of the Ubuntu open source ones) for over 2 years now.

I found the following article:

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

Which is a very nice troubleshooting tutorial, using **xrandr**. Alas, although I managed to add 1920x1080 to the Screen Resolution menu (via cvt and xrandr commands), selecting 1920x1080 from that menu yields no change in resolution.

I think this is because xrandr is really for I[ntel and Radeon]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Output_port_names") drivers, not for Nvidia.

Any idea how I go from here?

---

### Post by AJayDuhh on 2010-10-12
I'm not sure whether you tried forcing it using xrandr.

What happens if you run this?

```

xrandr -s 1920x1080

```

---

### Post by xp_newbie on 2010-10-12
> **AJayDuhh said:**
> I'm not sure whether you tried forcing it using xrandr.
Yes, I tried forcing it using xrandr. It did nothing.

Any idea how to proceed?

---

### Post by cchhrriiss121212 on 2010-10-12
Have you had a look at nvidia-settings?

---

### Post by xp_newbie on 2010-10-12
> **cchhrriiss121212 said:**
> Have you had a look at nvidia-settings?
I don't have any 'nvidia-settings' file on my system, but I do have 'nvidia-xconfig' and I just happened to solve the problem myself. Here is how:

```
sudo -i
nvidia-xconfig
```

Unfortunately, this by itself didn't help, as I was still unable to select 1920x1080 from displayconfig-gtk.

So edited /etc/X11/xorg.conf by hand, and modified the Virtual line under Section "Screen", SubSection "Display" to:
```
       Virtual     1920 1080	  # was 1400 1050 before

```

Problem solved!
OMG it's beautiful! :):):)

Am I good or am I good? :guitar:

---

