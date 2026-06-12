---
title: "How to fix Ubuntu 10.04 LTS to play audio cds?"
date: 2011-06-22
forum: Multimedia Software
---

### Post by Waffle-King on 2011-06-22
Recently, I upgraded to Ubuntu version 10.04 LTS from version 9.04. However, if I put I CD in my computer, the computer doesn't even know that it contains an audio disc. The disc isn't found in any audio music program(obviously). I believe the disc drive/hardware is just fine, as I listened to CDs regularly on my computer when I was still using 9.04. Are there any terminal commands or sequences of terminal commands that can remedy this, likely by installing drivers or something?(sorry. I don't know very much "computer-talk") Or perhaps there is an error in the default preferences of the new distro? Any help is appreciated, but I would ideally like to simply have some terminal code to copy and paste. Thanks to anyone who can help!

---

### Post by andrew.46 on 2011-06-23
This problem has popped up a few times recently. Can you play audio cds from the commandline by installing mplayer:

```
sudo apt-get install mplayer
```

and then running the following:

```
mplayer -cache 2048 cdda://
```

Hopefully this will at least get some music playing, but I am not sure about the underlying issues if this works...

---

### Post by Waffle-King on 2011-06-30
It does play CDs if I run that program, but it only runs in the terminal, so I can't rip audio tracks. I am BUMPing this thread because I now want to know how I might be able to rip audio CDs. Thanks for any relevant responses.

---

### Post by andrew.46 on 2011-06-30
> **Waffle-King said:**
>  I am BUMPing this thread because I now want to know how I might be able to rip audio CDs. 

Perhaps this might help:

HOWTO: Convert music CDs to MP3 using the Command Line.
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

---

