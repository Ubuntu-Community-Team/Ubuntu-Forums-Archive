---
title: "Webcam problem"
date: 2011-05-20
forum: Multimedia Software
---

### Post by andrei90 on 2011-05-20
I have a problem with my webcam, when someone sends me an invitation on Pidgin Internet Messenger it says my linux doesn't recognize the webcam..
I'm running Xubuntu 11.04 x64 on an Acer Extensa 5635Z with Webcam Incorporated.
I also want to broadcast my webcam.

How can I fix this issue??

---

### Post by no2498 on 2011-05-20
open a terminal type dmesg click enter
after it stops type lsusb click enter
that should give a number and name of your cam
if it comes up as a rico cam you need to get a driver for it

---

### Post by andrei90 on 2011-05-20
Ok, so here it is:
```
andrei@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**[COLOR="Red"]Bus 002 Device 003: ID 064e:a103 Suyin Corp.[/COLOR]** 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

If it's Suyin what should I do?

---

### Post by no2498 on 2011-05-21
[http://www.google.com/search?client=opera&rls=en&q=064e:a103+Suyin+Corp&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=064e:a103+Suyin+Corp&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

hope you find something that helps

---

### Post by no2498 on 2011-05-21
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

sudo apt-get install cheese
it ask for your pass word you do not see any thing as you type it click enter

it comes up in sound and video as cheese webcam booth

---

### Post by andrei90 on 2011-05-21
```
andrei@ubuntu:~$ gstreamer-properties
The program 'gstreamer-properties' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-media

```
Oh boy..

---

### Post by no2498 on 2011-05-22
did you do this

sudo apt-get install gnome-media

retry gstreamer-properties

---

### Post by andrei90 on 2011-05-22
It's working on the terminal but on the messenger the button is still grey.

---

### Post by no2498 on 2011-05-23
did you try it in cheese yet

if cheese stops working you will need to get the cam working again in gstreamer-properties

then try this program wxcam

you can get it in a deb file

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

### Post by andrei90 on 2011-05-24
Cheese is working but I cant manage to connect Cheese on Pidgin messenger, the Webcam button is still grey.

---

### Post by andrei90 on 2011-05-24
I've checked their forums and look what their saying:
> **How do I configure my microphone/webcam?**
Currently, the command-line gstreamer-properties program is used. This is only available on GNOME-based systems. On other systems, Pidgin makes its best guess as to which device to use. A plugin is planned to support this functionality on other systems.

---

### Post by no2498 on 2011-05-24
im only guessing but go to the adobe site find the settings manager
you can set it to the cam you use and the mic
you may need to go to the site you use the cam on first so you can set the site to allow and remember
all at the adobe site in the settings manager

---

