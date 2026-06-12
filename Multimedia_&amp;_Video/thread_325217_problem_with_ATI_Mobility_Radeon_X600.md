---
title: "problem with ATI Mobility Radeon X600"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by dipodo on 2006-12-25
I followed this guide [ [COLOR="Red"]**here**[/COLOR] ]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") to install the fglrx driver on my HP zd8179(edgy eft)..... 
> 
dipodo@laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


and then when i 

> 
dmesg


one of the lines is the following:

> 
[17283730.440000] [fglrx:firegl_unlock] *ERROR* Process 20985 using kernel context 0


any help????? ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Kubunteando on 2006-12-25
Hi,

try to install the latest ATI drivers following:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b)

The drivers supplied with Ubuntu have some bugs, and will not work so well.
For example I am having an ATI Radeon Mobility 9000, and the games crashes after sometime consuming all the RAM. I am surprised why the forums don't talk more about this.

A little more difficult way is to install the Open Source drivers:

[www.mesa3d.org](www.mesa3d.org)
dri.freedesktop.org

And installing "driconf" from the repositories which allows you to control the OpenGL parameters if you want to finetune those. I am using the Open Source drivers because there is no support anymore from ATI of my Graphic Card further than the driver version provided in edgy by Ubuntu, but you may want to install the latest ones if those support your card.

Both ways you need to do some work. I think it should be easier to get a good performance of the Graphics cards with Linux. It took me several months, and lot of reading... But now it seems to work really fine, and I have learned a lot about Linux.

---

### Post by Kubunteando on 2006-12-25
If you still have problems after installing the latest drivers from ATI.
You can post the output of:

"lsmod | grep -i fglrx"

And also the file: /var/log/Xorg.0.log

And you configuration file: /etc/X11/xorg.conf

Good luck,

---

