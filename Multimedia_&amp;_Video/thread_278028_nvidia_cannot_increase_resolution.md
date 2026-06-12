---
title: "nvidia cannot increase resolution"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by sumithar on 2006-10-15
he lspci | grep VGA command returns
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
But I am not able to increase my resolution past 1024*768.

WHen I boot this same machine under XP (it is a dual boot box) I can increase it to 1280*1024. (I use it only to watch videos like on the mlb website- I can't use it day-to-day, it is only a 17" monitor!)

I tried to update drivers using automatix and it said the drivers are  already in place because I had followed the instructions 
on the ubuntuguide.org webpage " How to install Graphics Driver (NVIDIA)."

I have downloaded the latest NVIDIA-Linux-x86-1.0-8774-pkg1.run file from the website- I ran into some difficulties running this so I have held off.  Do I need to do this too?

Thanks

---

### Post by darsan on 2006-10-15
[http://ubuntuforums.org/showthread.php?t=269052&highlight=resolution](http://ubuntuforums.org/showthread.php?t=269052&highlight=resolution)

---

### Post by tseliot on 2006-10-15
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by sumithar on 2006-10-16
Thank you.  I was able to use 
sudo dpkg-reconfigure xserver-xorg
as suggested in that link and change it.

---

