---
title: "nvidia driver problem"
date: 2010-08-19
forum: Multimedia Software
---

### Post by kaustubh14 on 2010-08-19
i have nvidia 8400gs. After fresh install my splash screen is at good resolution but after installing nvidia drivers i got resolution issue at splash screen. and when playing hd files in movie player i.e. totem i get slow frames. and in mplayer i got this error "could not open directshow codec wmvdmod.dll" but file plays in bad quality than windows. any solution for that plz help. and sorry for bad eng

---

### Post by lukeiamyourfather on 2010-08-19
Then remove the nVidia driver, doesn't seem to be doing you any good.

---

### Post by kaustubh14 on 2010-08-19
i can uninstall nvidia driver but i cannot enable previous nouveau driver.

---

### Post by realzippy on 2010-08-19
Have a look at this ppa:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by lukeiamyourfather on 2010-08-19
> **kaustubh14 said:**
> i can uninstall nvidia driver but i cannot enable previous nouveau driver.

Install the package for it again and it should configure itself. Someone please correct me if that's not the case with that driver.

---

### Post by BinoPanda on 2010-08-19
I used a tool called Envy when I had Nvidia problems, I don't know if it will help but here is a link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by kaustubh14 on 2010-08-19
> **lukeiamyourfather said:**
> Install the package for it again and it should configure itself. Someone please correct me if that's not the case with that driver.
i have installed nvidia's latest driver for linux i.e. version 256. everything is fine but resolution of splash screen is low 800X600 how can i change it to 1024X768 or better.
and in mplayer i got this error "could not open directshow codec wmvdmod.dll" but file plays

---

### Post by tjones00 on 2010-08-19
To fix the splash resolution with nvidia proprietary drivers open a terminal

Backup your grub settings

```
sudo cp /etc/default/grub ~/grub-backup
```Change the settings

```
sudo gedit /etc/default/grub
```find the line

GRUB_CMDLINE_LINUX_DEFAULT=

change it to the following with your preferred resolution in my case 1920x1200

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap"

save/close the file and update grub
```

sudo update-grub
```
If that didn't work to revert back to your original settings

```
sudo rm /etc/default/grub
sudo cp ~/grub-backup /etc/default/grub
sudo update-grub
```

---

### Post by kaustubh14 on 2010-08-19
again failure i didn't get the fine resolution i installed xdriinfo. But when i launch the program it will give me error like "XDriInfo returned with non-zero exit. any suggestion for that.

---

### Post by Linuxforall on 2010-08-20
Update nvidia to latest from Ubuntu's own ppa for x at [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by kaustubh14 on 2010-08-20
i have uninstalled nvidia drivers then removed blacklisting of x.org nouveau driver.
Then i switch to default conf when i got error when logging saying that x server could not start. Module not found "nvidia".
After rebooting i got my splash screen at previous resolution i.e.1024X768 but when i installed new 256 driver then it again chages to 800X600.
Problem not solved.

---

### Post by kaustubh14 on 2010-08-21
Still does not solve my problem. Thanks for ur support.

---

### Post by goldenbrown on 2010-08-21
> **kaustubh14 said:**
> i can uninstall nvidia driver but i cannot enable previous nouveau driver.

Install gdm

Press Ctrl+alt+f2

This open command promp

Type 
sudo apt-get stop gdm

Then type
sudo apt-get remove nvidia*

That remove all nvidia drivers

Install only nvidia driver you need

Type 
sudo apt-get install nvidia_185*

Press enter

Restart gdm 
Type
sudo apt-get start gdm 

It work for me

---

### Post by kaustubh14 on 2010-08-22
when i am going to install nvidia drivers downloaded form nvidia, installer gave me error"The distribution_provided pre-install scrip failed Continue install or not? 
if i said yes then it will install but i get low resolution on splash but from login window it works fine
Plz guys anybody can give me solution for that.

---

### Post by kaustubh14 on 2010-08-22
This is the log file created by nvidia installer.

---

