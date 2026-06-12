---
title: "Problem in playing the bin extension ? any help?"
date: 2008-06-15
forum: Multimedia Software
---

### Post by elord on 2008-06-15
Good day to all i have this problem in playing a bin extension in any application here.. i downloaded a VTC tutorial video for UBUNTU and i found out that some of the player like totem and mplayer can't support it..

i tried this site at youtube.com [http://www.youtube.com/watch?v=E8VmernM4qM](http://www.youtube.com/watch?v=E8VmernM4qM)
follow the step but i got this problem...

elord@elord-desktop:~/Documents/VTC/nsid-vtcu.r00_FILES$ sudo ./nsid-vtc.ubuntu.bin
./nsid-vtc.ubuntu.bin: 1: Syntax error: "&" unexpected (expecting ")")

but when i downloaded the googleearth and it runs really good.

hope anyone can help me with this problemm

MORE POWER to all and to UBUNTU..

---

### Post by Joeb454 on 2008-06-15
.bin files aren't video files :confused:

Or am I missing the point?

---

### Post by elord on 2008-06-15
same here i don't know i try to install divx in my wine but it come up with errors.. is there any DIVX for Ubuntu linux?

---

### Post by elord on 2008-06-15
i got this DIVX for linux at this site..[http://www.digital-digest.com/software/download.php?sid=1024&ssid=0&did=1](http://www.digital-digest.com/software/download.php?sid=1024&ssid=0&did=1) 

when i finished the download and extract the folde.. using the command sudo apt-get install divx i got this problem..

elord@elord-desktop:~/Desktop$ sudo apt-get install divx for linux
[sudo] password for elord:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package divx

hmmmmmmmm

---

### Post by elord on 2008-06-15
after extracting the file.. i read the installation procedure and found out that i have to use the command in the terminal and type ./install.sh 

here is the link where i downloaded the divx..

[http://www.divx-digest.com/software/divxcodec_linux.html#comments](http://www.divx-digest.com/software/divxcodec_linux.html#comments)

---

### Post by SimoneB on 2008-06-15
The tutorial in the first post is for installing google earth, so it could not work with your program. What is that you're trying to install?

Also, "DivX for Linux" looks like a video CODEC, not a video player. If you need a player, just use Totem or install VLC.

---

### Post by elord on 2008-06-15
yah.. i install the VLC but same problems occur..it can't play the video... any help or any idea? i appreciate it .,.

here is the link where i found the Video Tutorial... [www.vtc.com](www.vtc.com) then search UBuntu..by using the transmission i downloaded it in [www.seedpeer.com](www.seedpeer.com).. it's been 2 weeks now im desperate in searching for the player to play the video.. VLC and TOTEm can't play the video

---

### Post by elord on 2008-07-16
finally the problems is solve already.,.

---

### Post by forger on 2008-07-16
... for video codecs
1) install the repostitory at [www.medibuntu.org](www.medibuntu.org) ( [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) )
2) enable **universe** and **multiverse** from System > Administration > Software Sources, then click Close and Reload.


for ubuntu hardy heron 8.04.1 this is the solution, open a Applications > Accessories > Terminal and do:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install w32codecs libdvdcss2 libdvdread3
sudo apt-get install lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x gstreamer0.10-fluendo-mp3 libxine1-all-plugins
```

---

