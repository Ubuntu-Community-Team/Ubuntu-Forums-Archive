---
title: "camera problems with 9.04"
date: 2009-11-18
forum: Multimedia Software
---

### Post by chevyiron420 on 2009-11-18
I have a evision clearview camera that we bought from AOL some time ago. If i cable the camera to the usb port i cant find anything and fspot says no camera found. If i put the camera card into the cf/md slot and go to computer and click on that drive it says it cant mount file. 
 I found this forum late and am alwready frustrated with it. Can someone help?
 I am a real newby here and have to have simple and explicit instruction. Thanks--phil

---

### Post by no2498 on 2009-11-18
you need programs like cheese and wxcam
so you can see the cam
plug the cam in open the terminal copy an past ( gstreamer-properties )
click video try diff settings
good luck

---

### Post by chevyiron420 on 2009-11-18
Thanks, but that seems to be about streaming vidio. I just want to be able to work with my pictures.--phil

---

### Post by chevyiron420 on 2009-11-18
Im sorry to put information here in pieces but i forgot. I can plug in the sd card from my sons camera and it works fine. I think my problem has something to do with my camera being bought from AOL. The pictures in the camera are labeled AOL_ xxxxx jpeg. If i plug in the camera in my old computer(win98) and dont use the photosuite software on it it opens the pictures with microsoft internet explorer provided by aol?????

---

### Post by xc3RnbFO8P on 2009-11-19
> The pictures in the camera are labeled AOL_ xxxxx **jpeg**
In Terminal:
> identify -list format
Check if you got **jpeg** support 
and if you got **libquicktime1** installed (Synaptic Package Manager)

---

### Post by chevyiron420 on 2009-11-19
> **Ringi said:**
> In Terminal:

Check if you got **jpeg** support 
and if you got **libquicktime1** installed (Synaptic Package Manager)
This is what came up
philip@philip-desktop:~$ identify -list format 
The program 'identify' can be found in the following packages:
 * imagemagick
 * graphicsmagick-imagemagick-compat
Try: sudo apt-get install <selected package>
bash: identify: command not found

 I dont know what this means though.--phil

---

### Post by xc3RnbFO8P on 2009-11-19
> sudo apt-get install ImageMagick
Try the CF card again.

---

### Post by chevyiron420 on 2009-11-19
This is what i got
philip@philip-desktop:~$ sudo apt-get install ImageMagick 
[sudo] password for philip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ImageMagick

---

### Post by xc3RnbFO8P on 2009-11-19
In Synaptic Package Manager:
Settings> repositories> Ubuntu Software check all
Settings> repositories> Update> check all
Then reload or in Terminal: 
sudo apt-get update

---

### Post by chevyiron420 on 2009-11-19
Im not doing something right. I still get this.
philip@philip-desktop:~$ sudo apt-get install ImageMagick 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package ImageMagick
I think im gettin lostand not doing something right

---

### Post by chevyiron420 on 2009-11-19
Ringi, im getting to frustrated. I dont understand what im doing. If you can think of anything let me know. Im going to go work on my 57 chevy, i know what im doing with it. Ill be back later.

---

### Post by chevyiron420 on 2009-11-19
> **Ringi said:**
> In Synaptic Package Manager:
Settings> repositories> Ubuntu Software check all
Settings> repositories> Update> check all
Then reload or in Terminal: 
sudo apt-get update
I have followed these steps over and over and i dont seem to be getting imagemagick. I dont know what im doing wrong but i cant get it.
I dont require alot from a system but i need my floppy, camera, dvdrom. So far i got the floppy working but not the rest. I kept my old drive with win 98 and ive got it out of the closet and its about to go back in.

---

### Post by xc3RnbFO8P on 2009-11-20
In Synaptic Package Manager:
Settings> repositories> Ubuntu Software, **uncheck cdrom**
Download from: Main Server
[ATTACH]136894[/ATTACH]
[ATTACH]136897[/ATTACH]

---

### Post by chevyiron420 on 2009-11-20
Ringi, i did it two or three more times and it still reads this.
philip@philip-desktop:~$ sudo apt-get install ImageMagick 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ImageMagick

---

### Post by xc3RnbFO8P on 2009-11-20
Then check in Synaptic Package Manager.

---

### Post by chevyiron420 on 2009-11-20
This is a whole new ball game and i stumbled across it by dumb luck. If i plug in the cf card from my camera, then go to, system, administration, storage device manager, a new device shows up. Its called sdb. I click on it and it opens up to sdb1. I click on it and click mount. Then a icon shows on my desktop. I click on that and it shows a folder labeled AOL, i click on that and there are my pictures. I dont know how to make this more convenient but it works. I  restarted my computer to see if the icon came back automaticly and it doesnt, i have to go thru it each time. Any sugestions?:D

---

