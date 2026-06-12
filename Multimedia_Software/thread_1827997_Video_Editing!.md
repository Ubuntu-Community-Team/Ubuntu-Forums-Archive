---
title: "Video Editing!"
date: 2011-08-18
forum: Multimedia Software
---

### Post by Partian on 2011-08-18
So I have just recorded a tutorial using RecordMyDesktop 'Desktop Recorder' and it saves as a .ogg file which is fine HOWEVER
whenever I tried to edit my tutorial it speeds up ALOT.
I have used KDEnlive
Problem:
The audio and video is not sync sometimes the video is sped up.

Kino:
Problem:
It speeds UP alot, and their is no way of letting me change it, even the Sampler won't let me fix it.
The audio when editing does NOT work, I have played the tutorial back to me and their is sound (my microphone)

Any suggestions on WHY this is happening to both video editing software?

---

### Post by labinnsw on 2011-08-20
No idea, but I have found Openshot to be the most usable video editor on Linux.

---

### Post by handy on 2011-08-20
There has been a LOT of praise for Openshot of late, it may well be worth looking at.

If you want the most powerful (steeper learning curve) open-source editing/compositing software available then Cinelerra is it:

[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

---

### Post by darkdragn on 2011-08-20
At one point in time I used Record MyDesktop as well... however it has a few short comings and isn't regualrly maintained. To over come the same syncing issues you're having, I switched over to doing it by hand with good old fashioned ffmpeg. It's actually really easy to do with ffmpeg:
 
```
 
xwininfo

```
Then click on the window you want to record, and from the output get the top left corner, and the size. Enter the size after the -s below, and the corner after the :0.0+ and that is about it:
```
 
ffmpeg -r 24000/1001 -s 360x240 -i :0.0+2,64 -f alsa -ac 2 -i pulse -vcodec xvid -vb 500k -r 24000/1001 -s 360x240 -ac 2 -ab 96k output.avi

```
 
That's if you're working with the basic ffmpeg install, I have libx264 on mine, so I usually use -vcodec libx264 -vpre baseline and output to a mp4. OH! Another thing, if you do that and get no audio, then pop open 'pavucontrol' and make sure that pulse has your mic on, and the ffmpeg recording stream is assigned to internal audio. Enjoy, and I hope it works well for you! ^_^

---

