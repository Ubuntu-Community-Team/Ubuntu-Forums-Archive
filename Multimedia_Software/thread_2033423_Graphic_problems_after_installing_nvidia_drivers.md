---
title: "Graphic problems after installing nvidia drivers"
date: 2012-07-26
forum: Multimedia Software
---

### Post by wasabishot on 2012-07-26
Hello

I've just installed ubuntu 12.04 in my new dell inspiron n5100 laptop.

I noticed in "details" that my graphic card was not recognized so i searched the web for a solution.
It seems that many users have problems with nvidia graphic cards and furthermore with "optimus".

There was only one command line I followed
```
sudo apt-get install nvidia-current
```after reboot unity doesnt work anymore, something i was able to recover using this thread:
[http://askubuntu.com/questions/132112/how-to-install-nvidia-geforce-gt525m-driver-on-ubuntu12-04](http://askubuntu.com/questions/132112/how-to-install-nvidia-geforce-gt525m-driver-on-ubuntu12-04)

now, the problem is that my screen resolution is stuck on 640X480 and I'm not able to get back to my older settings.

please help!

---

### Post by BLTicklemonster on 2012-07-26
I'm very much interested in knowing the fix to this, also. All I have are nvidia cards, and Ubuntu has left me high and dry. 

I guess I could just dump 12.04 and go back to 11 until this is resolved, though...

(by the way, this helped, but the system bogs down immensely. Wasn't worth the hassle for me [http://askubuntu.com/questions/129322/how-to-install-a-driver-for-an-nvidia-card-not-detected-by-additional-drivers-on](http://askubuntu.com/questions/129322/how-to-install-a-driver-for-an-nvidia-card-not-detected-by-additional-drivers-on) )

---

### Post by TheFu on 2012-07-26
I'm still on 10.04 with my nvidia machine, but these commands seem to help to get things working with those cards.

```
sudo /usr/bin/nvidia-xconfig
sudo /usr/bin/nvidia-settings
```You might need to add a **option** line to the /etc/X11/xorg.conf file too specifying all the resolutions that your card supports that you want to use. Be certain the monitor also supports those modes or it could be bad.

I've found that a newer nVidia driver doesn't always mean a ***better*** nVidia driver.  Once I have something stable, I don't touch it until a new install.  I've been burned before. Since these are kernel modules, I've had to manually reinstall the modules after a new kernel gets installed too.  Sometimes the package dependencies weren't always right. I haven't seen that issue recently, however.

---

