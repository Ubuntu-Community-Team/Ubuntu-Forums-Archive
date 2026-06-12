---
title: "Cyclic Redundancy Check"
date: 2009-02-24
forum: Multimedia Software
---

### Post by Config122 on 2009-02-24
I am trying to rip a dvd (dark knight-css protected) using mencoder , but everytime I am getting
~error at resampling
~crc error..

Can anyone help me out of this???
I am using the below command..

mencoder dvdnav://1 -dvd-device g: -of lavf -lavfopts format=flv -ovc lavc -lavcopts vcodec=flv:vmax_b_frames=0:vbitrate=1000 -oac mp3lame -ofps 15 -srate 44100 -channels 2 -noskip -mc 0 -nocache -o "D:\dark_knight.flv"

---

