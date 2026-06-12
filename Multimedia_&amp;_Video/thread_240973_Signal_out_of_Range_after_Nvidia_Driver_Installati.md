---
title: "Signal out of Range after Nvidia Driver Installation"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by reneoctavio on 2006-08-21
I want to install xgl on my computer but when I install the drivers the monitor says that the signal is out of range, I tried installing nvidia-glx and I also tried installing the drive that have in nvidia site. The first recognize the driver and install sucessfully, but when I restart X, the monitor says that the signal is out of range, and I have to do a dpkg-reconfigure xserver-xorg and choose nv driver instead of nvidia(that doesn't work) to see my desktop again. The second way, it install sucessfully but when I change the nv to nvidia, the X says that is not installed.

What I have to now? Thanks.

My Computer is AMD Semprom 2600+ 1GB Ram, Asus K8N-4E Deluxe, Geforce 6600 PCI-e 256mb HD 80GB.

---

### Post by tseliot on 2006-08-21
Install Envy and follow the instructions on the website;
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

(choose not to start the Xserver when Envy asks you

Then try point 10 of the Problems Section of my guide:
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

Restart the Xserver:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use kdm)
```

---

