---
title: "Converting an AVI video clip to MPEG4 or anything else"
date: 2010-12-28
forum: Multimedia Software
---

### Post by tweedmeister on 2010-12-28
Somebody gave me a DVD of my little music group, and I used a Ubuntu application to edit out two clips (I think I used Avidimux--it was about a year ago). It produced a clip in AVI format, which is not accepted by anything. I'd like to upload it to my Facebook or even YouTube, but need to convert it. I've tried about everything, but have had no success. I just downloaded WinFF and tried that. The conversion window produce a lot of information ending with "Unknown encoder 'libx264'," whatever that means. 

Does anyone know how I would convert a clip from AVI to MPEG4? It's driving me nuts. Thanks.

---

### Post by MooPi on 2010-12-28
Install ffmpeg first ```
sudo apt-get install ffmpeg
```
Then in terminal
```
ffmpeg -i input.avi -target ntsc-dvd -aspect 16:9 final.mpg
```
input.avi is your file 
ntsc-dvd isn't necessary but it's nice if you ever want to write to dvd
aspect 16:9 gives you wide screen capabilities
Each of these can be omitted but I find they give you a versatile end .mpg file.

---

### Post by tweedmeister on 2010-12-28
Tried that. What happened was that I got an error message saying that my .avi file was not found in my directory. I've tried calling it file_name.avi and simply file_name (since it does not show up with an actual extension in its folder--it says it's an avi file only when you click on preferences).

---

