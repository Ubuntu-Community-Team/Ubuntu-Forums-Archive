---
title: "Convert video of Samsung Galaxy S2"
date: 2012-06-26
forum: Multimedia Software
---

### Post by moresun on 2012-06-26
Hi 

I search and tried a lot of settings but this works well to convert videos taken by a Samsung Galaxy S2 cellphone GT-I9100. 
Convert mp4 to avi using xvid

Tweek the data rate for a better and lower quality :-)

```

ffmpeg -i input.mp4  -vcodec mpeg4 -vtag XVID -b 1200k -acodec libmp3lame -ab 128k output.avi
```


On ubuntu 12.04 you may have to install libavcodec to avoid the following problem -->  **Msg: Unknown encoder 'libmp3lame'**
sudo apt-get install ffmpeg libavcodec-extra* 

mencoder provides also nice functions to crate xvid or divx files    
```
mencoder input.mp4 -ovc xvid -xvidencopts bitrate=1200:autoaspect -vf pp=lb -oac mp3lame -lameopts fast:preset=standard -o output.avi
```
```
mencoder input.mp4 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200:mbd=2:v4mv:autoaspect -vf pp=lb -oac mp3lame -lameopts fast:preset=standard 
```

---

