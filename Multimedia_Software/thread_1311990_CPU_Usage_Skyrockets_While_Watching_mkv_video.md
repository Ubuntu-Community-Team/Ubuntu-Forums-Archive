---
title: "CPU Usage Skyrockets While Watching mkv video"
date: 2009-11-02
forum: Multimedia Software
---

### Post by TJ1234 on 2009-11-02
Ok, so I updated to Karmic yesterday and everything was going fine until I tried to play an mkv video I had on my drive. At first it seemed I didn't have the right codecs but everything seemed to check out. Now my computer will play the files but the cpu usage goes way up to probably 90% or so compared to before I upgraded, it would run them fine without a cpu usage spike. I just want to know if there is a way to fix this?

Here is some more information: the mkv files would play but with a blue tint, I ran gstreamer -properties from the terminal and underneath the video option I had to switch the default output plug in to X Window System (No Xv). This is all I did to fix the problem.

My computer
HP dv9000
4 Gigs of RAM
Intel Core 2 Duo T5750 @ 2.00 GHz

---

### Post by lukeiamyourfather on 2009-11-02
Have you tried VLC or another player? It might be something specifically with that player. Also what codec was the video stream? Cheers!

---

### Post by TJ1234 on 2009-11-04
VLC works fine (Can't believe I didn't check this... And they let me administrate a network!).  But I would still like to know whats going on with MPlayer, how do I check which codec it's using?

---

### Post by lukeiamyourfather on 2009-11-04
> **TJ1234 said:**
> VLC works fine (Can't believe I didn't check this... And they let me administrate a network!).  But I would still like to know whats going on with MPlayer, how do I check which codec it's using?

VLC probably has a tool somewhere to tell what the video stream is, but I don't have it in front of me right now. Cheers!

---

