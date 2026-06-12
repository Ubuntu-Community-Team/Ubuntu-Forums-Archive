---
title: "How to turn a .mov film by 90 degrees?"
date: 2013-01-01
forum: Multimedia Software
---

### Post by quadruplex on 2013-01-01
Hello,

I have a rather weird question:

A friend of mine filmed me while boxing and kickboxing, and unfortunately (I do not know why he did this), he turned the camere 90 degrees clockwise.

Now, to watch the films, I have to turn the monitor 90 degress anti-clockwise :p

Is there a tool with which I can turn around a whole .mov film by 90 degrees?

Thank you for any suggestions,
Q.

---

### Post by andrew.46 on 2013-01-01
A short term solution with either SMPlayer or vlc is to rotate the video during playback (options exist with both vlc and SMPlayer), but I guess you wish to re-encode with the image rotated the correct way?

---

### Post by quadruplex on 2013-01-01
Thanks for the short term solution, i did not now that these options exist in VLC; I will try this out tomorrow.

And yes, I ultimately want a long term solution that I can send to other poeple.

Thank you very much!

---

### Post by fdrake on 2013-01-01
mplayer
```

mplayer -vf rotate 3 <myvideo>

```

---

### Post by andrew.46 on 2013-01-01
The FFmpeg / avconv method would be to re-encode using the transpose filter:

21.33 transpose
[http://libav.org/avconv.html#transpose](http://libav.org/avconv.html#transpose)

so I guess you would be after:

```
-vf transpose=2
```

If you are not yet an avconv ninja perhaps you could install avconv:

```
sudo apt-get install ffmpeg libavcodec-extra-53
```

and then run the following against your input file:

```
avconv -i *input.file*
```

(changing the name of input.file to match your own filename) and somebody can suggest a suitable commandline. Hope this helps?

---

### Post by quadruplex on 2013-02-22
Thank you for everybody answering me in this thread. I ultimately found a free Windows solution, DVDVideoSoft. :-(

I could not install the packages mentioned above, at least not under Debian (I know this is an Ubuntu forum, but I work with Debian on my laptop in my leisure time, I use Ubuntu at work.)

And I did not want to burden myself with compiling the packages.

Thank you all!

---

### Post by andrew.46 on 2013-02-22
As long as you have solved the issue, one way or the other :)

---

