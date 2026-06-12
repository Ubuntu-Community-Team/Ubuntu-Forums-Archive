---
title: "&quot;webcam&quot; config: &quot;file&quot; parameter not processing with strftime"
date: 2013-03-09
forum: Multimedia Software
---

### Post by cormacG on 2013-03-09
I'm using "webcam" ([http://manpages.ubuntu.com/manpages/precise/en/man1/webcam.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/webcam.1.html)) to grab images from my webcam at intervals. The config file I'm using is this:

[grab]
device = /dev/video0
text = skycam %Y-%m-%d %H:%M
fg_red = 255
fg_green = 255
fg_blue = 255
width = 320
height = 240
delay = 30
wait = 30
rotate = 0
top = 0
left = 0
bottom = -1
right = -1
quality = 100
trigger = 0
once = 0
[MyServer]
host = localhost
user = blah
pass = blah
dir  = /var/www/weather/cam
file = skycam_%Y-%m-%d-%H%M.jpg
tmp  = skycam-uploading.jpg
passive = 1
debug = 0
auto = 0
local = 1
ssh = 0

While **skycam %Y-%m-%d %H:%M** in the [grab] section is being correctly processed by strftime e.g. the image is stamped with "skycam 2013-03-10 04:30", no matter what I do, I cannot get **file = skycam_%Y-%m-%d-%H%M.jpg** in the [MyServer] section to process with strftime i.e. to create a unique timestamped filename. The "webcam" manpage indicates the file parameter is supposed to be parsed with strftime. Am I missing something blindly obvious here or have I uncovered a bug?

---

