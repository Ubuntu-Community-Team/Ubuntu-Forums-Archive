---
title: "Totem , VLC and Mplayer"
date: 2008-08-10
forum: Multimedia Software
---

### Post by rashwan on 2008-08-10
Hello,
sorry for disturbing but i really hope to solve this problem
story begins when i tried to play movie and found colors inverted
see image
[[IMG]http://img106.imageshack.us/img106/9108/screenshotbh8.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotbh8.png)

quick google search found this solution:
open gstream-properties
and change the video output plugin to custom
and the video output pipeline to:
ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink
and Test
then it works just fine , later on it came back inverted again
searched again found this solution:
open totem then Edit ----> Preference ----> Display
change the Hue to maximum or to the lowest 
and again it works but when i try to play anything it either be inverted or plays on very slow motion same on VLC and MPlayer have to reboot to solve this problem
any suggestion ..? Thank You

---

