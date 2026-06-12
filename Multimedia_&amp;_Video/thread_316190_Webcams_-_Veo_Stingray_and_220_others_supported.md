---
title: "Webcams - Veo Stingray and 220 others supported"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by Rodneyck on 2006-12-10
Hi,

I was hoping someone more experienced with compiling and installing things could help me. I am trying to get my old VEO Stingray webcam to work on Edgy and finally found a guy who I guess has written drivers for linux that support up to 220 webcams, including the veo stingray.

He has the packet/drivers (I guess that is what they are) available for download on his website but I have no idea what to do with them. 

BTW, this is a common problem for us newbies on Linux. I find this all the time, a file to download for my problem but no instructions on how to install or compile.

I unzipped the file, but don't see any compile file or anything. I was hoping someone more experienced could take a look and help me.

Website and file:
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

---

### Post by budgie9 on 2006-12-10
I would suggest as I have in other posts for webcam help, that you download a program called Easycam2. You will find this in the Synaptic download Manager.
Then run the program and it will fetch the correct drivers from the site for your cam, provided it is supported of course.
Also you will find plenty of posts re the unpacking and installation of these tar.gz files, if you wish to do it this way. 
Another program thay you will find useful is the Camorama program, I think that is how it is spelt, that too is in the download manager.
You can use the later program to test your camera is working.

---

### Post by Rodneyck on 2006-12-10
No such luck with easycam2 or camorama, could not detect device, but thanks. ](*,)

---

### Post by Scunizi on 2006-12-12
I tried finding Easycam2 in Synaptic with all the repositories checked without any success.  I'm running Dapper LTS.  Any suggestions?

---

### Post by andoty_jazz on 2006-12-31
**Hello**

I also have veo stingray and haven't installed it. Web cam is not working. The first time I docked to the usb port veo stingray webcam, I used *gqcam* which is searched in Synaptic and it work but really blurred capture. The next time I used  *gqcam*, "/dev/video: Device or resource busy" already.

If there anyone who can help, it will be of great pleasure

Thanks in advance. :)

---

### Post by Rodneyck on 2007-01-15
I installed gqcam through syaptic, but how do you make it run? Nothing showed up when I typed it in Terminal, nor on the menu list.

Here is a guide showing how to install the latest drivers from my original post. They are installing for a quickcam, but technically it should work for the VEO Stingray as they are all contained in the same Spca5xx source. 

For me, I was able to update the new Spca5xx driver file, but it still did not work under Ekiga.  Maybe someone else can fiddle with the guide.

[http://ubuntuforums.org/showthread.php?t=303330](http://ubuntuforums.org/showthread.php?t=303330)

---

