---
title: "[howto] AVCHD MTS w/PAFF interlacing to 720p AVI"
date: 2009-06-02
forum: Multimedia Software
---

### Post by kolavar on 2009-06-02
Some digital videocameras record 1920x1080 and 1440x1080 AVCHD in 60i with PAFF interlacing. That type of interlacing is problematic for most video players in the repositories except VLC. It took a while to figure out the quickest and easiest way to get a quality reencode without sacrificing quality or excessive hard drive space. Luckily the hardest part of this process is compiling MPlayer/MEncoder from source.

(Optional) First I got rid of the versions of MPlayer and MEncoder from the repositories:
```
sudo apt-get remove mplayer mencoder
```
Here are the commands I entered to compile from source on Ubuntu 9.04 32-bit:
```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
./configure
make
sudo make install
```
Here's the command to do a quick and dirty reencode:
```
mencoder -fps 60000/1001 [INPUT.MTS] -o [OUTPUT.AVI] -oac copy -vf pp=ci,dsize=1280:720:0 \
-ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=10000:aspect=16/9:threads=2:turbo=1 -ofps 30000/1001
```
Where [INPUT.MTS] is the input video file and [OUTPUT.AVI] is the output. If your source bitrate is higher than 10000, you should change 10000 to a higher value.

(Optional) Get rid of the MPlayer/MEncoder from source and reinstall the versions from the repositories
```
sudo make uninstall
sudo apt-get install mplayer mencoder
```
This should work with most AVCHD videocameras. If your videocamera is a European model, you probably need to change the fps parameter to 50000/1001 and ofps to 25000/1001. I hope this is useful for people having issues with their AVCHD videocameras.

---

