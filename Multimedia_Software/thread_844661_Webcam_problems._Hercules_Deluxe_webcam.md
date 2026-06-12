---
title: "Webcam problems. Hercules Deluxe webcam"
date: 2008-06-29
forum: Multimedia Software
---

### Post by annagud on 2008-06-29
Hi

My webcam is a Hercules Deluxe (I think) and I can't get it to work. I am running Hardy Heron and when I run lsusb my results are:

anna@anna-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05a9:4519 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 0000:0000  

I tried to follow this thread: [http://ubuntuforums.org/showthread.php?t=690666](http://ubuntuforums.org/showthread.php?t=690666)
Well make install resulted in error so I was kinda stuck after that.

Please if anyone has the same and made it work some help would be great.

Anna

---

### Post by ZeldeR on 2008-08-16
Hallo Anna, I have Hercules webcam Deluxe too and I tried your manual and It doesn't work. I done it right but no ideas why.

I found an other way to get this webcam work:

Hercules Webcam Deluxe instaled on Ubuntu and working with Skype!

PS. this is Hercules Deluxe 

[IMG]http://zeldor.funpic.de/image/9254hercules_webcam_d.jpg[/IMG]

This is a brief tutorial about installing the webcam Hercules Deluxe in Ubuntu or Debian distributions.

It is dedicated by ZeldoR who owns the Hercules Deluxe webcam

1. To install the drivers you need first the linux headers. You install them typing on a terminal window (Applications -> Terminal on Ubuntu):


[COLOR="Red"]sudo apt-get install build-essential linux-headers-`uname -r`[/COLOR] 

2. You need to to get the modules for your webcam:

[COLOR="Red"]wget [http://www.zeldor.biz/Ubuntu/ov51x-jpeg-1.5.8.tar.gz](http://www.zeldor.biz/Ubuntu/ov51x-jpeg-1.5.8.tar.gz)[/COLOR]

 3. Then you extract the drivers:

[COLOR="Red"]tar -xvf ov51x-jpeg-1.5.8.tar.gz [/COLOR]

4. And Change directory to where your sources are:

[COLOR="Red"]cd ov51x-jpeg-1.5.8 [/COLOR]

5. Prepare the installation files

[COLOR="Red"]make [/COLOR]

6. Compile the modules:

[COLOR="Red"]sudo make install[/COLOR] 

7. And install them:

[COLOR="Red"]sudo depmod -A[/COLOR]
 
[COLOR="Red"]sudo modprobe ov51x-jpeg[/COLOR]

8. You should now be able to enjoy images from your webcam. To view if it worked you can download and install wxcam, plug-and-play your webcam and you should be able to see video your streaming with wxcam

[COLOR="Red"]http://www.zeldor.biz/Ubuntu/wxcam_1.0.1_i386.deb[/COLOR]


9. Now, if you use Skype on your computer and you always see a black square, you can make your webcam working with Skype with the following code:

[COLOR="Red"]echo "options ov51x-jpeg forceblock=1" | sudo tee -a /etc/modprobe.d/options
[/COLOR]


I think  it is very very simple try it and write some comments.

Sry. my English is bad but I'm shure you understand me  :smile:

ZeldoR [ZeldeR]

---

### Post by annagud on 2008-08-23
Thank you. :)
Your English is fine

Anna

---

### Post by kem on 2008-10-08
ZeldeR, thank you for your step-by-step instructions. Good news is it works well - at least in wxCam or Cheese. Bad new is I was unable to see video in Skype and Ekiga.

EDIT: Finally, it works! I don't exactly what was the problem but after restart it works! Thank you!

---

### Post by _sluimers_ on 2008-11-18
I've followed the instructions, but
I get a black screen on xawtv, and static on cheese, gyachi, camorama, wxcam and kopete.

If anyone can help me with this it would be great.

---

### Post by duki_du on 2008-11-18
Hello
I'm new with Ubuntu, end I have the same problem.
I don't anders tend what I need to doe with step:

4.And Change directory to where your sources are:

[COLOR="Red"]cd ov51x-jpeg-1.5.8[/COLOR] 

5. Prepare the installation files

[COLOR="Red"]make[/COLOR]

Can somebody pleas explain what I need too doe?  Venn I tipe make in terminal he say command not found
.

Sorry, my English is bad, but pleas help..

---

### Post by gychang on 2010-07-18
will this work with linuxmint, latest 32bit?, I have the webcam and use LM9.

gychang

---

### Post by sathish85295 on 2010-07-21
hi everyone....
iam using ubuntu 10.04 64bit, my web cam is my mobile phone motoroker E6.... i use it quit a long time in windows... works perfect.... now for the first time iam trying to use it in ubuntu... finally it works in ubuntu 10.04... 

one problem is it is not working properly in gyachi v1.2.6 but it works fine in cheese....
i hav attached 2 images one from cheese and another one from gyachi.... can any one tell me a solution for this????

in cheese it works fine with the resolution setup 640x480... but cheese gives the same error image like gyachi if resolution setup changed to some other lower resolution...

can any one help me???:(

---

### Post by YannBuntu on 2010-07-27
@sathish85295 : which protocol do you use ? Yahoo? Gtalk? Jabber?

---

