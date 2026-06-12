---
title: "enabling multimedia on ubuntu feisty without an internet"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by rathipriya on 2007-08-24
new ubuntu user here. can  enyone tell me how to enable multimedia in ubuntu feisty without an internet connection. plz reply quickly as possible.

---

### Post by Hugolp on 2007-08-24
If that computer doesnt have internet youll have to go to a computer with internet (a friend, a internet public computer, ...) and dowload the gstreamer deb files. Copy those files in a cd or external hard drive (or anything you use) and copy the deb files in you computer. Once they are there just double click them and they will install automatically.

I dont know what exact modules and dependencies you have to download but I know its about gstreamer, so you can search that at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) .

You can also check [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) .

Hugo

---

### Post by ajgreeny on 2007-08-24
If you have a friend with ubuntu (or other debian based OS) it could be even easier to use aptoncd.  Get this on the other machine and then use it to create a repository on CD which can be used on your machine to install packages.

---

### Post by Scorpuk on 2007-08-24
Can you use aptoncd if they are using 32bit and you are using 64bit?

---

### Post by ajgreeny on 2007-08-24
No, sorry, but I doubt that you can.  Unless you can get them to download the packages for you and use them as a completely separate activity to their own updating and installing.

---

### Post by Scorpuk on 2007-08-24
Ahh okies.


If I goto [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and download by tge link for AMD64 will that download all I need or do I need to goto every link on each page for a package to get everything?

ie:

Looking for multimedia playback I would go for gstreamer plugins etc. So for an example this one:

[http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-bad-multiverse](http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-bad-multiverse)

At the bottom there is a link to AMD64 .deb download. Any idea if this will get all the dependencies?


Not important, just built my server while away from home so wont get internet access until next weekend, but would like to at least try out mp3 playback. :-)


Tnx in advance.

---

### Post by Scorpuk on 2007-08-25
Tried it last night and just downlaoding the deb packages did not include all the dependencies.


Oh well :(

---

