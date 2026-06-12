---
title: "Change Cheese Temp Directory"
date: 2009-08-21
forum: Multimedia Software
---

### Post by X96 Design on 2009-08-21
Hi There,

I want to set up a "security" camera using my webcam, but I want to make sure I don't run out of space for the video.

I have a 640 GB external HD, and want to tell Cheese Webcam Booth to record the file into a directory on my External HD.

Is there any way to do this? If not, is there any other program which can?

Thanks a lot!

// X96 \\

---

### Post by trovich on 2009-11-07
See [4.2.&#8195;GConf settings]("http://library.gnome.org/users/cheese/stable/setting-up.html.en")

It's possible to define where Cheese stores the captured media (photos and videos). These settings are stored in GConf. You can change the settings with the gconf-editor, application. There you have to select /apps/cheese in the tree on the left. Then you can set the video_path and photo_path to the location you prefer. There you can also set other parameters for Cheese, but you should use the preferences dialog for a controlled access.

---

### Post by X96 Design on 2009-11-07
Thank You!

// X96 \\

---

### Post by xX0v0Xx on 2012-05-17
It seems that cheese is no longer mananed by gconf-editor in Ubuntu 12.04.

---

### Post by overdrank on 2012-05-17
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

