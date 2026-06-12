---
title: "converting vob to mp4"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by xjgnsdof on 2008-01-29
I'm trying to convert VOB files to MP4 so I can put them on my iPod Touch. I'm using Avidemux. What settings do I select from the drop down menus (namely, Video, Audio, and Container)?

---

### Post by specvthis on 2008-01-30
I use this script and it works great on my Iphone.  It should be either identical or essentially the same for an iPod.  Just create a file called iphonevid.sh or something similar in your /usr/bin/ directory (need sudo) and put the following code in it.  To use it just simply execute it as following:

iphonevid [input.vob] [output.mp4]

> 
#!/bin/bash
ffmpeg -i $1 -b 576k -s 480x320 -vcodec mpeg4 -ab 220k -ar 44100 -acodec aac $2


Also you will need ffmpeg so make sure to run this first

sudo apt-get install ffmpeg

---

### Post by FakeOutdoorsman on 2008-01-30
The Ubuntu Wiki has a good ipod encoding section: [Encoding Video for the iPod Video]("https://help.ubuntu.com/community/iPodVideoEncoding").  I've used and recommend the pypodconv script mentioned in the wiki page.

---

### Post by xjgnsdof on 2008-01-30
The iphonevid script didn't work ("command not found"). I'll try the pypod solution when simpler solutions have been exhausted. Any idea how to do this in avidemux? I have some experience using that...

---

### Post by specvthis on 2008-01-30
Sorry to run it you would need to type:

iphonevid.sh [input.vob] [output.mp4]

---

### Post by xjgnsdof on 2008-01-30
Terminal couldn't recognize that command, even as sudo. I copied the text into the script before copying it into the filesystem at the path you specified above, though I doubt that makes any difference. I'm just putting that out there because I have relatively little experience with scripts.

---

### Post by xjgnsdof on 2008-01-31
It turns out the Ubuntu wiki had the solution that I needed. Mark Pilgrim's mencoder based solution, specifically, enabled my to encode .avi, .mpg, and .vob movies to .mp4 quickly and easily. Thanks!

---

