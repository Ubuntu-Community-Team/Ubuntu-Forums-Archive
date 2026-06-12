---
title: "ffmpeg converting series of .pngs into .mp4 change of colours."
date: 2018-10-03
forum: Multimedia Software
---

### Post by Silneus on 2018-10-03
Hi,

I use :
    
    ```
ffmpeg -r 1/2 -i 7A%03d.png -pix_fmt yuv420p out.mp4
```

(Ubuntu 16.04, ffmpeg version 2.8.15-0ubuntu0.16.04.1)

to convert series of images into .mp4 clip. Everything works fine apart from the fact that ffmpeg is changing the colors of output video:

PNG:
[https://ibb.co/m6Lyoe](https://ibb.co/m6Lyoe)

MP4:
[https://ibb.co/ewndoe](https://ibb.co/ewndoe)


How could I keep the original colors in output clip.

Cheers

[EDIT]

I have found it was player related:

-Totem plays video clip correctly, nbut with changed colors
-VLC shows proper colors but the first frame is frozen for the entire length of video
-Parole plays video correctly with right colours 

Is there a way to convert the images to video that could be played correctly with every player?

---

