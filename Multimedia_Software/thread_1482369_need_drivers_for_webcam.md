---
title: "need drivers for webcam"
date: 2010-05-13
forum: Multimedia Software
---

### Post by Skipopis on 2010-05-13
Ok I just bought a microsoft  lifecam vx-3000 and I want to ues it on my Ubuntu 9.04 os, please help. 


Skipopis

---

### Post by lrcaballero on 2010-05-13
Try the following:
CODE...
sudo modprobe uvcvideo
sudo apt-get install cheese
cheese

Luis Caballero

---

### Post by no2498 on 2010-05-13
if what he said does not work
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

910 and up cheese webcam booth should be loaded
look in sound & video

---

### Post by Skipopis on 2010-05-14
thank-you for your quick reply's, but neither option worked.


Skipopis



p.s. still need help with webcam

---

### Post by no2498 on 2010-05-14
Microsoft VX-3000 webcam

tells you in that post

---

### Post by no2498 on 2010-05-14
zerwas 
A Carafe of Ubuntu

 
 
 
Join Date: Dec 2004
Location: Germany
Beans: 131 
Ubuntu 9.10 Karmic Koala 
    	Re: Microsoft VX-3000 webcam 
Okay,

first we need to open a terminal. To do this, go to Applications menu -> Accessories -> Terminal.

Now you enter these commands (one by one):
Code:
cd /tmp
wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
tar xvfj tip.tar.bz2
cd v4l*
make
Wait, until it is finished (it will finish with an error).
Now, execute this command to open a file with a text editor:
Code:
gksudo gedit /tmp/v4l*/v4l/.config
Search for the line 
Quote:CONFIG_DVB_FIREDTV=m 

and change it to
Quote:CONFIG_DVB_FIREDTV=n 

Now click on "Save", close the text editor and get back to the terminal where you enter:
Code:
make
sudo make install
Now reboot your computer and your webcam should work.

---

### Post by Skipopis on 2010-05-14
Thanks I followed your instructions to the letter to no avail. Webcam not working.


Skipopis

---

### Post by no2498 on 2010-05-14
Skipopis slow down and try again 

and you do have all the extras installed i hope
not sure if its mebubuntu extras in 10.04 or not
as i use 804 and 910

---

### Post by Skipopis on 2010-05-14
not sure what extras I'm running 9.04 and I've just started to download programs to it, its fairly clean.

---

### Post by no2498 on 2010-05-15
ok did you get adobe flash or use something else

---

### Post by Skipopis on 2010-05-19
yes I use adobe flash

---

### Post by no2498 on 2010-05-22
sudo apt-get install ubuntu-restricted-extras

hope that helps

---

### Post by Skipopis on 2010-05-25
Thank u its working in cheese, now I need help with Skype, I have it downloaded I can see n hear the other person but they cant see or hear me. Any tips would be appreciated. 


Thank-you again, 



Ron

---

### Post by no2498 on 2010-05-25
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

think you need to do this every time you open skype
put that in a terminal

---

### Post by Skipopis on 2010-05-26
Thanks that takes care of the visuals now what about the sound. Please n thank-you




Ron

---

