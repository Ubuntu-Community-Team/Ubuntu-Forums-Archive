---
title: "Sony motion eye webcam not working"
date: 2010-09-05
forum: Multimedia Software
---

### Post by zazootheparrot on 2010-09-05
I have a Sony Vaio VGN-SZ740 laptop with ubuntu 10.04. 
Unfortunately the motion eye webcam in not working.  When I type lsusb in the terminal, it gives the following message: 
```
Bus 007 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 054c:0281 Sony Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Could anyone please help me? I really need the webcam to work!!!

Thanks in advance

---

### Post by zazootheparrot on 2010-09-05
Actually, the sound recorder doesn't record my voice so I think the microphone is not working and when I try to open Guvcview it gives me the following error: 
" Unable to open device Please make sure the camera is connected and that the correct driver is installed" .

I can't use skype, nor cheese and Ekiga. 

Any ideas?

---

### Post by zazootheparrot on 2010-09-06
bump?

---

### Post by no2498 on 2010-09-06
i have seen a few people asking for help for this kind of webcaam
Bus 001 Device 003: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870

they was told to get a driver

type webcam
in a terminal see what it says

---

### Post by zazootheparrot on 2010-09-06
> **no2498 said:**
> i have seen a few people asking for help for this kind of webcaam
Bus 001 Device 003: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870

they was told to get a driver

type webcam
in a terminal see what it says

Many thanks for replying :D

I typed webcam and it said: 
```
ava@ava-laptop:~$ webcam
The program 'webcam' is currently not installed.  You can install it by typing:
sudo apt-get install webcam

```

so I installed webcam, after that I typed webcam again. The following appeared: 
```
ava@ava-laptop:~$ sudo apt-get install webcam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xawtv-plugins
The following NEW packages will be installed:
  webcam xawtv-plugins
0 upgraded, 2 newly installed, 0 to remove and 38 not upgraded.
Need to get 125kB of archives.
After this operation, 582kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid/universe xawtv-plugins 3.95.dfsg.1-8.1ubuntu1 [86.2kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid/universe webcam 3.95.dfsg.1-8.1ubuntu1 [38.7kB]
Fetched 125kB in 0s (195kB/s)  
Selecting previously deselected package xawtv-plugins.
(Reading database ... 190988 files and directories currently installed.)
Unpacking xawtv-plugins (from .../xawtv-plugins_3.95.dfsg.1-8.1ubuntu1_i386.deb) ...
Selecting previously deselected package webcam.
Unpacking webcam (from .../webcam_3.95.dfsg.1-8.1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up xawtv-plugins (3.95.dfsg.1-8.1ubuntu1) ...
Setting up webcam (3.95.dfsg.1-8.1ubuntu1) ...
ava@ava-laptop:~$ webcam
reading config file: /home/ava/.webcamrc
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no grabber device available

```

Would you kindly tell me what to do now? 

Thanks

---

### Post by zazootheparrot on 2010-09-07
DO I need to install a driver or something?

---

### Post by no2498 on 2010-09-07
most webcam drivers are installed

try the cam in cheese
look in sound & video for cheese webcam booth
if you do not find cheese
type it in a terminal just cheese

---

### Post by zazootheparrot on 2010-09-18
> **no2498 said:**
> most webcam drivers are installed

try the cam in cheese
look in sound & video for cheese webcam booth
if you do not find cheese
type it in a terminal just cheese

I just tried cheese: 

```
root@ava-laptop:~# cheese

(gnome-help:2170): Yelp-WARNING **: Failed to load config file: No such file or directory


(gnome-help:2170): Gtk-CRITICAL **: gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(gnome-help:2170): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-help:2170): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-help:2170): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(gnome-help:2170): Gtk-CRITICAL **: gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(gnome-help:2170): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-help:2170): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-help:2170): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed


```

It said: no device found!

What should i do now?

Thanks

---

### Post by no2498 on 2010-09-18
[http://ubuntuforums.org/showthread.php?p=8930938](http://ubuntuforums.org/showthread.php?p=8930938)


thats the first hit in google for this

ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870

---

### Post by zazootheparrot on 2010-09-19
> **no2498 said:**
> [http://ubuntuforums.org/showthread.php?p=8930938](http://ubuntuforums.org/showthread.php?p=8930938)


thats the first hit in google for this

ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870


Thank you soooooooo much for your help! :grin:

---

### Post by no2498 on 2010-09-20
? did it help you if yes mark it solved

---

### Post by zazootheparrot on 2010-09-21
Sure! Thx :)

---

### Post by mcopelli on 2011-10-18
Thank you so much! It worked!

---

