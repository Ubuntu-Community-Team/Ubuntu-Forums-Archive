---
title: "Nvidia installtion...I'm stuck..please help"
date: 2006-03-10
forum: Multimedia &amp; Video
---

### Post by cabber on 2006-03-10
I'm installing the latest nvidia drivers and got lost.  I am using this guide via method 2:

[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers)

I downloaded the driver installer to my desktop and am stuck at this point:

```


Code:
cd “directory where you have the nvidia installer”
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
```

I'm not sure how to get to the directory where I have the installer (desktop?)

Thanks.

---

### Post by astyanax on 2006-03-10
Why are you using method 2?  The first method is so much easier.  Just do this:

```
sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf  
```


- Add Load “glx” to Module section
- Change the Driver “nv” value in the “Device” section to Driver “nvidia”

And that's really it.  Restart x and you should be using the nvidia drivers.

---

### Post by DavidW2 on 2006-03-10
[QUOTE=astyanax]Why are you using method 2?  The first method is so much easier.  Just do this:

```
sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf  
```


- Add Load “glx” to Module section
- Change the Driver “nv” value in the “Device” section to Driver “nvidia”

And that's really it.  Restart x and you should be using the nvidia drivers.[/QUOTE]

I also had to comment out:
> Load GLCore
Load dri



---

