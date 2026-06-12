---
title: "Ubuntu 12.04 - Skype 4.1 not working and Cheese intermittent"
date: 2012-12-18
forum: Multimedia Software
---

### Post by Bhairava on 2012-12-18
Hello everyone,

I have installed Cheese and Skype 4.1 for video chat.
I have a very inexpensive webcam - Radioshack's Gigaware.
OS - Ubuntu 12.04

Cheese is working the first time I start my machine and then it stops. 
I reboot and it works the first time again.
As for Skype, in the "video devices", I see a black image (no image).
The other side can hear my voice but cannot see me. 
I tried changing the path that was recommended as a solution to many queries - [http://ubuntuforums.org/showthread.php?t=2028125](http://ubuntuforums.org/showthread.php?t=2028125)

It worked once on Skype but my video froze after sometime and then it stopped altogether.

Can someone please help me out.

Thanks !

---

### Post by Bhairava on 2013-02-09
Ok. I had attached a link in the previous post.
I find that copying and pasting 

"LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype" in the terminal works perfectly fine with Skype.
This is as opposed to "v4l2compat.so."

Now, this may seem a bit weird, but when I open other applications such as, say the Chromium browser and fiddle around for a certain amount of time and my Skype video chat is on, then my video freezes.
What I found in this case is, though troublesome it may be, is that, disconnecting the USB webcam and reconnecting it helps in restoring the original settings. This may be obvious but I struck upon it only after an hour or so.
If there is a better solution please let me know.

Thanks !

---

