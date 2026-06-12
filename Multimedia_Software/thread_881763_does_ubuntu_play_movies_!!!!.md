---
title: "does ubuntu play movies !!!!"
date: 2008-08-06
forum: Multimedia Software
---

### Post by rashwan on 2008-08-06
Hello,
when i try to play any movie it gives me silly blue tint
i'ave searched in forums till i found this 
```
gstream-properties
```
and changed the video output plugin to custom
and the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink
and Test .....ok it works but once only once soon after it came back this Damn tint and with the previous options loaded
also i dont DREAM to play a .rmvb movie also the realplayer plays only .rm and no audio control !!

[[IMG]http://img106.imageshack.us/img106/9108/screenshotbh8.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotbh8.png)

so that makes me wonder...does ubuntu play movies !!?

---

### Post by tuxxy on 2008-08-06
Did you install ubuntu-restricted-extras package, this will install many codecs including dvd playback.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by snipehunter on 2008-08-06
I was trying to find how to play DVDs on Ubuntu and ran across this [page]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") explainging what specific packages need to be installed.  

Apparently the libdvdcss2 package needs to be installed, which you can do through synaptic package manager.  And if you have international code issues like I do, you might want to install regionset while you're at it.  

I haven't tested playing a DVD since I installed the packets, so this is more of a hint than a solution. [-o<

---

### Post by tuxxy on 2008-08-06
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Codecs)

---

### Post by rashwan on 2008-08-06
ohh Yeah , sure , of course , why not....but am wondering what should these packages do with the BLUE TINT !!
still nothing changed

---

### Post by eival on 2008-08-06
try playing the DVD with the VLC player.

---

### Post by rashwan on 2008-08-06
eival, its not DVD issue its about all video extentions (eg: .avi , .wmv , .mpg)
even so ..  VLC gives blue tint also

---

### Post by soxs on 2008-08-06
> **rashwan said:**
> eival, its not DVD issue its about all video extentions (eg: .avi , .wmv , .mpg)
even so ..  VLC gives blue tint also

Did you ever see that vid with true life colours? It may be corrupted, or did you check it with winblows or OSX

---

### Post by ZeldaFan on 2008-08-06
Soxs, pardon me for the unrelated post here, but :lolflag: at your currrent, peculiar post count.

---

### Post by rashwan on 2008-08-06
sox, yeah it works even in ubuntu but takes no long to be BLUE again

---

### Post by rashwan on 2008-08-06
thats what i got when try to play any video type

[[IMG]http://img106.imageshack.us/img106/9108/screenshotbh8.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotbh8.png)

---

### Post by eival on 2008-08-06
> **rashwan said:**
> thats what i got when try to play any video type

[[IMG]http://img106.imageshack.us/img106/9108/screenshotbh8.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotbh8.png)

i can tell by that image that the correct name of your issue is your picture color is "inverted", not just a blue tint. i use photoshop alot and are familiar with the color scheme effect.

however i dont know why your video card would be doing that to the image. try looking at the video settings and see if adjusting the color or hue/tint does anything

EDIT: i just noticed the name of the file "aXXo" so its not a store bought dvd, the issue could be during the actuall burning process itself. unless you're playing the raw AVI file strait from your HDD.

....wait a minute, have you watched past that opening scene?

that might look like that on purpose

---

### Post by rashwan on 2008-08-06
eival, thx for the quick replay but actually it was working , it gives that "inverted"
before and i just lunched gstream-properties from konsule and and changed the video output plugin to custom
and the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink
and Test .....and it works just fine but it came back "inverted" again!

---

### Post by mc4man on 2008-08-06
see links in this thread, one of them should work
[http://ubuntuforums.org/showthread.php?t=869210&highlight=wrong+colors](http://ubuntuforums.org/showthread.php?t=869210&highlight=wrong+colors)

---

