---
title: "Help! TVtime SOX Spdif Delay!"
date: 2009-05-13
forum: Multimedia Software
---

### Post by cssetti on 2009-05-13
Help!

I have TVtime running on my Jaunty setup, and i'm using SPDIF output, i am using sox for the output, but after a few minutes there is a delay between the video and the sound

I have tried using the trim 1 and trim 2 command, but it still doesn't work for the long term

What can i do to get tvtime to output to spdif in sync with the video??

here is the command that i'm using for sox:

```
sox -s -r 32000 -c 2 -t alsa hw:1,0 -s -r 32000 -c 2 -t alsa hw:0,0
```

---

### Post by cssetti on 2009-05-14
Still have not resolved issue, can anyone help??

---

### Post by xc3RnbFO8P on 2009-05-15
Read this:
[http://ubuntuforums.org/showthread.php?t=872554]("http://ubuntuforums.org/showthread.php?t=872554")
[http://ubuntuforums.org/showthread.php?t=884438]("http://ubuntuforums.org/showthread.php?t=884438")

---

