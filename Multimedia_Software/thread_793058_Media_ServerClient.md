---
title: "Media Server/Client"
date: 2008-05-13
forum: Multimedia Software
---

### Post by LindsaySlater on 2008-05-13
Good morning, Afternoon, and/or good evening to all!
Here is my situation:
I have an outdoor sound system, with a stereo in the garage, but I would like to be able to access all the music stored in iTunes on my XP machine back in the house.

My understanding is that the cheapest/easiest way to do this would be set up a media sharing client on the XP machine (I already have 3 methods, due to the fact that I have an Xbox 360 upstairs which accesses all the content fairly well)
The current media servers are:
 iTunes, with its built in sharing
 TVersity, sharing my movies, photos, etc
 TwonkyVision, mostly for sharing my iTunes Library

I already have a cheap machine running Xubuntu 6.06 set up in the garage, attached to the network of course.

What media players would you suggest for accessing my iTunes library, through any of the servers I have running already?

Sorry if this has already been discussed in the past and I just missed the thread...

Thanks in advance to all who reply!

---

### Post by cariboo on 2008-05-13
The easiest way is just to mount your music directory on your Xubuntu computer and use your favorite music player. If you want to use a streaming server, most music players can access streaming media.

Jim

---

### Post by LindsaySlater on 2008-05-13
Thanks for the quick reply!

I have heard that Amarok will read an iTunes library file, but sadly it has been waay too long since I last actually worked with Xubuntu.
I'm just wondering if any of the media players out there will see a shared iTunes library, and how to configure one to find it.

---

### Post by LindsaySlater on 2008-05-25
Well, after a week of messing around with various settings and operating systems, I have settled on Kubuntu for the moment, but still cannot figure out how to set up amaroK to see my shared iTunes library.

Is there anybody out there in the land of the interweb that could help me out on this one???

---

### Post by kbailey on 2008-05-28
You could "share" your folder containing the music files, then modify your /etc/fstab file on the Kubuntu machine to mount the folder on startup. I have Mediatomb set up that way for streaming audio and video from a network drive to my D-Link media player.

---

