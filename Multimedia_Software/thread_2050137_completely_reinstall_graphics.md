---
title: "completely reinstall graphics"
date: 2012-08-30
forum: Multimedia Software
---

### Post by nikio on 2012-08-30
After installing Nvidia drivers ubuntu started to boot with unity 2D,
after (installing, uninstalling, reconfiguring)*(mesa,vesa,nouveau,nvidia) several times I ended up with a lower unchangeable resolution (1024x768 ) instead of (1366 x 768 ), unity is still 2D and now other monitors are not detected... ](*,)

I've tried
```
sudo apt-get remove --purge xserver-org [COLOR="Red"]WRONG!![/COLOR]

```
```

sudo apt-get remove --purge xserver-[COLOR="Red"]x[/COLOR]org
```
but:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xserver-org

```

I wouldn't like to reinstall all the system because reinstalling all the software would take me a whole day...

The question is:
is there a way to radically purge and reinstall all and only graphics related stuff?

---

### Post by jonnyboysmithy on 2012-08-30
Try synaptic package manager, it can be found in the ubuntu software centre.
Use that to look for the packages you are after. Its a very useful tool. Using that you can easily find packages and purge/reinstall them.
I'm not to sure but I don't think you want more than one driver installed at a time. Make sure the driver gets applied properly. You may need to restart.
Hope that helps :)

---

### Post by nikio on 2012-08-30
I do have Synaptic, but if apt-get doesn't find xorg, I doubt Synaptic will,
furthrmore, once I've uninstalled graphics, I will be able to work only through text terminal...

by the way... with synaptics I've seen that there are loads of drivers related to hardware I don't have (ATI for example), is that normal?

---

### Post by jonnyboysmithy on 2012-08-30
I believe ubuntu ships with a lot of generic drivers. If you don't have an ATI graphics card then I don't think you should have an ATI driver installed.
I'm not very knowledgeable, perhaps someone would like to fill in a bit here?
Synaptic package manager is a front-end for apt-get (gui: Graphical User Interface).
Reinstalling might be the easiest way to go..
I think you can remove a driver, install a different one and reboot and the new one should work.

Heres some guides that might help:
[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)
[http://www.omgubuntu.co.uk/2010/02/how-to-install-nvidia-drivers-manually-in-ubuntu/](http://www.omgubuntu.co.uk/2010/02/how-to-install-nvidia-drivers-manually-in-ubuntu/)

---

### Post by nikio on 2012-08-30
thank you, I managed to spot my mistake,
I got back my resolution and my other monitor...
still unity2D... but work-able
):P

---

### Post by nativehound on 2012-08-30
First thing do is get xorg back and then edit /etc/X11/xorg.conf. add "1366 x 768" to screen section and "nvidia" to device driver section
if it's not already there.

```
sudo aptitude install xserver-xorg-video-nvidia
```

---

### Post by nikio on 2012-08-30
Everything started because of Nvidia's driver:
Xlib:  extension "NV-GLX" missing on display ":0"
God knows what is wrong now
I tried to compile Mesa 8.0.4 and something went wrong there too... 
I'll stick with this solution until 12.10 is out

---

