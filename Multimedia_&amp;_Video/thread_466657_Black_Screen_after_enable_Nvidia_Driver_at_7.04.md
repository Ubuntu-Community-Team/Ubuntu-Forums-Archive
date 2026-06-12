---
title: "Black Screen after enable Nvidia Driver at 7.04"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by hutucong on 2007-06-06
I enabled the non supported nvidia driver for my laptop. After the package was installed and I re-started I was faced with a completely blank screen.

What should I do now? A newbie for Ubuntu/Linux. Please give me some detail instructions.

Thanks!

---

### Post by Nythain on 2007-06-07
well... for a temporary fix to get your gui back...
at the blank screen hit control alt f2
that should hopefully bring you to a console login
log in
then type
sudo nano /etc/X11/xorg.conf
find the section that says Driver      "nvidia" and change it to "nv"
control x, yes, enter yadayadayada to save and exit the program saving the file
then restart the machine...

as for why the proprietary driver gave you a blank screen, possibly a driver mismatch, or an error in your xorg.conf file somewhere that x cant comprehend (if changing the driver from "nvidia" to "nv" didnt fix the problem then an error in your xorg.conf file is more than likely the culprit, at wich point i would suggest logging back in to the console and trying the sudo dpkg-reconfigure xserver-xorg option of setting up a fresh new xorg.conf)

ok, hopefully at least some of that helps

---

### Post by hutucong on 2007-06-07
Thank you for your answer.

I tried your instruction and after change xorg.conf I did get my GUI back. I will figure out what is wrong.
 
> **Nythain said:**
> well... for a temporary fix to get your gui back...
at the blank screen hit control alt f2
that should hopefully bring you to a console login
log in
then type
sudo nano /etc/X11/xorg.conf
find the section that says Driver      "nvidia" and change it to "nv"
control x, yes, enter yadayadayada to save and exit the program saving the file
then restart the machine...

as for why the proprietary driver gave you a blank screen, possibly a driver mismatch, or an error in your xorg.conf file somewhere that x cant comprehend (if changing the driver from "nvidia" to "nv" didnt fix the problem then an error in your xorg.conf file is more than likely the culprit, at wich point i would suggest logging back in to the console and trying the sudo dpkg-reconfigure xserver-xorg option of setting up a fresh new xorg.conf)

ok, hopefully at least some of that helps

---

