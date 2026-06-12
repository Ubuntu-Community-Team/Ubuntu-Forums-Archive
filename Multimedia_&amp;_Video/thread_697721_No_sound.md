---
title: "No sound"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by Fistols on 2008-02-15
Hi, I dont get sound at all on my laptop with Gutsy, I thought I did get sound when I logged in, but we were playing around with Festival in one of my classes and I wanted to put it on my laptop, and I dont hear any sound. So I installed banshee and connected to a radio station to try and test if I had sound at all, and I got nothing. Please let me know if you have any ideas.
-Derek

---

### Post by Giannis68 on 2008-02-15
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2

For **i386**, the package is called **w32codecs**: 
sudo apt-get install w32codecs
 For **amd64**, the package is called **w64codecs**:
sudo apt-get install w64codecs

---

### Post by Fistols on 2008-02-15
That didnt work, I went to the page and tried everything as well.

---

### Post by Giannis68 on 2008-02-17
run aplay -l to get list about your soundcard
if success run alsamixer increase sound volume unmute channels 
**sudo apt-get update && sudo apt-get install alsa-oss**
banshee needs to install
sudo apt-get install gstreamer0.10-plugins-base \
    gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly \
    gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly-multiverse \
    gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg \
    gstreamer0.10-fluendo-mp3

---

### Post by Fistols on 2008-02-18
I still get nothing... Is there something I needed to do when I first installed Ubuntu?

---

