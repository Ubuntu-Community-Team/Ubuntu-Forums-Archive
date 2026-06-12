---
title: "jpeg top mpeg renderproblem"
date: 2010-05-16
forum: Multimedia Software
---

### Post by cotcot on 2010-05-16
I want to include pictures in a video project. Importing the pictures in the VSE and adapting the number of frames to show is no problem. After rendering (default ffmpeg HD or PAL DVD) the rendered video does not give a stable play back. On some pictures you see the playback alternating switching between 2 x the same image but very slightly shifted from each other with a frequency of about half a second. Especially the green from trees and so seem to be subject of this phenomenon.
It does not seem to be an (de)interlace issue.
The same picture rendered to mpeg with other editors give no problem. I have tried Pitivi (however with theora) and cinelerra. (kdenlive failed in the rendering and openshot did not find the codecs)

This is a copy of a post on the blenderartist forum because I saw that it is more an ffmpeg issue than a blender VSE issue. I have tried different ffmpeg versions under 9.04 and 10.04. 

I can repeat the problem using this command :```
ffmpeg -loop_input -f image2  -i IMG_3391.JPG -r 24000/1001 -qmin 2 -vframes 50 -s hd1080 -aspect 16:9 -bufsize 1835k -maxrate 9800K -minrate 9000K -b 9000K testffmpeg3.mpg
```

See example here : [http://ubuntuone.com/p/3oc/]("http://ubuntuone.com/p/3oc/")

(The ubuntu one server is giving an internal error at the moment of this post)

---

