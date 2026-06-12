---
title: "Not recognizing QuickCam Deluxe for Notebooks"
date: 2009-08-20
forum: Multimedia Software
---

### Post by Elisavan on 2009-08-20
I'm having trouble with my Logitech QuickCam Deluxe for Notebooks on Jaunty Ubuntu.:(

I'd like to know if these two are copmatible, which patches/fixes/drivers I need/should have to make it work, and if there are any known programs that will not work with this webcam.:confused: With this problem, I am at the point at which Ubuntu does not 'bat an eye' when I plug in the USB cord for the Webcam.

I'm at the very beginning of using Ubuntu (just installed at the beginning of Aug/09) and have not begun to try to find workarounds for my webcam until recently. I'm working from a clean slate in this area, and so the more help I can get on this problem would be excellent!:)

Hopefully some people can help me! ^_^

---

### Post by madurst on 2009-08-20
hey i just got my webcam almost working... first in the terminal type  
```
lsusb
```in the terminal and paste what comes out
should look like this 

```
 
matt@matt-laptop:~$ lsusb
Bus 001 Device 013: ID 046d:09c1 Logitech, Inc. QuickCam Deluxe for Notebooks
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0461:4d65 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
matt@matt-laptop:~$ 

``` now lookup what comes out as your logitech driver at this website and see if it has any known issues.

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

use the ID numbers to look it up. 

Matt

---

