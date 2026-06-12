---
title: "How to prepare images to upload to Youtube"
date: 2013-09-16
forum: Multimedia Software
---

### Post by shantiq on 2013-09-16
to get full ffmpeg functionality install from [here]("https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide")

  &#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;


[U]ONE IMAGE + ONE SOUND FILE
[/U] 
If you have a song or speech file and want to upload

```
time ffmpeg  -loop 1 -r 2 -i INPUT.png -i INPUT.mp3 -c:a copy -c:v libx264 -g 7 -crf 0 -vf scale=-1:720  -preset veryfast -shortest OUTPUT.mkv
```


scale can be 1:1080 if you wish for even higher res
Thanx to FakeOutDoorsman and Temüjin for code


[U]IMAGES TO VIDEO [NO SOUND]
[/U]

Say set of photos from your camera


```
time ffmpeg  -r 1/15 -pattern_type glob -i '*.JPG' -s 1640x1230 -c:v libx264  OUTPUT.mkv
```

if png needs one extra command 

```
time ffmpeg  -r 1/15 -pattern_type glob -i '*.png' -s 1640x1230 -c:v libx264  [COLOR=#000000]-pix_fmt yuv420p[/COLOR] OUTPUT.mkv
```
  

will display new image every 15 seconds ; change ratio to suit you  [1/5 , 1/22 etc...] ; can also change -s to the size you wish for
[extra info]("https://trac.ffmpeg.org/wiki/Create%20a%20video%20slideshow%20from%20images")


[B]ps    All your pictures need be the same size and format to work   if they are not run this first


[/B]> for f in *.png; do convert "$f" -resize  2700x2500 -background black -compose Copy -gravity center -extent 2700x2500  "${f%.png}.png"; done 



---

