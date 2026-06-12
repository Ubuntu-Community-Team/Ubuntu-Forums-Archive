---
title: "[SOLVED] Playing or encoding (mplayer/mencoder) from mounted .iso image."
date: 2008-07-10
forum: Multimedia Software
---

### Post by heyho on 2008-07-10
I'm currently in the process of trying to output an avi (xvid) using mencoder, but by using a mounted iso and not a physical dvd.

I know that mplayer can play a mounted iso image, but I have achieved this using the GUI via preferences>misc then changing the DVD device path, but I'm stuck when it comes to playing the iso from the command line.  Once I have worked out how to play the iso, I can start on encoding.

Hoping this is a simple one!

The path to the .iso is /mnt/disk

---

### Post by mc4man on 2008-07-10
I can't duplicate what you have because I have a separate / and /home (not enough space in /) but this should give you the idea. (I had to mount the iso in home dir., in this case 8 was the title of movie)
>   mplayer -dvd-device /home/doug/disk dvd://8 so try 
> mplayer -dvd-device /mnt/disk dvd://<title >

---

### Post by heyho on 2008-07-11
Thanks for the reply - not working yet, but a lot closer!

I'll update as and when I have success.

---

### Post by mc4man on 2008-07-11
As far as playback should work, do you have the iso mounted? It should be seen in places -> removable media (probably named disk)

---

### Post by heyho on 2008-07-11
You're spot on - I had mounted the image initially, but had started a new session when I read your reply, and had forgotten to re-mount the image. Doh!

Now working for playback, so I see no reason for it not to work for encoding - I'm at work at the moment, but will try it with mencoder this evening.

Many thanks.

---

### Post by heyho on 2008-07-11
Now also able to encode directly from image file - great stuff, thanks again.

---

