---
title: "How to make VLC (or any video player) the default for all video files."
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by u-slayer on 2007-09-09
I've searched the forums in the past, trying to find a way to change the default application that opens video files. The best response I ever found was to right click on the files and manually change the properties. 

I find this method slow and tedious. There are 19 different types of video files. Therefore, I have automated the whole thing. ONE line in the terminal will change ALL of your video files so that they open with vlc

```
cd /usr/share/mime
ls video/* | sed 's/.xml/=vlc.desktop/' | tee -a ~/.local/share/applications/defaults.list
```

By the way, this also works for Image, message, multipart, text, audio, packages and video files.

Just change the word video to one of the above options and change vlc to whatever app you like best.

---

### Post by u-slayer on 2007-09-09
Well? does this work for anyone else?

---

### Post by SynUK on 2007-09-11
Sorry no it doesn't for me. After running the above, MP4 files still opening with Totem Movie Player.

---

### Post by u-slayer on 2007-09-11
Can you copy and paste your ~/.local/share/applications/defaults.list here? I think you may have duplicate entries.

---

### Post by SynUK on 2007-09-13
Yep no problem. My defaults.list is :

```
video/3gpp=vlc.desktop
video/dv=vlc.desktop
video/isivideo=vlc.desktop
video/mpeg=vlc.desktop
video/quicktime=vlc.desktop
video/vivo=vlc.desktop
video/vnd.rn-realvideo=vlc.desktop
video/wavelet=vlc.desktop
video/x-anim=vlc.desktop
video/x-flic=vlc.desktop
video/x-matroska=vlc.desktop
video/x-mng=vlc.desktop
video/x-ms-asf=vlc.desktop
video/x-msvideo=vlc.desktop
video/x-ms-wmv=vlc.desktop
video/x-nsv=vlc.desktop
video/x-ogm+ogg=vlc.desktop
video/x-sgi-movie=vlc.desktop
video/x-theora+ogg=vlc.desktop
video/mp4=vlc.desktop
```

and for some reason when I run an mp4,avi or mpg file it stil opens it with totem movie player.

---

### Post by u-slayer on 2007-09-13
Sorry it doesn't work for you. It works for me and it works for these guys...

[http://forum.videolan.org/viewtopic.php?f=13&t=40560](http://forum.videolan.org/viewtopic.php?f=13&t=40560)

Now they are including the code into the vlc source tree.

---

### Post by SynUK on 2007-09-14
Well the script they list doesn't work on my system either so there must be something else wrong somewhere. When I run the script they say they are putting into the package I get the following :

```

./video-vlc-default.sh: 1: cannot open !DOCTYPE: No such file
./video-vlc-default.sh: 1: html: not found
./video-vlc-default.sh: 2: PUBLIC: not found
./video-vlc-default.sh: 3: Syntax error: newline unexpected


```

I'm not sure what is going on really. I have install Ubuntu Feisty as normal from a DVD then added Beryl but apart from that it is a normal install and everything else works fine. I can even run VLC manually and open the MP4 file and it plays with no problem, just not by double clicking the MP4 file - then it always opens Totem Movie Player.

---

### Post by Sbarton on 2007-09-22
I was looking at how to achieve making VLC default when I noticed this post:[http://ubuntuforums.org/showthread.php?p=3330312&highlight=how+to+make+VLC+default+player#post3330312](http://ubuntuforums.org/showthread.php?p=3330312&highlight=how+to+make+VLC+default+player#post3330312)
which worked for me.
regards and thanks to OP of that link.

---

