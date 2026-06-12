---
title: "HELP: CODEC for MY PC w/o NET CONNECTION?"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by k_orbz on 2007-10-14
Guys, i am a "TOTAL NOOB" in using Linux UBUNTU, 

just installed the OS on my PC that doesn't have net connection.

My question is this..

How can i install the applications I want?? And the  codecs that are needed for DVD and MP3 playback.

Suggestions and TIPS would be much appreciated. TNX

Is it possible for me to download it on another PC then save the file to a mobile media or something??

And what are the steps for installations??


:popcorn:!

---

### Post by christhemonkey on 2007-10-14
See the link in my signature.

That program will download what you want, and you can save the files it downloads to a usb stick or something, then go to your ubuntu box and install all of the files.

---

### Post by k_orbz on 2007-10-14
> **christhemonkey said:**
> See the link in my signature.

That program will download what you want, and you can save the files it downloads to a usb stick or something, then go to your ubuntu box and install all of the files.

Can this program run on WINDOWS? Sorry for asking such a silly question.. I'm using a PC w/ WINDOWS XP OS right now but this UNIT restricts opening of EXECUTABLE files. Which in short means, I can't try the software for the moment :(


by the way, THANKS!

---

### Post by christhemonkey on 2007-10-14
Yes it runs on windows. If you cant open executables then that doesnt really help.

You can do it manually, if you go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and then search for what you want, but for each package you want, you have to make sure you get all the dependencies listed, then all the dependencies of those dependencies, and so on.

---

### Post by k_orbz on 2007-10-20
> **christhemonkey said:**
> Yes it runs on windows. If you cant open executables then that doesnt really help.

You can do it manually, if you go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and then search for what you want, but for each package you want, you have to make sure you get all the dependencies listed, then all the dependencies of those dependencies, and so on.

Sorry for yet another "NOOB QUESTION".

I need some guidance my good sir, i want to dload this package (gstreamer0.10-plugins-farsight) but when i place this in your program, it can't download a thing.. :confused:

If you could give me a simple step by step guidance sir would really be appreciated. THANKS!

---

### Post by christhemonkey on 2007-10-22
Ok,
Step 1:
Run the .exe file

Step 2:
Type in the version of ubuntu you are using (dapper, fiesty or gutsy)

Step 3:
Type in the architecture you use (most use i386)

Step 4:
Type in package name

Step 5:
Click the button

Step 6:
Wait as your package and all the dependencies are downloaded!

Step 7:
Transfer across all the packages and install them all, either by double clicking on them or you can place them all in a folder and run this command:
```
sudo dpkg -i ./*.deb 
```

---

### Post by k_orbz on 2007-10-31
The program states it is downloading 31 files for the "gstreamer0.10-plugins-farsight" package, but when it goes to 28 of 31 is stops and when checking the configured save directory, theres no file.. Not even one.. :(

---

