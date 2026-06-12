---
title: "fuzemux not working"
date: 2011-01-10
forum: Multimedia Software
---

### Post by mike2434 on 2011-01-10
So i just got a sansa fuze and it works great with ubuntu lucid. the fuze however only plays mp4 videos. i have a video thats in avi and im trying to convert it to mp4 and came across fuzemux in the software center which is supposed to do just that. my problem is that is says in synaptic and the software center that its installed. but its nowhere to be found. any suggestions? thanks in advance.

---

### Post by mike2434 on 2011-01-10
guessing no one has used this before ? lol

---

### Post by Whitefall on 2011-01-11
Fuzemux does only a part of the conversion. You first have to convert the video using ffmpeg or mencoder to have the correct resolution, frame rate, codec settings, bitrate etc. There is an example mencoder call in [http://code.google.com/p/fuzemux/wiki/MencoderBatchFile](http://code.google.com/p/fuzemux/wiki/MencoderBatchFile):
```
mencoder -ovc lavc -oac mp3lame -ffourcc DX50 \
        -ofps 20 -noskiplimit -vf pp=li,expand=:::::224/176,scale=224:176 \
        -lavcopts vcodec=mpeg4:vqscale=3:vmax_b_frames=0:keyint=15 \
        -srate 44100 -af resample=44100:0:1,format=s16le \
        -lameopts cbr:br=128 \
        -o outputfile.avi inputfile.avi -msglevel mencoder=1 
```


Afterwards, you can run the result through fuzemux. This is necessary since the Sansa Fuze requires a very specific AVI format that mencoder cannot create by itself.

There is also a GUI application that does  everything automatically: [http://code.google.com/p/video4fuze/](http://code.google.com/p/video4fuze/)

---

