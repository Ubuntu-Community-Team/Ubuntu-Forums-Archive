---
title: "[SOLVED] FYI - Motion, webcam, and cpu pegged"
date: 2008-11-28
forum: Multimedia Software
---

### Post by andguent on 2008-11-28
Hello all,

This post was originally to ask for help, but I figured it out. Instead, I'm going to post a small bit of info about what I accomplished.

I have a (046d:08d7) Logitech QuickCam Communicate STX hooked up to an Ubuntu Server (Dapper actually). I'm attempting to set the camera up to be viewable via webpage with a VERY low framerate (1 frame every 3 seconds is fine). I do not need any images recorded.

Everywhere I read, the package 'motion' is recommended for turning USB webcams into security cameras. However I didn't need video, recording, or notifying of movement. I was able to get motion setup fairly easily, but when viewing the camera from other machines, it caused both Hardy boxes and WinXP boxes to peg the CPU and usually freeze Firefox.

How I got it working was using a package creatively named 'webcam'. I already had apache installed and working which helped. Now I can view [http://SERVER_IP/cams/webcam.jpeg](http://SERVER_IP/cams/webcam.jpeg) and I can see my image. A little bit of html work later using meta refresh and I'm done.

I'm sure there are a thousand other ways to do it, but it works for me.

Here are my configs and other key files:

~/.webcamrc
```

[grab]
device = /dev/video0
text = webcam %Y-%m-%d %H:%M:%S
fg_red = 255
fg_green = 255
fg_blue = 255
width = 320
height = 240
delay = 3
wait = 0
rotate = 0
top = 0
left = 0
bottom = -1
right = -1
quality = 75
trigger = 0
once = 0

[ftp]
host = www
user = webcam
pass = xxxxxx
dir  = /var/www/cams/
file = webcam.jpeg
tmp  = uploading.jpeg
passive = 1
debug = 0
auto = 0
local = 1
ssh = 0

```

webcam-refresh-on.html 
```

<html>
<title>
	Camera
</title>
<meta http-equiv="refresh" content="3" />
<body>
<img src=webcam.jpeg>
<br>
<br>
Auto refresh: [ON] <a href="webcam-refresh-off.html">[OFF]</a>

</body>

```

webcam-refresh-off.html 
```

<html>
<title>
	Camera
</title>
<body>
<img src=webcam.jpeg>
<br>
<br>
Auto refresh: <a href="webcam-refresh-on.html">[ON]</a> [OFF]

</body>

```

---

