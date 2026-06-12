---
title: "Microdia Webcam drivers?"
date: 2008-10-01
forum: Multimedia Software
---

### Post by GodsDead on 2008-10-01
Hey, im trying to get my webcam to work on my ubuntu server, i have installed webcam-server, but after running i get unable to initialise camera, so i guess that the driver isnt installed, being a server and all.. i found this [http://mxhaard.free.fr/](http://mxhaard.free.fr/) but my camera dousnt seem to be supported, using:
```

lsusb

```
gave me
```

Bus 004 Device 005: ID 0c45:627b Microdia
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 0000:0000

```

And thats as far as i got, can someone help me get ubunu server to recomize my camera, so i can setup a "survalance" camera onto my server =]

Thanks.

---

### Post by ewan86 on 2008-10-03
I also have the same problem in that I cannot get my webcam to work which is a major bind. It is a microdia too.

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 001 Device 003: ID 0c45:6130 Microdia 
Bus 001 Device 001: ID 0000:0000

---

### Post by kwacka on 2008-10-03
I had a couple of these a year or so back and gave up trying to get installed - but it seems that things might have moved on a little.

A couple of places to try:

[http://www.linuxtv.org/v4lwiki/index.php/Webcams](http://www.linuxtv.org/v4lwiki/index.php/Webcams)

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

after following instructions at the second my camera (0c45:6270 Microdia U-CAM PC Camera NE878) worked. 

Insmod initially failed, but worked immediately after I 'modprobe videodev'.

---

### Post by ewan86 on 2008-10-03
thanks for your help kwacka. I am trying to follow the the advice from the second link as you suggested but I am way too technicaly inept to understand it. It is double dutch to me. I'm not even sure I have all the Git things installed that I need. I could not find the cogito thing they suggested for ubuntu, [http://groups.google.com/group/microdia/web/using-git-with-microdia]("http://groups.google.com/group/microdia/web/using-git-with-microdia") ,but I found git-gore and git-gui though I have no idea what these are!!

I have included an image of what I have installed in synaptics package manager.

I cannot even then do step one where it says to cd to a directory as I have no idea what this means!!

[COLOR="RoyalBlue"]1. Download the source code

From a command-line prompt, cd to a directory where you want to download it, then run the command: 

$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)

 

This will create a folder named "microdia" which contains all the source code[/COLOR]


when i type in the command given there this is what I get:

[COLOR="RoyalBlue"]ewan@ewan-laptop:~$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
Initialized empty Git repository in /home/ewan/microdia/.git/
/usr/bin/git-clone: 374: curl: not found[/COLOR]

sorry I am such an helpless case!!!

---

### Post by kwacka on 2008-10-07
Sorry for the delay.

There isn't a file named 'cogito' in the Ubuntu repositores, I used synaptic to search for files with this in the description and found a library file and installed that. (Cogito has been removed from Debian/Ubuntu repositories)

Curl is a data transfer tool (http, ftp, https, telnet et al) just ```
sudo apt-get install curl
```

---

### Post by ewan86 on 2008-10-07
Thanks Kwacka. I've now made some progress and can actually see my webcam in Amsn.It wont work with cheese or ekiga tho. Also its a funny colour even after configuring and a bit fuzzy! is this the best I can hope for?

Also when configuring in msn it gives the device as a v4l: Sonix Pccam + which i think is the driver which I installed when using easy cam...would this affect it?? It gives the channel as SN9CXXX which I guess would be right.

I have included attachments of what I did. Also this is the link for the page I am following. [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft]("http://groups.google.com/group/microdia/web/testing-microdia-driver-draft")

[ATTACH]87646[/ATTACH]

[ATTACH]87647[/ATTACH]

[ATTACH]87648[/ATTACH]

[ATTACH]87649[/ATTACH]

Thanks for your help :)

---

### Post by intel on 2008-10-15
ewen your webcam is already supported by the Linux kernel
if its not working properly you need to file a bug report against GSPCA 2 package

again, your webcam is not supported by the driver at repo.or.cz/..... 
You don't need to do such complex things

---

