---
title: "ClibGrab download problem"
date: 2013-05-24
forum: Multimedia Software
---

### Post by veledrom on 2013-05-24
Hi,

I installed ClibGrab to download videos as in MP3. It shows as "download finished" but when I open download folder e.g. /home/Dekstop/ or anywhere else like other folder and medias, there is no file appears. Any reason why?

Thanks

Ubuntu 12.04 lts, ClibGrab

---

### Post by andrew.46 on 2013-05-26
I am not sure what you mean by 'download videos as in MP3'? Do you mean that it downloads a video and then extracts an mp3 track? If so have a look at:

```

find $HOME -iname *.mp3

```

and perhaps this may find the missing files :)

---

### Post by veledrom on 2013-05-28
You understood right. Finding didn't return anything.

---

### Post by andrew.46 on 2013-05-28
I downloaded the source + compiled, have to admit I was not that keen on ClipGrab. It uses FFmpeg for the conversion and this worked well enough on my system. Make sure that you have FFmpeg installed and that it is capable of converting to mp3:

```

sudo apt-get install ffmpeg libavcodec-extra-53

```

Hopefully this will get you going :)

---

### Post by veledrom on 2013-05-28
Excellent. Thank you very much.

How do I mark this as solved?

---

### Post by BlinkinCat on 2013-05-28
> **veledrom said:**
> Excellent. Thank you very much.

How do I mark this as solved?


Here's how to mark your first post as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :p

---

### Post by veledrom on 2013-05-28
There is no "Prefix" option between Reason and Title though. It doesn't appear. I tried with old post, this current post, with old comment, with a new comment. No luck.

---

### Post by BlinkinCat on 2013-05-28
> **veledrom said:**
> There is no "Prefix" option between Reason and Title though. It doesn't appear. I tried with old post, this current post, with old comment, with a new comment. No luck.

It is a 4 step process on your first post which should work. Did you select "Go Advanced" ?

---

### Post by andrew.46 on 2013-05-28
> **veledrom said:**
> Excellent. Thank you very much.

Good to see the issue resolved :)

---

### Post by veledrom on 2013-05-28
There is no Prefix option. I went through 10 times. Also why they don't add a simple button to mark it as solved anyway! Why go through many steps.....

---

