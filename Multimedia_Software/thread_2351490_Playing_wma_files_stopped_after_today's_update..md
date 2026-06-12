---
title: "Playing wma files stopped after today's update."
date: 2017-02-03
forum: Multimedia Software
---

### Post by lammert-nijhof on 2017-02-03
After the update of today 3-feb-2017 of Ubuntu 16.04.1, I have lost the possibility to play my 24GB of wma files. I still can play the few m4a and mp3 files I have. I have tried re-installing ubuntu-restricted-extras, but that did not help. I had the same problem with Ubuntu 17.04 (the development version), but that has been corrected some months ago by an update. In a working system a lot of packages are re-installed after removing and installing ubuntu-restricted-extras. In a defect system only the package itself is installed. 

How can we correct that situation or do I have to wait a few months using 17.04 Alpha to play the music in the mean time or I could use windows media player and XP in virtualbox ?

---

### Post by deadflowr on 2017-02-03
*Thread moved to **Multimedia Software**.*

Is that a typo?
24GB files are gigantic.

---

### Post by lammert-nijhof on 2017-02-03
No I have 24 GB of music files. Immigrating I put all my LPs and my CDs on the computer in wma format and since then I also added a lot of the local music.

---

### Post by cariboo on 2017-02-03
Depending on what app you use to upgrade, you can check /var/log/apt/history.log to see if any multimedia packages were upgraded.

Synaptic also has a history log.

---

### Post by lammert-nijhof on 2017-02-04
The relevant updates have been: "Start-Date: 2017-02-03  16:06:03Commandline: aptdaemon role='role-commit-packages' sender=':1.1306'
Upgrade: gstreamer1.0-plugins-ugly-amr:amd64 (1.8.2-1ubuntu0.1, 1.8.3-1ubuntu0.1), google-chrome-stable:amd64 (56.0.2924.76-1, 56.0.2924.87-1), skypeforlinux:amd64 (1.16.0.1, 1.17.0.1), gstreamer1.0-libav:amd64 (1.8.2-1~ubuntu1, 1.8.3-1ubuntu0.1), gstreamer1.0-plugins-ugly:amd64 (1.8.2-1ubuntu0.1, 1.8.3-1ubuntu0.1)
End-Date: 2017-02-03  16:06:47"

Well the gstreamer1.0-plugins-ugly contains the wma codec and that one seem to contain the bug.

---

### Post by mc4man on 2017-02-04
It was the gst-libav package that broke wma in gstreamer.
This was the bug fixed that caused update - 
[https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1619600](https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1619600)
(- may need to file a new bug as the deed was done..

To temp workaround downgrade gstreamer1.0-libav to previous version, pick arch

amd64
[https://launchpad.net/ubuntu/+source/gst-libav1.0/1.8.2-1~ubuntu1/+build/10161238/+files/gstreamer1.0-libav_1.8.2-1~ubuntu1_amd64.deb](https://launchpad.net/ubuntu/+source/gst-libav1.0/1.8.2-1~ubuntu1/+build/10161238/+files/gstreamer1.0-libav_1.8.2-1~ubuntu1_amd64.deb)

i386
[https://launchpad.net/ubuntu/+source/gst-libav1.0/1.8.2-1~ubuntu1/+build/10161241/+files/gstreamer1.0-libav_1.8.2-1~ubuntu1_i386.deb](https://launchpad.net/ubuntu/+source/gst-libav1.0/1.8.2-1~ubuntu1/+build/10161241/+files/gstreamer1.0-libav_1.8.2-1~ubuntu1_i386.deb)

Download & install with dpkg, Ex.
sudo dpkg -i  /home/doug/Downloads/gstreamer1.0-libav_1.8.2-1~ubuntu1_amd64.deb

---

### Post by lammert-nijhof on 2017-02-04
OK thanks that solved my problem

---

### Post by lammert-nijhof on 2017-02-04
I also blocked further updates of the package [COLOR=#000000]gstreamer1.0-libav using Synaptics and the package menu, because the "software updater" directly installed the wrong version again.[/COLOR]

---

### Post by mc4man on 2017-02-04
New bug filed
[https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1661842](https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1661842)

---

### Post by Donk^^ on 2017-02-05
Thanks for the tip :)

---

