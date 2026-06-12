---
title: "ATI drivers for a EAH2400PRO"
date: 2008-05-11
forum: Multimedia Software
---

### Post by FoX_HunteR on 2008-05-11
well i tried just unlocking the ones on ubuntu(hardy) but no good,
it just switched my monitor off after it finished booting,
then i tried the official ones from ATI, but no luck, they wont even install,
and i just tried EnvyNG but again, no good, does the same as the first option...

does anyone know what i can do? im a fresh use to linux all together, being a windows user all my life im used to just have the software supplied with the hardware...

any ideas?

when the monitor goes black, it still plays the sound of the login screen, so i know its all working apart from the video card?

---

### Post by Yellow Pasque on 2008-05-11
Your card is PCI-e16, not AGP, correct?

Press Ctrl+Alt+F1, and that should bring you to the terminal where you can install the radeonhd driver.

Use the two commands below and choosed radeonhd as your video driver. This should get your GUI working again after you restart, and then we can work on installing the Catlyst drivers if you want 3D accel and/or desktop effects.
```
sudo apt-get install xserver-xorg-video-radeonhd
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by FoX_HunteR on 2008-05-11
ok cheers, ill take a look at that now, so your saying after i enable the drivers and the screen goes black or before-hand?

and yes, PCIe is correct.

---

### Post by Yellow Pasque on 2008-05-11
Let the system boot. When it's finished its flurry of disk activity and loaded all of your startup programs/daemons, then press Ctrl+Alt+F1

---

### Post by FoX_HunteR on 2008-05-11
ok, so now i have my gui back,
how do i go about getting drivers that work/to work?

---

### Post by Yellow Pasque on 2008-05-11
Open a terminal.
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv
```
Now restart. If you get a black screen again, redo the radeonhd commands, restart and let me know. We'll take a look at your xorg.conf file then.

---

### Post by FoX_HunteR on 2008-05-11
im about to restart now, but heres what i got:

```
brett@da-beast-duo:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for brett: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brett@da-beast-duo:~$ sudo aticonfig --initial -f --overlay-type=Xv
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Uninitialised file found, configuring.
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Segmentation fault

```

---

### Post by FoX_HunteR on 2008-05-12
well it didn't make it black, it flickered a fair bit while logging on, but otherwise, everything is the same.

---

### Post by Yellow Pasque on 2008-05-12
Great, now let's make sure it's installed correctly:
```
fglrxinfo
```

---

### Post by FoX_HunteR on 2008-05-12
```
brett@da-beast-duo:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```

---

### Post by FoX_HunteR on 2008-05-12
i know nothing is working yet drivers wise as all the 3D programs have massively low FPS.
which driver are we attempting to use by doing this?

---

### Post by FoX_HunteR on 2008-05-12
well i decided to try other drivers and tried the ones from the ATI site, the official ones,
after 3 hours i finally got them to install, but no good,
black screen again!
it plays the login screen sound but by then the screen is already black...

this is starting to annoy me, everything else worked off the bat,
i was convinced my wireless was what was going to be painful, but it was the easiest by far!

any ideas????

---

### Post by FoX_HunteR on 2008-05-13
i know i probably shouldn't keep bugging for help,
but i REALLY need help with this!
i cant get it to work no matter what i do!

---

### Post by FoX_HunteR on 2008-05-14
delete this thread please, im just going to format

---

