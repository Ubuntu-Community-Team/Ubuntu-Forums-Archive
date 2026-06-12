---
title: "possible to resize screen capture in realtime with ffmpeg?"
date: 2011-07-25
forum: Multimedia Software
---

### Post by greenbag on 2011-07-25
As the title says, I'm looking for a command to resize on the fly as I capture. My desktop's 1680x1050, but I want to shrink down to say 1280x720.. or other.

So far my command is:

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1680x1050 -i :0.0 -acodec pcm_s16le -vcodec rawvideo -threads 0 output.avi
```

Is there a resize switch I can add? If not, can someone suggest something.. other than resizing after?


Thanks...........

---

### Post by greenbag on 2011-07-25
got it.......


> from ffmpeg-doc.html



15.17 scale

 Scale the input video to width:height and/or convert the image format. 

 For example the command: 
./ffmpeg -i in.avi -vf "scale=200:100" out.avi

 will scale the input video to a size of 200x100. 

 If the input image format is different from the format requested by the next filter, the scale filter will convert the input to the requested format. 

 If the value for width or height is 0, the respective input size is used for the output. 

 If the value for width or height is -1, the scale filter will use, for the respective output size, a value that maintains the aspect ratio of the input image. 

 The default value of width and height is 0.


```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1680x1050 -i :0.0 -acodec pcm_s16le -vcodec rawvideo -threads 0 [color="red"]-vf "scale=1280:720"[/color] /home/greenbag/Captures/output.avi
```



All good :)



Cheers...............

---

