---
title: "Capture with avconv : Trouble in color"
date: 2014-02-16
forum: Multimedia Software
---

### Post by Yobogs on 2014-02-16
Hello,

I try to capture part of my screen with avconv.

I use this commande (it's part of python script) :
avconv -y -f x11grab -s {width}x{height} -r {fps} -i {display}+{x},{y} -vcodec libx264 -pre lossless_ultrafast -i ./static/generatevideo/Metrage/{music}.mp3 -b 10000k -threads 0 {fname}

I have a trouble with a quality of color :
[IMG]http://www.mutuelle-assistance.com/color.jpg[/IMG]
The first is the original, the second is my capture.

Anyone have an idea how i can improve the quality color of my capture ?

Thanks for your help

---

