---
title: "Webcam trust WB-1100G installation in ubuntu"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by cormorano1 on 2008-01-19
This post is to share  a solution on an installation problem that make me fool for a couple of week.

How to install the WG-1100G webcam in ubuntu 7.10

The procedure is quite simple:
 1- verify the gspca module is installed in your pc by typing the following command:
     modprobe -l | grep gspca
   the output should be: 
     /lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko
    
   if this module is not present, download and install it from this site: [http://mxhaard.free.fr/](http://mxhaard.free.fr/) 

 2 - edit with vi or gedit  the file  "/etc/modprobe.d/blacklist" with the command "sudo vi  /etc/modprobe.d/blacklist "  and add the following line: 
     blacklist sn9c102

3- plug your webcam to an USB port and reboot the system

4- now do the command : sudo chmod a+rw /dev/video0  

At this point the webcam should be functional. To try it you can use xawtv.
Type the following command: xawtv -hwscan  

The output shoulld be:  

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l
    name : Sonix sn9c10x + Pas106 sensor
    flags:  capture 

Hope this little tutorial can help someone.

Cormorano1

---

### Post by vivalant on 2008-01-21
Try the Generic V4L1+V4L2 SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org) . It gives you better quality, do not confuse with the v4l2-only sn9c1xx driver.

---

