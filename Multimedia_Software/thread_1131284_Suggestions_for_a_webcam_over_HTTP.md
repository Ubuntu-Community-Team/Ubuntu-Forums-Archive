---
title: "Suggestions for a webcam over HTTP"
date: 2009-04-20
forum: Multimedia Software
---

### Post by R.Bucky on 2009-04-20
My wife and have a psychotic cat and want to watch him online when we are at work. I operate a web server at home with a true static ip. I want to embed the feed into a page on my LAMP box. 

What is the best software/hardware combo from user experiences? Not wanting to spend a briefcase full of money on the webcam. 
Suggestions?

---

### Post by tripolitan on 2009-04-20
software= sudo apt-get install webcam
hardware=logitech Webcam for notebooks -not  the pro version (it is Outdated but works with linux right out of the box and cheap! less than $30)

Come back if you want help with editing the configuration file .webcamrc and setting up a webpage that refreshes every so many seconds...

---

### Post by R.Bucky on 2009-04-20
Excellent. This is what I was looking for. We will buy the cam in a day or so. 
I'll be back!

~Mark

---

### Post by R.Bucky on 2009-06-04
Wow! that was a long two days. Anyways, I finally received my QuickCam for Notebooks. It is setup on my server at [http://buckycomputing.net:8888](http://buckycomputing.net:8888) (going to configure that later). The problem is that once I refresh the page, the image turns very dark. Here is my .webcamrc
```

[grab]
       device = /dev/video0
       text = "webcam %Y-%m-%d %H:%M:%S"
       infofile = filename
       fg_red = 255
       fg_green = 255
       fg_blue = 255
       width = 400
       height = 300
       delay = 3
       wait = 0
       norm = pal
       rotate = 0
       top = 0
       left = 0
       bottom = -1
       right = -1
       quality = 100
       trigger = 0
       once = 0
```

I would like to stream the images, rather than having to refresh the page everytime. What config. tags would accomplish this feat?

~Mark

---

### Post by tripolitan on 2009-06-10
Sorry for the delay, I was "away" for a while. I'm not sure if you have fixed this problem or not but the .webcamrc seems to be missing a lot of lines. Is this all you have?

---

### Post by R.Bucky on 2009-06-10
No worries - I was delayed in obtaining the webcam! I had the camera online using webcam-server, but as i mentioned in the previous post,  it only took static images. It would not use the [ftp] tag as the software resides on my server (hosted at my home).

---

