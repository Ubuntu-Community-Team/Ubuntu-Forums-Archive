---
title: "Nvidia 8500GT, which driver?"
date: 2008-08-19
forum: Multimedia Software
---

### Post by rakan_dr on 2008-08-19
Hi guys,
I have nvidia 8500GT but i don't know what driver should i use for it.

Ubuntu installed one when i chose the Normal and Extra Visual Effects from Appearance, but it wasn't good.

Please help me and give me a name for a driver in the repos.

I have Ubuntu 8.04.1

Thnx

---

### Post by Loaded.len on 2008-08-19
I have an 8600 GTS and I use nvidia-glx-new

does that answer your question?

---

### Post by rakan_dr on 2008-08-19
I'll make a try and download it.
thnx.

---

### Post by nikobor on 2008-08-19
I also have nvidia 8500GT and I use nvidia-glx-new.

---

### Post by forger on 2008-08-19
Why not just go to System > Administration > Hardware drivers and allow Ubuntu to find the best driver? You check the "Enabled" checkbox

By the way, I heard the Nvidia 8xxx cards have some problems, is this your case?
If you want to use an updated driver ([COLOR="Red"]**could break stuff!**[/COLOR])m you might want to use envyng to download a newer version of the driver:
```
sudo apt-get install envyng-gtk
```
then menu Applications > System Tools > EnvyNG

---

### Post by rakan_dr on 2008-08-19
> **forger said:**
> Why not just go to System > Administration > Hardware drivers and allow Ubuntu to find the best driver? You check the "Enabled" checkbox

By the way, I heard the Nvidia 8xxx cards have some problems, is this your case?
If you want to use an updated driver ([COLOR="Red"]**could break stuff!**[/COLOR])m you might want to use envyng to download a newer version of the driver:
```
sudo apt-get install envyng-gtk
```
then menu Applications > System Tools > EnvyNG

I just did what u said "to use Hardware Drivers" but i feel that my windows "and 3D graphics in general" are heavy on the system.

---

### Post by rakan_dr on 2008-08-19
> **nikobor said:**
> I also have nvidia 8500GT and I use nvidia-glx-new.

hi man, 
do u have any problems with the driver??? Do u feel that the 3D graphics and windows are heavy???

By the way what's your card's vendor??
I have XFX.

---

### Post by rakan_dr on 2008-08-19
> **nikobor said:**
> I also have nvidia 8500GT and I use nvidia-glx-new.

What Ubuntu version do u have??
I have Ubuntu 8.04.1

---

### Post by nikobor on 2008-08-19
Me too. As for the heavy 3D graphics, I don't have such a problem. The only problem I have is that my refresh rate isn't detected correctly and I need to install nvidia-settings to edit the refresh rate because I don't like messing up with xorg. But this is a problem of monitor as ubuntu can't recognize it.

---

### Post by nikobor on 2008-08-19
Forgot to mention: Ubuntu 8.04.1, but 64bit AMD.

---

### Post by forger on 2008-08-19
> **nikobor said:**
> Me too. As for the heavy 3D graphics, I don't have such a problem. The only problem I have is that my refresh rate isn't detected correctly and I need to install nvidia-settings to edit the refresh rate because I don't like messing up with xorg. But this is a problem of monitor as ubuntu can't recognize it.

You have an LCD monitor?
1) Try a newer driver using envyng, it could fix things.
2) Use an adaptor (DVI to normal VGA output) to connect the LCD monitor with the graphics card.
If not, then you should report your brand and model of your monitor and your graphics card to nvidia. Send the info as an email with the nvidia-bug-report.log that the following command creates:
```
sudo nvidia-bug-report.sh
```
(the email is shown when you execute the command)

---

### Post by rakan_dr on 2008-08-19
I have a Samsung SyncMaster 920N LCD monitor with VGA connector (so i don't need a converter).

---

