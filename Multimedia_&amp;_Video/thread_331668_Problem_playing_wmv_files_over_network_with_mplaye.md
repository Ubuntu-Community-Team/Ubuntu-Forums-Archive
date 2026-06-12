---
title: "Problem playing wmv files over network with mplayer"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by ctaskiran on 2007-01-04
Hi,

I have a problem with playing WMV files from certain sources using mplayer (1.0rc1-4.1.2). For example I can play 
  [http://www.addict3d.org/videos/rgs-ilovesky.wmv](http://www.addict3d.org/videos/rgs-ilovesky.wmv)
with no problem, but when I try to play 
  [http://wmscnn.stream.aol.com/cnn/world/2007/01/03/doane.india.skeleton.cnn.ws.wmv](http://wmscnn.stream.aol.com/cnn/world/2007/01/03/doane.india.skeleton.cnn.ws.wmv)
(a video from cnn.com) I get the error message "Ahhhh, stream_chunck size is too small: 4"

My questions are:
1. Can anyone play the second URL?
2. I have tried VLC (0.8.6 ), Xine, and Kaffeine. All fail on the second URL. Is there any other program I can use?

Thanks a lot!

Cuneyt

---

### Post by pay on 2007-01-04
Try ```
sudo aptitude install w32codecs
```and then see if mplayer will play it.

---

### Post by ctaskiran on 2007-01-04
I had already installed some win codecs. I still tried the command you suggested and got:

$ sudo aptitude install w32codecs
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for w32codecs
The following packages have been automatically kept back:
  libnspr4 libnss3
The following packages have been kept back:
  firefox w3m
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Can you play the second file with your set up? This would be very helpful to know. 

Thanks,

Cuneyt

---

### Post by pay on 2007-01-04
You need to enable the repository that win32codecs is from. I think that it is the universe repository. I can't test if the file will play on my setup because I'm not on Ubuntu right now (I kinda stuffed it up).

---

