---
title: "Video playback color"
date: 2013-02-25
forum: Multimedia Software
---

### Post by 1kevin662 on 2013-02-25
Video playback color is not right and video looks faster than it should be. this on all local playback. Youtube is fine but my camcorder videos and dvd movies do not look right. I have an intel 855 gm chip-set.

---

### Post by 1kevin662 on 2013-02-26
I may just load 10.4 back on and see how it works

---

### Post by sudodus on 2013-02-26
I think that Ubuntu with Unity needs more horsepower (CPU) and memory (RAM) to work well. So try a desktop environment with a lighter foot-print on that computer.

- Xubuntu 12.04 LTS with the light XFCE or
- Lubuntu 12.10 with the ultra-light LXDE

Iso files with these Ubuntu flavours can be downloaded and tested when you boot from the CD or USB drive. It is important to test them before deciding to install.

---

### Post by 1kevin662 on 2013-02-26
Which is better for trimming and adding music to home videos....

---

### Post by uc50_ic4more on 2013-02-26
> **1kevin662 said:**
> Which is better for trimming and adding music to home videos....

You could (and should) try PiTiVi, Openshot, Avidemux and Kdenlive. Download and install 'em all through the Software Centre and crack them open to see which one you prefer!

---

### Post by sudodus on 2013-02-26
> **1kevin662 said:**
> Which is better for trimming and adding music to home videos....
***Lubuntu*** will be the fastest. ***Ubuntu studio*** is a good alternative for music and video editing. A lot of software comes with the installation.

---

### Post by 1kevin662 on 2013-02-26
thanks guys I guess I was not clear which one will be better for trimming video and adding music between 

Xubuntu 12.04 LTS with the light XFCE  and
- Lubuntu 12.10 with the ultra-light LXDE

---

### Post by sudodus on 2013-02-26
> **1kevin662 said:**
> thanks guys I guess I was not clear which one will be better for trimming video and adding music between 

Xubuntu 12.04 LTS with the light XFCE  and
- Lubuntu 12.10 with the ultra-light LXDE

It depends what you need and what you like. Maybe both work well, maybe one of them has problems with some part of the hardware. So I suggest that you try both, and find out. Try them live without installing anything and do different things to find out which of them performs better.

---

### Post by uc50_ic4more on 2013-02-26
> **1kevin662 said:**
> thanks guys I guess I was not clear which one will be better for trimming video and adding music between 

Xubuntu 12.04 LTS with the light XFCE  and
- Lubuntu 12.10 with the ultra-light LXDE

Neither of these Desktop Environments installs, by default, an audio or video editing application. Both XFCE and LXDE use the GTK toolkit for applications, and therefore using a GTK-based application might be the smartest option. PiTiVi, Openshot and Avidemux might be your best bets and are easily installed through the Software Centre.

---

### Post by 1kevin662 on 2013-02-26
I understand i will have to have an application to edit video but the playback on 12.04 is the problem. the color is so bad I can not watch it... and it is running a little fast.. I cannot install or run  lubuntu because of my old processor.. I had to upgrade from 10.04 to get 12.04 on my laptop.

---

### Post by sudodus on 2013-02-27
> **1kevin662 said:**
> I understand i will have to have an application to edit video but the playback on 12.04 is the problem. the color is so bad I can not watch it... and it is running a little fast.. I cannot install or run  lubuntu because of my old processor.. I had to upgrade from 10.04 to get 12.04 on my laptop.
Then I suggest that you check if you have pae. This command should print at least one line with pae, if the CPU has that feature
```
gksudo lshw|grep --color pae
```
If not, you cannot use Lubuntu 12.10, but Lubuntu 12.04 and Xubuntu 12.04 LTS have non-pae kernels, so they should work. Unfortunately Lubuntu 12.04 is only supported until October 2013.

However, there is a work-around, that you might want to try, if you have a Pentium M CPU. See this link.

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2113826[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2113826")

---

