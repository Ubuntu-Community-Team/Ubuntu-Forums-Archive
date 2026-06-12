---
title: "Problems using DV camera as v4l device (webcam)"
date: 2008-12-09
forum: Multimedia Software
---

### Post by airtek on 2008-12-09
Hi guys , 

I'm using My dv camera as a v4l device , with ffmpeg .

I follow this thread [http://ubuntuforums.org/showthread.php?t=664596](http://ubuntuforums.org/showthread.php?t=664596)

but I have problem taking the audio form the dv camera , becuase if I use dvgrab with this commands

dvgrab -showstatus -f raw -noavc -nostop  - | ffmpeg -f mpeg  -r 25 -s 720x576 -i -   -target pal-dvd -acodec mp2 -ab 192k  -vol 65536 -s  320x240 -b 5000k -f mpeg -r 25 out.mpg

Here I have the camcoder audio.

If I use dv4l or dv4lstart , with this command

dv4lstart ffmpeg -f video4linux -r 25 -s 720x576 -i /dev/video0    -target pal-dvd -acodec mp2 -ab 192k  -vol 65536 -s  320x240 -b 5000k -f mpeg -r 25 out.mpg 

I dont'have the audio of the dv camcoder . How I can take the audio of the camcoder?

thanks fot the help

Goodbye

Pierpaolo

---

