---
title: "Video resolution"
date: 2013-08-02
forum: Multimedia Software
---

### Post by Issam_JAAFARI on 2013-08-02
Good day guys

I used a command line to get a video resolution like this wxh (i.e: 640x320), it is not mediainfo, it is just a 2 or 3 words, if somebody has an idea about the same, I will be greatfull

Thx

---

### Post by Petro Dawg on 2013-08-02
something like this...

```
xrandr
```

???

---

### Post by Issam_JAAFARI on 2013-08-02
not that one :(

---

### Post by Petro Dawg on 2013-08-02
How about...

```
gnome-display-properties
```

???

It might be helpful if you describe what you are trying to do.  Are you setting up dual monitors, changing your resolution on a single output, or are you just wanting to see what your current resolution is?

---

### Post by alfirdaous on 2013-08-03
If I have a video file, I can do like this:

```

mediainfo file.mp4

```

this command line will extract all information about file.mp4, hence I need only width and height of the video file

---

### Post by Petro Dawg on 2013-08-03
Well that's certainly a horse of a different color.

Aside from Mediainfo, the only other terminal commands I can find are...

With MPlayer installed...
```
./midentify.sh /path/to/vid.format
```

and..

```
ffmpeg -i video.mpg
```

or...

```
ffprobe -i video.format
```

---

### Post by alfirdaous on 2013-08-03
Thx Petro, not that one, the only result should be something like:

```
1210x720
```

---

### Post by Petro Dawg on 2013-08-03
If you used the command at some point on your current installation you could try using...

```
history
```

to see what terminal commands you have entered in the past.

---

### Post by alfirdaous on 2013-08-03
Unfortunatly I reinstalled the system, I used few months back

---

