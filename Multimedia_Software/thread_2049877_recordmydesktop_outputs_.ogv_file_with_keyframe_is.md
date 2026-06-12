---
title: "recordmydesktop outputs .ogv file with keyframe issues"
date: 2012-08-29
forum: Multimedia Software
---

### Post by rowntreerob on 2012-08-29
this is a bug possibly related to [here]("http://ffmpeg.org/pipermail/ffmpeg-user/2012-February/005117.html")

recreate bug:

create .ogv file with recordmydesktop

use it in an ffmpeg step like:

 ffmpeg -vol 512 -i orig.ogv new.ogv

stdout with lots of bad keyframes ...
```


[ogg @ 0x3797260] Broken file, non-keyframe not correctly marked.
Broken file, non-keyframe not correctly marked.00:05:06.88 bitrate= 301.1kbits/s dup=3872 drop=0    
[ogg @ 0x3797260] Broken file, non-keyframe not correctly marked.
Broken file, non-keyframe not correctly marked.00:05:11.37 bitrate= 297.2kbits/s dup=3936 drop=0    
Broken file, non-keyframe not correctly marked.00:05:11.48 bitrate= 301.3kbits/s dup=3995 drop=0    
[ogg @ 0x3797260] Broken file, non-keyframe not correctly marked.
    Last message repeated 1 times
Broken file, non-keyframe not correctly marked.00:05:15.66 bitrate= 302.4kbits/s dup=4055 drop=0    
[ogg @ 0x3797260] Broken file, non-keyframe not correctly marked.
Broken file, non-keyframe not correctly marked.00:05:19.63 bitrate= 302.6kbits/s dup=4111 drop=0    
Broken file, non-keyframe not correctly marked.00:05:23.91 bitrate= 302.6kbits/s dup=4133 drop=0    
[ogg @ 0x3797260] Broken file, non-keyframe not correctly marked.
    Last message repeated 1 times
Broken file, non-keyframe not correctly marked.00:05:28.20 bitrate= 303.1kbits/s dup=4238 drop=0    
[ogg @ 0x3797260] Broken file, non-keyframe not correctly marked.
Broken file, non-keyframe not correctly marked.00:05:36.97 bitrate= 299.0kbits/s dup=4285 drop=0    
[ogg @ 0x3797260] Broken file, non-keyframe not correctly marked.
Broken file, non-keyframe not correctly marked.00:05:41.26 bitrate= 299.5kbits/s dup=4388 drop=0    
Broken file, non-keyframe not correctly marked.00:05:41.26 bitrate= 303.7kbits/s dup=4422 drop=0    
[ogg @ 0x3797260] Broken file, non-keyframe not correctly marked.
frame= 5224 fps= 89 q=0.0 Lsize=   13204kB time=00:05:48.26 bitrate= 310.6kbits/s dup=4576 drop=0    
video:8514kB audio:4604kB subtitle:0 global headers:3kB muxing overhead 0.632708%
```

---

### Post by FakeOutdoorsman on 2012-08-29
Can you provide a sample file? Can you provide the complete ffmpeg console output (including version/config headers, etc.)? What version of Ubuntu are you using?

---

