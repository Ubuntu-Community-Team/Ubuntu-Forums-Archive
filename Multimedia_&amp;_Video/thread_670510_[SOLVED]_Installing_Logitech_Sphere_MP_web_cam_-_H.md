---
title: "[SOLVED] Installing Logitech Sphere MP web cam - Help needed"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by malayka on 2008-01-17
Hi everyone,

I am trying to install a Logitech web cam (Sphere MP) on to my ubuntu operating system. I am on the 7.10 version of ubuntu.

Are there any instuctions or advice someone can give to try and install the cam.

I have seen the following advice but don't really understand how it works.

Source code for the Linux UVC kernel driver can be found in the Linux UVC Subversion repository on the BerliOS project page.

If you are in a hurry, checkout the latest version with

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

I'm very new to open source so please bear with me if I sound a little stupid.

Any help would be much appreciated. 

Many thanks 

Chris

---

### Post by linuxwizard on 2008-01-17
Have you tried using the webcam with Ekiga or Camorama see if it works before installing any drivers it may just work. plug cam in > in terminal > type > lsusb > post results

---

### Post by malayka on 2008-01-18
Hi,

Thanks for the quick reply.

I ran the lsusb command and the following info was installed:

cgadmin@cgadmin-desktop:~$ lsusb
Bus 001 Device 002: ID 6891:a727  
Bus 001 Device 003: ID 046d:08cc Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:0707 Microsoft Corp. 
Bus 004 Device 003: ID 045e:0717 Microsoft Corp. 
Bus 004 Device 004: ID 045e:0714 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
cgadmin@cgadmin-desktop:~$ 


However I still can not see the system pick up the web cam . When  I look in the Hardware Information there are no references to it.

regards

Chris

---

### Post by linuxwizard on 2008-01-18
This is your webcam
Bus 001 Device 003: ID 046d:08cc Logitech, Inc.

---

### Post by malayka on 2008-01-18
Thanks again for your quick reply.

I have installed camorama but when I launch it it comes up with the following error:

could not connect to video device (/dev/video0)
please check connection.


Is this because its not looking in the right place?

If so how do I make the connection?

Are there other drivers I need to install?

Kind regards

Chris

---

### Post by linuxwizard on 2008-01-18
I wished you would have tried Ekiga first. But this is the driver you need > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) > your cam is 13 down from top. Look at notes on that line you may have issues with the webcam. You can use these instructions to install driver > [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC). Also from here > [http://www.quickcamteam.net/hcl/linux/logitech-webcams](http://www.quickcamteam.net/hcl/linux/logitech-webcams) > your cam 10 down from top > look at notes.

---

### Post by malayka on 2008-01-19
Hi Linux Wizard,

Thanks again for the information.

I managed to follow the instructions to install UVC using the subversion repository.   Correctly I hope.

However I still get an error when trying to open camorama.    'Could not connect to video device'.

Any thoughts?

Would I be better installing Ekiga?

Kind Regards


Chris

---

### Post by linuxwizard on 2008-01-19
Did you reboot your computer after installing driver ? Ekiga is installed by default > Applications > Internet > Ekiga Softphone

---

### Post by malayka on 2008-01-19
Hi,

Yes rebooted the PC a couple of times.

If I try it with Ekiga I get an  error message saying Error while opening video device UVC Camera (046d:08cc) A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

Your video driver doesn't support the requested video format.

Not sure what i've missed. Probably something quite simple?

regards

chris

---

### Post by linuxwizard on 2008-01-19
Open Ekiga > click on Edit > Preferences > look for Devices > Video Devices > try changing video plugin settings > also make sure your webcam is listed in input device

---

### Post by malayka on 2008-01-19
Hi linuxwizard

Thankyou very much for all your help. Changing the settings has worked. 

A very satisfied linux user!

Kind regards

Chris

---

### Post by linuxwizard on 2008-01-19
You're Very Welcome malayka I am glad that I was able to help you and now everything is setup and working for you. Please mark thread as SOLVED.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

