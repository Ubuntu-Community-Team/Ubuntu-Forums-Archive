---
title: "Quickcam Messenger stopped working after upgrade kernel"
date: 2008-06-23
forum: Multimedia Software
---

### Post by ahbart on 2008-06-23
Hi,
After a week holiday I updated my Ubuntu hardy install including a kernel update to 2.6.24-19 (X86_64). Before that my webcam, a Logitech Quickcam Messenger (ID 046d:08da Logitech, Inc. QuickCam Messanger) was working well. I used Camorama, Skype and Cheese. All doing well.
After the update The Cam stopped working. The LED light is constantly on. 
Camorama says: Could not connect to /dev/video0 etc. I tried /dev/video1 and 2 also because of my tv-card. 

I tried to install gspcav1-20071224 from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
This doesn't work either. I found out that when I place 'blacklist gspca' in /etc/modprobe.d/blacklist and than reboot and 'sudo modprobe gspca' my cam is working! 8-)
But it is very irritating to do this everytime! And My wife cannot do this when I'm not at home.
I really do not understand what is happening here! Can anybody help me with this? Is this a bug in any package?
Please!
Bart

---

### Post by ahbart on 2008-06-23
Anyone? please any suggestion!

---

### Post by zasq on 2008-07-05
Hi Bart! Did you find a solution? I have exactly the problem here with the same came, same distribution, same programs...
Best,
zasq

---

