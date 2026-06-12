---
title: "Connecting Sony Experia Z"
date: 2013-09-20
forum: Mobile Technology Discussions (CLOSED)
---

### Post by flyers2114 on 2013-09-20
**Version 12.04.3 LTS**

I am brand new to this. I used Ubuntu a long time ago but didn't change any hardware, etc. .....So yes call me a noob....:DHere is the problem...I cannot get it to recognize my phone at all now,,......Originally when I first added it it came with an error..."Unable to Mount Android Error initializing camera- 60: Could not lock the device" So I installed the sdk for android ...tried to hook it up again and now I get nothing.....Please help...I am trying to root the phone...Another question which may be the issue, how do you install the phone drivers? Or any extra drivers period? Thank you...Oh and trust me I have been researching for the last 24 hours trying to find a fix..

EDIT: I forgot to add that I have an Samsung Galaxy S3 also. All it does is give me the cannot mount error that I stated above. Also the usb ports are working because I tested my external hard drive with no issues....so it has to be a driver issue..

I was still trying to find a fix and thought it was this. setting the auto mount. But I get errors in the script and nothing is in that file either?

```
flyers2114@flyers2114-HP-Pavilion-dv2500-Notebook-PC:~$ dconf-editor
The program 'dconf-editor' is currently not installed.  You can install it by typing:
sudo apt-get install dconf-tools
flyers2114@flyers2114-HP-Pavilion-dv2500-Notebook-PC:~$ sudo apt-get install dconf-tools
[sudo] password for flyers2114: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  dconf-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 77.6 kB of archives.
After this operation, 293 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe dconf-tools i386 0.12.0-0ubuntu1.1 [77.6 kB]
Fetched 77.6 kB in 0s (179 kB/s) 
Selecting previously unselected package dconf-tools.
(Reading database ... 210373 files and directories currently installed.)
Unpacking dconf-tools (from .../dconf-tools_0.12.0-0ubuntu1.1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0 ...
Setting up dconf-tools (0.12.0-0ubuntu1.1) ...
flyers2114@flyers2114-HP-Pavilion-dv2500-Notebook-PC:~$ dconf-editor


(dconf-editor:12742): Gtk-WARNING **: Theme parsing error: a11y.css:408:23: 'px' is not a valid color name


(dconf-editor:12742): Gtk-WARNING **: Theme parsing error: a11y.css:465:23: 'px' is not a valid color name


** (dconf-editor:12742): WARNING **: dconf-schema.vala:401: Unknown tag <comment>


** (dconf-editor:12742): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends


** (dconf-editor:12742): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends


** (dconf-editor:12742): WARNING **: dconf-schema.vala:401: Unknown tag <comment>
flyers2114@flyers2114-HP-Pavilion-dv2500-Notebook-PC:~$ dconf-editor


(dconf-editor:12747): Gtk-WARNING **: Theme parsing error: a11y.css:408:23: 'px' is not a valid color name


(dconf-editor:12747): Gtk-WARNING **: Theme parsing error: a11y.css:465:23: 'px' is not a valid color name


** (dconf-editor:12747): WARNING **: dconf-schema.vala:401: Unknown tag <comment>


** (dconf-editor:12747): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends


** (dconf-editor:12747): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends


** (dconf-editor:12747): WARNING **: dconf-schema.vala:401: Unknown tag <comment>
flyers2114@flyers2114-HP-Pavilion-dv2500-Notebook-PC:~$ 

```

---

### Post by flyers2114 on 2013-09-25
Bump?? no one

---

### Post by Bucky Ball on 2013-09-25
*Thread moved to **Mobile Technology Discussions**.*

Another staff member may feel it is better elsewhere (***Hardware*** possibly) and move again accordingly, but see how you go here for now. You don't mention the Ubuntu release you are using. Vital information. ;)

---

### Post by flyers2114 on 2013-09-25
oops good point....thx sir!

---

### Post by 3rdalbum on 2013-09-27
Ubuntu 12.10 and below can't directly mount devices running Android 3 and above.

Either upgrade to Ubuntu 13.04, or send files across to the phone using the 'adb-push' command, or set up the phone as an FTP server and connect the computer to the server over wifi.

---

### Post by flyers2114 on 2013-09-27
thank you! now that makes sense because I been searching and scouring everywhere to no avail...I will downgrade for now....seriously really appreciate you taking the time to post...have a good one...

plus I swore I grabbed the latest Ubuntu version...not sure how I didn't...lol

---

