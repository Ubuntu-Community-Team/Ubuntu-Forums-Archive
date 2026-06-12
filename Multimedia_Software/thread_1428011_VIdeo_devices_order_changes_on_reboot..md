---
title: "VIdeo devices order changes on reboot."
date: 2010-03-12
forum: Multimedia Software
---

### Post by MrTashi on 2010-03-12
Hi guys !

I'm having a problem with video capture devices. 
I have a cheap analog capture card (encore) and a webcam.
Not sure exactly why, they are mapped as /dev/video0 and /dev/video1 in diferent orders randomly as far as i can see.

So, sometimes i reboot having webcam as /dev/video0 and capture card as /dev/video1. But then i reboot later, or next day, and they swap.

Then, i have to change config for other programs over and over again. For example, i use tvtime to watch live tv, and i have to edit the config xml files almost everyday...

Any idea if this behavior is normal?? 
Can i force devices to be always mapped the same way?
Can i at least add some kind of alias to use instead of device numbers?

Sorry if this is posted already. Googled it a while without any success.

By the way, i'm on 9.10-karmic koala

Thanks in advance,
tashi.

---

### Post by wkulecz on 2010-03-12
I'm seeing the same issue with only a single USB video device, usually its /dev/video0 after I plug it in, but sometimes for no reason I can see, its /dev/video1 :(

Using it with 9.10 too.

--wally.

---

### Post by sisco311 on 2010-03-12
Instead of /dev/video* use the static device names from /dev/v4l/by-path/*.

---

