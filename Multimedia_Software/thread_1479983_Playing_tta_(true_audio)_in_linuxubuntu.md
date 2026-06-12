---
title: "Playing tta (true audio) in linux/ubuntu"
date: 2010-05-11
forum: Multimedia Software
---

### Post by shantiq on 2010-05-11
[COLOR="brown"][B][COLOR="Blue"]In case you were wondering

&#9829; you can play tta in both xmms and qmmp (both supporting cuefile)
&#9829; also in xmms2 and aqualung (natively but no cuefile)
[/COLOR]



1 for xmms you need a plugin 
it is found here    **both plugins also attached**


to install ttaenc    no configure   just make and sudo make install



Download

 [TTA plug-in version 1.2 for XMMS]("http://www.hqshare.net/redirector.php?url=http%3A%2F%2Fprdownloads.sourceforge.net%2Ftta%2Fttaplugin-xmms-1.2.tgz%3Fdownload") (Linux x86)
[TTA plug-in version 1.2 for XMMS]("http://www.hqshare.net/redirector.php?url=http%3A%2F%2Fprdownloads.sourceforge.net%2Ftta%2Fttaplugin-xmms-1.2-src.tgz%3Fdownload") (Source Code)


extract the file named libxmms-tta.so and put into your home/.xmms/plugin folder


2 for qmmp go into settings/plugins/click on FFmpeg Plugin/click on preferences/tick true audio

it is really well hidden i had to write to the designer to find it


the true audio main site is [here]("http://www.hqshare.net/redirector.php?url=http%3A%2F%2Ftrue-audio.com%2FFree_Downloads")


i found installing tta on linux a bit tricky at first but simple with those instructions

i also wrote to the guy who maintains true audio

he gave me [this source file link]("http://www.hqshare.net/redirector.php?url=http%3A%2F%2Fsourceforge.net%2Fprojects%2Ftta%2Ffiles%2Ftta%2Fttaenc-src%2Fttaenc-3.4.1-src.tgz%2Fdownload")

the folder's name is ttaenc-3.4.1-src 



no need for
Code:
```
./configure
```
but instead 

Code:
```
$ su -
# cd /(your work dir)/ttaenc-3.4.1-src
# make; make install
```
well on ubuntu it worked with 


Code:
```
$ cd ./ttaenc-3.4.1-src
$ make 
$ make install
```
then run ttaenc in terminal and there you have it 


ps the manual is in the read file in the ttaenc-3.4.1-src folder ( no man ttaenc in the terminal)




[/B][/COLOR]

---

