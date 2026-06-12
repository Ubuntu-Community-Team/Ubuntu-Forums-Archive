---
title: "Web Cam Z-Star ZS0211-LF"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by Andrelz on 2008-04-14
Hi People, 

I'm trying to install a web Cam Z-star ZS0211-LF.
I downloaded the driver from [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz). I installed the driver correctly following the steps from the site but, when finish the installation the web cam doesn't work!!!
I tried to open the camorama appear the message below!

[IMG]http://img120.imageshack.us/img120/6445/screenshoterrorcamoramata8.png[/IMG]

The devide /dev/video* isn't created when I plug the cam in the USB!!
Ow, I'm using Ubuntu 7.10, I tried with the 7.04 version and doesn't work too!!

What Can I do to solve this problem??
Anybody knows??


Thanks!!

André Luiz

---

### Post by linuxwizard on 2008-04-14
Did you reboot your computer after installing the driver ? Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)
 
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by Andrelz on 2008-04-14
I already did it, and doesn't work again!!

Anything else??

---

### Post by linuxwizard on 2008-04-14
Are you sure you are using correct driver ? Post results > lsusb

---

### Post by Andrelz on 2008-04-14
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0ac8:307b Z-Star Microelectronics Corp. 
Bus 002 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-04-14
OK That is the correct driver. Did you load the driver ? sudo modprobe gspca


[http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/](http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/)

---

### Post by Andrelz on 2008-04-15
:( The same error!!!
Any Suggestion??

---

### Post by benquick on 2008-05-31
```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0ac8:307b Z-Star Microelectronics Corp.
Bus 002 Device 001: ID 0000:0000

```

i got same problem with you, until now i can't do anything with my webcam

---

### Post by smileone on 2008-07-22
hi I have install the same webcam on debian lenny.

1)
Install gspca-source
```
apt-get install gspca-source
```
2)
open terminal with root privilege or sudo
go to directory /usr/src and unzip gspca.tar.bz2 file, you obtain gspca folder, enter in this new folder
3)
read instruction in /usr/share/doc/gspca-source/README.Debian 

if webcam doesn't work, it's probably that you haven't privilege on /dev/video0 (in my pc).
```
adduser name-user video
```
```
chmod 777 /dev/video0
```
```
ls -l /dev/video0
```
If webcam's colour doesn't work correctly
```
nano -w /etc/modprobe.d/options
```
add this line
```
options gspca force_rgb=1
```
That's all.
For any information write me.
A good program to admin your webcam is camorama.:lolflag:

---

### Post by xtrumanx on 2008-07-24
Hey there. I tried everything on this thread and nothing seems to be working. When I open camorama, it just hangs with a static gibberish image showing up sometimes. 

Any help?

---

