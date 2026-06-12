---
title: "ubuntu 10.04 nvidia Quadro4 750 XGL driver problem"
date: 2010-05-25
forum: Multimedia Software
---

### Post by Gmjunk1 on 2010-05-25
Hi. newbie here. 
I upgraded to ubuntu 10.04 via the system-->admin-->update manager. 
and am trying to install nvidia driver. I am having many problems and am stuck.

My video card:
# lspci | grep -i nvidia

01:00.0 VGA compatible controller: nVidia Corporation NV25GL [Quadro4 750 XGL] (rev a3)

I followed the great  instructions on this site: 

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

The nvidia driver i downloaded is: 
NVIDIA-Linux-x86-96.43.16-pkg1.run

After installing this according to the website instructions, 
The windowing system is very messed up and i can return "normalcy" by editing the /etc/X11/xorg.conf file and replacing nvidia with nv  as shown below:

Section "Device"
    Identifier     "Device0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
EndSection

What else do I need to do to get the Nvidia driver to work?  
Specific suggestions appreciated!
Thanks in advance. 
GM

Update:
I repeated the web instructions--again--and they seem to work for me now.  So this is SOLVED-THANKS

---

