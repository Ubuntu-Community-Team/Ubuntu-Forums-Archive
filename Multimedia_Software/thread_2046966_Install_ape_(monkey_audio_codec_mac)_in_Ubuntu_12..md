---
title: "Install ape (monkey audio codec mac) in Ubuntu 12.04"
date: 2012-08-23
forum: Multimedia Software
---

### Post by Acharn on 2012-08-23
I downloaded a music torrent, and what I got was a folder with cover art and a .ape and a .cue file. I've been looking for ways to extract the separate tracks from the .ape file, and all the posts I've been able to find (for Linux, Windows seems to be easy) require installation of the 'mac' codec. Problem is, the only place I've been able to find this is in a .deb file at [http://ubuntuforums.org/attachment.php?attachmentid=162759&d=1278575963](http://ubuntuforums.org/attachment.php?attachmentid=162759&d=1278575963). Unfortunately, when I try to install that package, dpkg tells me the version string does not start with a numeral, so the package is broken. I've tried to install through the Ubuntu Software Center and using apt-get, but no joy.

Can anybody help me out here? How can I get the 'mac' package? Has it been discontinued? Is there any other way to extract .flac files from a .ape file? I don't have any problem playing .flac files in Rhythmbox, Banshee, Exaile, Movie Player, SMPlayer or VLC Player, so what am I missing?

---

### Post by shantiq on 2012-08-24
Acharn to do this task you can use flacon which is in repo

```
sudo apt-get install flacon
```


it will pull down a correct version of mac    [which will also be picked up by the system]



once installed go to cue file /right-click /open with/ pick flacon and choose format you want to separate tracks into:KS

---

### Post by Acharn on 2012-08-24
Errrmmm... What is this repo of which you speak?
```
roger@roger-Aspire-M1610:~$ sudo apt-get install flacon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package flacon
```

---

### Post by Acharn on 2012-08-25
OK, I must write on the whiteboard 100 times, "Google is your friend." Given the name of the program I found instructions on how to install it at [http://www.webupd8.org/2011/12/lossless-audio-split-tools-updates.html](http://www.webupd8.org/2011/12/lossless-audio-split-tools-updates.html), the WebUpD8 site. I really like that site -- it has so much neat stuff, it's a shame that 99% of it doesn't apply to my interests. Thanks Shantiq. Worked great, did exactly what I wanted.

---

### Post by shantiq on 2012-08-25
sorry acharn   it is in repo on 12.04    maybe not earlier    not sure there


anyway you got there:KS


so for other guys who might visit

> sudo add-apt-repository ppa:flacon/ppa  
sudo apt-get update
sudo apt-get install flacon

---

