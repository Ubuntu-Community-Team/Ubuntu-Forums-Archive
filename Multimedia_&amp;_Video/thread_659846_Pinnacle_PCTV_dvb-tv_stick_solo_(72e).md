---
title: "Pinnacle PCTV dvb-tv stick solo (72e)"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by michelev on 2008-01-06
Hi,
I have a USB PCTV
I have tried this procedure to install the device [http://wiki.ubuntu-it.org/Pinnacle](http://wiki.ubuntu-it.org/Pinnacle) but some problem occurred.

~$ sudo modprobe em28xx
~$ sudo modprobe em28xx-audio
FATAL: Module em28xx_audio not found.
~$ sudo modprobe em28xx-dvb
FATAL: Module em28xx_dvb not found.

I have tried to download and install differents firmware but the problem occurred again
Any suggestion?
TNX to all the "ubunters" 
michelev

PS: OS Gutsy

---

### Post by michelev on 2008-01-08
no one?
](*,)

---

### Post by Del Gro Badeu on 2008-01-12
Hi, 

Michelev; know that's ok for you, cause you have posted on french ubuntu forums, 
so, the other can try it, it's perfectly working on my computer. It's in french, but easy to understand :

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1452346#p1452346](http://forum.ubuntu-fr.org/viewtopic.php?pid=1452346#p1452346)

(And, as usual, sorry for my poor english)

---

### Post by dabigjones on 2008-05-27
Hey there,
First of all i'm German. So please excuse my bad knowledge of english.
If you use the 2.6.24.14 version of kernel you can make this device Work by doing the following things.
First you need at least one of these pakeges (i'm not sure wich one).
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh 
next steps are:
> wget [http://www.barbak.org/v4l_for_72e_dongle.tar.bz2](http://www.barbak.org/v4l_for_72e_dongle.tar.bz2)
tar xvjf v4l_for_72e_dongle.tar.bz2
cd v4l-dvb
sudo cp firmware/dvb-usb-dib0700-1.10.fw /lib/firmware/
make all
sudo make install
sudo reboot

After the reboot you can plug in the device and use it with kaffeeine

---

### Post by zujik on 2008-06-09
I got it working like above but just before 'make all' (after the cp to the /lib/firmware folder) I also had to cp to my /lib/firmware/<kernel name folder>.

After that I then used make distclean to allow it to work on my 2.6.24-16 kernel and it worked fine after following the rest of the above instructions.

---

### Post by michelev on 2008-07-08
Incredible!
pinnacle stick solo now works!
I have just copied the firmware.
tnx all
michelev

---

### Post by x2l2 on 2008-07-22
im trying whit this
[http://martinpitt.wordpress.com/2008/06/10/packaged-dvb-t-drivers-for-ubuntu-804/](http://martinpitt.wordpress.com/2008/06/10/packaged-dvb-t-drivers-for-ubuntu-804/)

looks like more easy solution...

---

