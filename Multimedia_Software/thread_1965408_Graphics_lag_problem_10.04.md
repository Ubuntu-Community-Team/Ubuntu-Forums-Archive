---
title: "Graphics lag problem 10.04"
date: 2012-04-25
forum: Multimedia Software
---

### Post by leenfrewin on 2012-04-25
Hi.  I'm very new to Linux.  I just install Ubuntu 10.04 on my Lenovo v570 laptop.

Intel i5 2450M 2.5 GHz processor
6 GB Memory
Intel HD Graphics 3000

I installed Mupen64 to play some N64 games, but the graphics are constantly lagging, making it impossible to play.  Also, Cheese is having the same problem.  Videos through my web browser have been working perfectly.  I've been watching youtube with no problems.

Does anyone have any ideas?  I thought my hardware would be fine to run games like this, but maybe I'm wrong.  I can't seem to find any threads with this specific problem.

Any help is appreciated.

-kathleen

---

### Post by lovinglinux on 2012-04-25
I have a system similar to yours. The only difference is that my processor is i5-2410M.

I haven't tried to play games on Linux yet. However on Windows, it plays games like Portal 2 fine if I lower some settings.

---

### Post by BicyclerBoy on 2012-04-25
The stock 10.04 kernel & Xorg/intel drivers are way to out-of-date to run sandybridge CPU/GPU at any performance level. 

I would suggest you to upgrade, in one step, to 12.04 LTS when it hits shop floor.

If the prospect of unity put you off, consider installing gnome-fallback session. Not quite as good as gnome2 on 10.04.

To attempt to get HD300 graphics working with 10.04 would require serious updates to: kernel, Xorg, intel driver etc..

---

### Post by leenfrewin on 2012-04-27
Okay, thanks.  I don't have a problem with Unity, so I will definitely give 12.04 a shot.

---

### Post by MonkeyPaw on 2012-04-28
I would definitely agree there. New hardware will do better on newer versions of Ubuntu. I'm curious to see how your HD 3000 does on 12.04. I've been eyeing the i3 2125 for my machine to reduce power consumption.

---

### Post by leenfrewin on 2012-05-09
I've just upgraded to 12.04, and the graphics have been working fine for a week or so.  After installing some updates, I'm getting the same lag problem, though.  I don't know what to make of it.

---

