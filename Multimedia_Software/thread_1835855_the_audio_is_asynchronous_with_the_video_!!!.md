---
title: "the audio is asynchronous with the video !!! ?"
date: 2011-08-30
forum: Multimedia Software
---

### Post by q8_legend on 2011-08-30
Hi

I'm running under Ubuntu 11.04, and I'm facing problem with the audio while playing videos...

when I play the video in VLC the audio is not synchronous with the video, there is some delay(seconds)... why that is happening ?? before it was just fine, I don't know why the problem start now !!


[B]Note:

When I play the same video in SMplayer it works just fine, while in other video player(like VLC) the problem occur... !!! Can any one tell me why ??[/B]

Thanks alot

---

### Post by BicyclerBoy on 2011-08-30
If you use VLC directly with alsa there is no sync problem.

The newer pulse audio time scheduler has caused upstream problems with VLC.

You can change pulse audio back to interrupt timing method.
[http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime](http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime)

---

### Post by q8_legend on 2011-08-30
> **BicyclerBoy said:**
> If you use VLC directly with alsa there is no sync problem.

The newer pulse audio time scheduler has caused upstream problems with VLC.

You can change pulse audio back to interrupt timing method.
[http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime](http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime)



Thank you so much... now its working ;)

---

### Post by BicyclerBoy on 2011-08-30
Most welcome..

---

