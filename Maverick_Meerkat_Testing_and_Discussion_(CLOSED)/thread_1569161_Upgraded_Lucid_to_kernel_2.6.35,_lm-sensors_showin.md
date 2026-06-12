---
title: "Upgraded Lucid to kernel 2.6.35, lm-sensors showing high CPU temps"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by empty_spaces on 2010-09-06
I upgraded my Lucid install to the 2.6.35 kernel using the following commands to add the kernel PPA and update.

```
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-19-generic linux-image-2.6.35-19-generic
```

Now lm-sensors is reporting CPU temps around 15 deg C higher than 2.6.32. (i.e. around 62C compared to 47C)
The reason I doubted lm-sensors was because the laptop did not really feel any hotter than before.

Apparently, this is a bug affecting some users because of the way lm-sensors reports CPU temps with 2.6.35. The TJunction value is being reported as 100C for 2.6.35 as compared to 85C for 2.6.32.
See this thread:
[https://bbs.archlinux.org/viewtopic.php?id=103118&p=2](https://bbs.archlinux.org/viewtopic.php?id=103118&p=2)

I'm also seeing the same behavior with the Maverick Beta install since it uses 2.6.35 too.

So, anybody else here seeing the 15C rise for 2.6.35? Any solutions or corrections?

---

### Post by mc.god on 2010-09-06
Hi, I've got exactly the same behaviour upgrading Lucid 64 to kernel 2.6.35-19-generic AMD64.

On my Acer notebook, lm-sensor recognizes 4 sensors, 2  "virtual" and 2 on ISA bus. While the 2 "virtual" sensors retrun the same temp as under 2.6.32 (and exactly the same temp reported by the acpi bus), the ISA sensors have increased about 15° and report 61-62° in idle status.

Here the result of launching sensors copmmand:
[[IMG]http://a.imageshack.us/img163/9901/sensorsp.th.png[/IMG]](http://img163.imageshack.us/i/sensorsp.png/)

If I boot the notebook with the old 2.6.32-24 kernel, the 4 sensors report very close temps, and this 15° rise disappears.

---

### Post by empty_spaces on 2010-09-07
> **mc.god said:**
> Hi, I've got exactly the same behaviour upgrading Lucid 64 to kernel 2.6.35-19-generic AMD64.

On my Acer notebook, lm-sensor recognizes 4 sensors, 2  "virtual" and 2 on ISA bus. While the 2 "virtual" sensors retrun the same temp as under 2.6.32 (and exactly the same temp reported by the acpi bus), the ISA sensors have increased about 15° and report 61-62° in idle status.

Here the result of launching sensors copmmand:
[[IMG]http://a.imageshack.us/img163/9901/sensorsp.th.png[/IMG]](http://img163.imageshack.us/i/sensorsp.png/)

If I boot the notebook with the old 2.6.32-24 kernel, the 4 sensors report very close temps, and this 15° rise disappears.


That definitely looks like the same issue. I guess it doesn't hurt anything since we know that lm-sensors is reporting the wrong values, but I would feel much better if this could be resolved.
Not sure if it's the kernel or lm-sensors that's at fault here.

---

### Post by mc.god on 2010-09-08
Yes, I'm not really concerned by that, but hope it can be solved.
lm-sensors work fine under 2.6.32, so it could be a bit incompatible with new kernel, maybe a future update of lm-sensors will work fine with 2.6.35.

Bye

---

### Post by cariboo on 2010-09-08
The kernel was updated to 2.6.35-20 yesterday, do you still have the same problem?

---

### Post by cloyd on 2010-09-08
I was having trouble with high temps with Lucid. Tried different kernels. The 2.6.35 worked passable well as far as temp goes (just passable). Wireless internet in marginal situations was not good. The new 2.6.34-24 is the best I've seen. It runs cooler than the others on my machine, and wireless works well with a weak signal.  

I started using Ubuntu wiht 9.10. No temp issues there. I started having temp issues with Lucid, but managed to get temps back down in 50 C's with the right kernels. What you are telling me tells me I don't want to upgrade to Maverick in too much of a hurry. It appears that the developers are developing toward desktop machines rather than lap tops with their cooling issues. (Really, I don't know this . . . too much of a newbe, but I've learned laptops and netbooks face temp issues that desktops don't. 

It is interesting . . . . When I used windows, I didn't worry about temps much. I've learned a bit since thenb.

---

### Post by empty_spaces on 2010-09-08
Not sure why this was moved to "Maverick Meerkat Testing and Discussion", unless the people here might have a better handle on issues with the 2.6.35 kernel.

I'm having this issue on _Lucid_ with the 2.6.35-19 kernel, which I installed using kernel-ppa.
I just did a refresh in update manager and I'm not seeing the 2.6.35-20 kernel yet.

---

### Post by ranch hand on 2010-09-09
This forum is in the development part of the forums.  2.6.35 is the kernel for 10.10.

I would get the -20 version and try it.

---

### Post by VinDSL on 2010-09-09
> **empty_spaces said:**
> So, anybody else here seeing the 15C rise for 2.6.35?Not me, but...

Thanks, for reminding me to install 'sensors-applet'...  :D

I've meant to do this, every morning, for the past 2 weeks.

Anyway, all of my readings in 10.10 (2.6.35-20) are consistent with the temps reported in 10.04 (2.6.32-24).

Here's a screenie, showing my temps (in sizzling Arizona)...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=168923&d=1284011466[/IMG]

---

### Post by recluce on 2010-09-09
I guess you guys need to compare more hardware details (chipset and so), I am running 2.6.35-20 (and until today 2.6.35-19) on Lucid and Maverick - and the sensors show completely normal values (idle CPU and chipset at 40°C, GPU (with lots of Compi stuff) 47°C.

So I'll make a start: Dell Latitude D830 (Intel Mobile 965GM Express Chipset Motherboard) with nvidia Quadro NVS 140 graphics. Ubuntu 10.04.1 and 10.10beta (AMD64 versions).

---

### Post by VinDSL on 2010-09-09
> **recluce said:**
> I guess you guys need to compare more hardware details[...]

So I'll make a start: Dell Latitude D830 (Intel Mobile 965GM Express Chipset Motherboard) with nvidia Quadro NVS 140 graphics. Ubuntu 10.04.1 and 10.10beta (AMD64 versions).Well, if you think it will help...

I'm running:

[LIST]
[*]DFI LanParty Pro875B mobo
[*]XFX GeForce 7600 GT video card
[*]Intel P4EE Gallatin CPU @ 3.4GHz
[*]Intel 875P chipset
[*]Tuniq Tower 120 cooler
[*]Ubu 10.04.1 and 10.10
[/LIST]

Here's a purdy pic (black PCB rawks!)...

[INDENT][IMG]http://ubuntuforums.org/attachment.php?attachmentid=168934&d=1284018497[/IMG][/INDENT]

---

### Post by dino99 on 2010-09-09
hi guys,

dont pay to much attention on sensors values, we all know that dont reflect the real temp anyway. We need to wait for 2.6.36 kernel which might work far better with sensors, so patience ):P

---

