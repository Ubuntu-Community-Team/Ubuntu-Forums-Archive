---
title: "package webcam setting multiple cams in webcam.conf?"
date: 2012-03-11
forum: Multimedia Software
---

### Post by Allochtoon on 2012-03-11
hello fellow 'bunters,

i was wondering if and how it is possible to feed multiple cams to jpg with the webcam package. i tried to run a different webcam process for the second cam (webcam /etc/webcam1.conf). also tried one webcam process and inserting second cam with approapriate config in /etc/webcam.conf. no joy.

i can see both cams; /dev/video0  /dev/video1

thank you,

---

### Post by Allochtoon on 2012-03-11
got it working, will post details asap.

---

### Post by Allochtoon on 2012-03-11
--> Startup Applications .. 

webcam /etc/webcam.conf
and
webcam /etc/webcam1.conf

/etc/webcam.conf
```

[ftp]
host = localhost
user = nobody
pass = xxxxxx 
dir = /var/www/spacelotusone
file = webcam.jpg
tmp = imageup.jpg
local = 1

[grab]
device = /dev/video0
width = 1280
height = 1024
delay = 10
input = Camera 1
quality = 99
trigger = 150
rotate = 0

```

/etc/webcam1.conf
```

[ftp]
host = localhost
user = nobody
pass = xxxxxx 
dir = /var/www/spacelotusone
file = webcam1.jpg
tmp = imageup1.jpg
local = 1

[grab]
device = /dev/video1
width = 1280
height = 1024
delay = 10
input = Camera 1
quality = 99
trigger = 150
rotate = 1

```

---

