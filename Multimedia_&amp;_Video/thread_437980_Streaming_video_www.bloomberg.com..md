---
title: "Streaming video www.bloomberg.com."
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by hfe on 2007-05-09
Hello, 

I have been trying to play streaming video with mixed success. Some sites work perfectly and some don't. 

My question here is if someone has managed to get the live tv from bloomberg.com ([http://www.bloomberg.com/avp/avp.htm?clipSRC=LiveBTV#](http://www.bloomberg.com/avp/avp.htm?clipSRC=LiveBTV#)) to work? I sometimes manage to get a bad quality video stream to work (without desktop effects) but the sound refuses to work. 

Thank you in advance, for any pointers in the right direction. 

Regards, 
hfe

---

### Post by amlucent23 on 2007-05-09
do the videos at cnn.com work for you? they have never worked for me.

---

### Post by hfe on 2007-05-09
Hello again, 

[http://edition.cnn.com/video/](http://edition.cnn.com/video/) works fine, and the media player that I am using is mplayer with mplayer firefox plugin. It seems like bloomberg is using the audio codec 0xa for which I have not been able to find any support in linux. =/ The error I get from bloomberg when trying to play the stream with mplayer (to be more specific) is "Cannot find codec audio format 0xa", which is a windows media player audio format (I suspect). So hopefully there is support for it somewhere in some program in ubuntu. I just need to find out if and where. 

Regards, 
hfe

---

### Post by hfe on 2007-05-10
Hello! 

Problem solved. =) 

Solution: 
Use mplayer with the mozilla-mplayer plugin (optional but convenient). 
Then add the w32codecs. I was tricked by the gstreamer codecs that you can add by going to Add/Remove Applications in the graphical menu, but that wont work, so do this: 

1. gedit /etc/apt/sources.list

2. enter these two lines and save your file: 

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

3. sudo apt-get update. 

4. wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- > key.txt

5. sudo apt-key add key.txt. 

6. sudo apt-get update. 

7. sudo apt-get install w32codecs libdvdcss2. 

There you go! Now, what tricked me with bloomber is that the uk version seems to be optimized for a 56k connection, which is worthless, the quality is horrible. If you want decent quality use the US version. 

Hope this helps someone. 

Regards, 
hfe

---

### Post by SuperGuest on 2008-02-03
Hi 


I was trying to resolve the no-sound problem on Bloomberg TV when using MPlayer as well. I followed the instructions and encountered a roadblock on the following step:
sudo apt-get install w32codecs

The response is as follows. I tried numerous searches on the net on this "Package w32codecs is not available" issue but could not get any good solutions. I recall having installed this w32codecs before as I has followed the instructions here ([http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)) before to setup my browser.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I also try using MediaPlayerConnectivity Add-On on my browser but to no results. And I am running Ubuntu 7.10 on an AMD64. Greatly appreciate some help.

Thanks!
- newbie -

---

### Post by RomeReactor on 2008-02-03
Hi. You need to add the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu") to your software sources in order to install w32codecs. Or download the [w32codecs package]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu0.7.04.1_i386.deb") and double click on it to install. Note that if you don't add the Medibuntu repository you won't get software updates for w32codecs through the Update Manager.

---

### Post by AgentZ86 on 2008-06-28
Hi all, 
How do I add the Medibuntu repository to my software sources so that the sources will work via install Applications Add/Remove

I installed Mplayer to try and get bloomberg.com tv to work, but it does not play anything. I've fooled with the Mplayer setting to get it working but I think I'm missing something

I'm using 8.04 fully updated.

Anyhelp would be great.
Thanks

---

