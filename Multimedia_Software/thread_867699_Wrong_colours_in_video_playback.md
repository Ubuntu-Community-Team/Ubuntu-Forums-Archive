---
title: "Wrong colours in video playback"
date: 2008-07-23
forum: Multimedia Software
---

### Post by Lux01 on 2008-07-23
Hi, I was wondering if anyone here can help me.

I just recently installed Ubuntu 8.04 64-bit and videos were playing fine but I booted it up this morning and when trying to play a video or DVD the colours are wrong. For example what should be blue is red and vice versa. It was working last night when watching a DVD in Ogle as VLC and the rest wouldn't play DVDs for some reason last night but even that has the problem now.

I uploaded a screenshot of what I mean: [http://www.lux01.co.uk/files/Screenshot.png]("http://www.lux01.co.uk/files/Screenshot.png"). As you can probably tell, people aren't blue and he isn't supposed to be (I've watched the DVD before).

Thanks in advance,

William

---

### Post by Bachstelze on 2008-07-23
Moved to Multimedia & Video.

---

### Post by munkyboy on 2008-07-23
I had exactley the same problem. And found it was because i was playing from an external drive.

Once i played the files from my Ubuntu partiotion it worked perfectley

---

### Post by Lux01 on 2008-07-23
I tried that but there's no change.

---

### Post by Lux01 on 2008-07-23
*facepalm* :redface: It's working now after a reboot.

---

### Post by kaefert66014235 on 2009-04-30
I suddenly got the same problem on Ubuntu 8.10, and rebooting doesn't solve it for me. I also tried switching the nvidia driver, that doesn't solve it too.

What would solve it is to deactivate the nvidia driver, but then the graphical performance reaaally sucks.

please help

---

### Post by loki.verloren on 2010-10-24
I just had the same problem upon a fresh install of Maverick - the problem is caused by the setting in the nvidia-settings defaulting to 180 degrees hue adjustment. Just change it to zero and everything is back to normal. Most linux video playing apps can also let you adjust the hue just within the program but obviously it would make sense to do the adjustment universally (or, to be more exact, *un*do the adjustment) so all video playback is corrected, and no extra load is put on the machine running colour adjustment transforms.

---

