---
title: "HP Dv6 no sound"
date: 2009-09-24
forum: Multimedia Software
---

### Post by Ozzee on 2009-09-24
Hi,

I'm trying to fix an HP DV6 laptop that has no sound after a new 9.04 installation.

I've been trying upgrading alsa to 1.0.20 and configuring the alsa-base.conf file, but apparently I haven't done it right or the problem is somewhere else. Has anyone got it working with these specs?

Codec: IDT 92HD75B3X5
Laptop: Hp Dv6 1220so

Any suggestions or help in this matter would be greatly appreciated :)

---

### Post by hosein-mec2 on 2009-09-26
follow [this solution]("http://unixwars.com/2009/07/29/ubuntu-9-04-problems-jaunty-fixes-for-hp-dv6-1120es/?wscr=1680x1050") ...

---

### Post by Ozzee on 2009-09-27
I got it working with this fix when i reinstalled and updted and then did the steps described:
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/80818](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/80818)

---

### Post by Neezer on 2009-10-22
> **hosein-mec2 said:**
> follow [this solution]("http://unixwars.com/2009/07/29/ubuntu-9-04-problems-jaunty-fixes-for-hp-dv6-1120es/?wscr=1680x1050") ...

Fantastic!!! Just did it and am listening to music right now!!!

Thank You.

---

### Post by Neezer on 2009-10-23
So I updated my system, and upon reboot, my GRUB had another kernel in it. I started the newest kernel and had no sound again. I then went through the process again of getting sound back, and it is working again....kind of annoying though.

---

