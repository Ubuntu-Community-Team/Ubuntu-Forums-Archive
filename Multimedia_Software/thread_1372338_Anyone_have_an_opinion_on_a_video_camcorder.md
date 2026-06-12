---
title: "Anyone have an opinion on a video camcorder?"
date: 2010-01-04
forum: Multimedia Software
---

### Post by whiskeylover on 2010-01-04
I am in the market for a video camera, with HD capabilities. I am also inclined towards flash rather than HDD. I'm eying the Canon HF S10 at the moment.

Its got 1080p video output, 10x optical zoom (a bit less that what I'd like), and AVCHD video format. 

I should be able to download files easily, and be able to edit them easily too (with or without commercial software.)

Anybody's got any opinions?

---

### Post by whiskeylover on 2010-01-04
Can a mod move this to the multimedia forum?

---

### Post by LowSky on 2010-01-04
Samsung makes great HD cams that are Linux file friendly

[http://www.newegg.com/Product/Product.aspx?Item=N82E16830144208](http://www.newegg.com/Product/Product.aspx?Item=N82E16830144208)

---

### Post by whiskeylover on 2010-01-05
Thanks for your reply.

Any other suggestions?

---

### Post by RedRat on 2010-01-05
I have a Canon Vixia HV30, got it last year so the model number may have changed, and it works via a 1394 (FireWire port). I can download from the camera to Linux (I am using 8.04) and use the command line. The video files are in a .m2t format. The camera uses tape, so that may be why I am stuck with command line.

Editing is another problem, at least for me using 8.04, in that editing software from my distro has not fully updated to HD video. This might be solved for 9.10 users. I will be switching in a few month to 10.04 and hopefully things will be improved.

---

### Post by altonbr on 2010-01-05
I've had nothing but problems with my Panasonic HDC-SD9. It creates video in MTS/AVCHD file format (which has the ability to be [transcoded via Linux]("http://www.fsckin.com/2008/01/03/transcoding-mtsm2ts-avchd-video-files-with-free-software/"), but it's not the easiest procedure). Also, I thought it'd be nice to have a HD video camera that uses SD cards, but with an 8GB card, I can only get 1hr of shooting in, which isn't much when you're video taping sports or any major family events. Lastly, it has no add-on features, such as microphone inputs or headphone jacks. It really is quite the "point-and-shoot" type of video camera and I really wish I researched it more because it cost me about $500 CDN.

Just make sure you take all of those into consideration before buying your next video camera.

---

### Post by cotcot on 2010-01-05
I avoided a HDD because of the noise of the disk. HDD needs a bigger battery.

Check stuttering of the video during fast panning. I needed to learn how the use my camera to avoid/limit stuttering due to panning. (avoid to much zooming of fast objects; follow the object rather than heaving a fixed view point with the object moving from left to right; time preset choice to 1/50). I guess that there are small difference between the different cameras on this subject.

---

### Post by whiskeylover on 2010-01-05
I ordered the Cannon HF S10 online and picked it up from the store today. So far I'm really happy with it. I have yet to play with it in daylight. Low light videos on this camera are known to suck.

Thanks for the responses everyone. These responses and a ton of research on features and reviews helped me come to this decision.

---

### Post by altonbr on 2010-01-07
> **whiskeylover said:**
> I ordered the Cannon HF S10 online and picked it up from the store today. So far I'm really happy with it. I have yet to play with it in daylight. Low light videos on this camera are known to suck.

Thanks for the responses everyone. These responses and a ton of research on features and reviews helped me come to this decision.

If you figure out a good way to use, edit, convert, whatever the AVCHD/.MTS format that all these new cameras are making, let me know!!

Pitivi in their PPA can handle MTS which is nice, but I don't know any way to batch convert MTS to something usable or watchable yet.

---

### Post by whiskeylover on 2010-01-07
I haven't explored importing and editing videos yet. But if I find something useful, I will post it here.

---

### Post by cotcot on 2010-01-09
> **altonbr said:**
> 
Pitivi in their PPA can handle MTS which is nice, but I don't know any way to batch convert MTS to something usable or watchable yet.

I convert the .MTS files from my Canon HF100 in batch with one of these instructions in terminal (terminal started from the folder with the .MTS) :
```
find ~/encode -name '*.MTS' -type f -exec mencoder '{}' -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o '{}'.mpg \;
```

or 
```
for f in *.MTS; do  mencoder “$f” -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o "${f%.MTS}.mpg"; done
```

---

### Post by derekeverett on 2010-01-09
I can tell you from experience with 2 cams.. that JVC are fairly easy to use but have major focus issues. The color seems to be a little wonky too. 

With Ubuntu, the only way I could play the files was to change the extension of the files from .mod to .mpg - thought I could pony up that little bit of advice just in case...

The Windows software it comes with works well in Windows though, and imovie on the mac deals with the native file type no problem. But like I said earlier... focus coming in and out can be an issue.

---

### Post by altonbr on 2010-01-10
> **cotcot said:**
> I convert the .MTS files from my Canon HF100 in batch with one of these instructions in terminal (terminal started from the folder with the .MTS) :
```
find ~/encode -name '*.MTS' -type f -exec mencoder '{}' -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o '{}'.mpg \;
```

or 
```
for f in *.MTS; do  mencoder “$f” -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o "${f%.MTS}.mpg"; done
```

This is wonderful, thank you! I'll tell you my results!

---

