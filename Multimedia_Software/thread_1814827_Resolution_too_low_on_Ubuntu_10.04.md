---
title: "Resolution too low on Ubuntu 10.04"
date: 2011-07-30
forum: Multimedia Software
---

### Post by shortpplerule on 2011-07-30
Hi I was wondering if anyone could help me out with a resolution problem.

I recently installed (dual booting) Ubuntu 10.04 on a Samsung QX411-W01 running Windows 7.  It's a system with with two graphics drivers (Intel HD 3000 and NVIDIA GeForce® GT 525M, 1GB).

Right now when I try to change the monitor settings, Ubuntu doesn't seem to detect my proper capabilities (currently only allowing 1024x768 when Windows 7 is as good as 1366x768. )

I don't really know how to go about fixing this issue.  I've tried reading through the forums, but I'm not finding any solutions.

Also I am unable to turn on any form of desktop effects.  It seems the issue is with the driver, but if anyone can give me further help and instruction on how to remedy this annoyance, I'd greatly appreciate it!

---

### Post by JsinLegacy on 2011-08-03
> **shortpplerule said:**
> Hi I was wondering if anyone could help me out with a resolution problem.

I recently installed (dual booting) Ubuntu 10.04 on a Samsung QX411-W01 running Windows 7.  It's a system with with two graphics drivers (Intel HD 3000 and NVIDIA GeForce® GT 525M, 1GB).

Right now when I try to change the monitor settings, Ubuntu doesn't seem to detect my proper capabilities (currently only allowing 1024x768 when Windows 7 is as good as 1366x768. )

I don't really know how to go about fixing this issue.  I've tried reading through the forums, but I'm not finding any solutions.

Also I am unable to turn on any form of desktop effects.  It seems the issue is with the driver, but if anyone can give me further help and instruction on how to remedy this annoyance, I'd greatly appreciate it!

you care to share how you got it to install on this laptop... I have been trying for a few days but have nothing but failure..

---

### Post by Furball588 on 2011-08-03
erk...sandy bridge and optimus.

I guess to answer your question, you need the 3D acceleration going and to do that, you probably need to disable optimus (and just not use one of those video processors)

---

### Post by shortpplerule on 2011-08-07
> **JsinLegacy said:**
> you care to share how you got it to install on this laptop... I have been trying for a few days but have nothing but failure..

So I installed ubuntu 10.04 using a USB stick.  When the system restarts, press the F2 button to get into the BIOS settings and change the boot options so that you boot from the USB drive first.  Save the settings and restart so you the laptop reboots from the iso image on the USB and install following the instructions.




I never got the resolution fixed in ubuntu 10.04 but I upgraded to Ubuntu 10.10 and it corrected everything.  I guess ubuntu 10.04 just doesn't have the capabilities to detect the hardware for 3D acceleration?

---

### Post by .... on 2011-08-07
It sounds like you're using the sandy bridge integrated intel video and the Lucid kernel is just too old to do mode-setting properly (and mesa too old for 3D) on those chips.

---

### Post by lordlynxwolf on 2011-08-24
Hi, i also can't install ubuntu 11.04 on this laptop. I get a black screen after the grub install screen when selecting to try it out or install it. I have tried various options by editing the boot string,like nomodeset or acpi=off but no cigar. Any sugestions or as anybody found the way to install it please reply, i'm getting frustrated here.

PS: sorry for the bad english

---

### Post by chops23 on 2011-08-24
I also have problem with QX411.

I tried booting the latest Ubuntu then Mint on my QX411 and it would not boot from disc, but it does boot from USB. When booted from USB after selecting install Mint screen stayed blank/ black.

I also tried the same thing with Backtrack 5. Same thing happened.

I called Samsung tech support.

Support unable to solve problem. They said they will call me back within 48 hours and advance tech support will try solve problem.

I will post if I get a solution if you haven't received one yet.

---

### Post by shortpplerule on 2011-09-03
hmmm... I've been thinking about installing Mint on my QX411-W01 (dual booting with Ubuntu 11.04 that I currently have installed), but I understand what you mean.  I only managed to install Ubuntu 11.04 on it by using a USB stick because I couldn't do it with a boot disc.  

I have yet to try installing Mint, so I can't offer you any feedback yet but if you happen to find a solution to your problem please post.  I will post any updates when I do try installing it.

---

