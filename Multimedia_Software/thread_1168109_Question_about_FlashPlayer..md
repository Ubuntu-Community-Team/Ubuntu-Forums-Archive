---
title: "Question about FlashPlayer."
date: 2009-05-23
forum: Multimedia Software
---

### Post by Lakeside5 on 2009-05-23
I am wondering about flashplayer for linux- like if it's installed on here.  I seem to be able to embed youtube videos on my website (own server/website) and I can see them, but when I try to put on my own videos that are in my computer, put in website's image folder in root, they do not, and they are .swf files. I clicked on the said video (test.swf) but when it wouldn't load in totem movie player, it said: An error occurred  GStreamer encountered a general supporting library error.

---

### Post by lovinglinux on 2009-05-23
I think you need to use flv movies instead of swf. Additionally, how are you embedding the videos? Just putting them on a folder won't let you view them via web. You need to embed the file yourself or use a custom player on your page.

---

### Post by Lakeside5 on 2009-05-23
I'm sorry for not putting in all the information..trying not to make such a big post :)  I have installed the AllVideos plugin from Joomlaworks (for whoever may be familiar with that) and all you have to do with that is put  {flv}videoname{/flv}  if you are using a flv, change for the file type and filename.  I did try using flv with same result, but for some reason the youtube ones DO play..  Sasswebs.com  the white space underneath should be my own video playing, but it's not for some reason.

---

### Post by lovinglinux on 2009-05-23
> **Lakeside5 said:**
> I'm sorry for not putting in all the information..trying not to make such a big post :)  I have installed the AllVideos plugin from Joomlaworks (for whoever may be familiar with that) and all you have to do with that is put  {flv}videoname{/flv}  if you are using a flv, change for the file type and filename.  I did try using flv with same result, but for some reason the youtube ones DO play..  Sasswebs.com  the white space underneath should be my own video playing, but it's not for some reason.

I use Joomla, but I haven't used AllVideos extension for a while. As far as I remember, AllVideos supports other codecs and containers. Have you tried with avi or wmv files? What video plugin are you using on Firefox?

I recommend this guide: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Lakeside5 on 2009-05-24
Thanks for your reply lovinglinux, it seems the .flv and wmv aren not working either, so I don't know what's going on.  will keep trying though, thanks.

---

### Post by Lakeside5 on 2009-05-24
Could anyone tell me, just from looking here:  sasswebs.com  why the last two videos won't play? I am using an video player extension called 'AllVideos' on a Joomla CMS website, and the last two videos are a .flv, and a .mov file hosted by my computer (using Hardy Heron here). I don't know what file type the first two movies are, the ones coming from youtube, and I'm wondering why they are playing, and mine aren't.

---

### Post by lovinglinux on 2009-05-24
> **Lakeside5 said:**
> Could anyone tell me, just from looking here:  sasswebs.com  why the last two videos won't play? I am using an video player extension called 'AllVideos' on a Joomla CMS website, and the last two videos are a .flv, and a .mov file hosted by my computer (using Hardy Heron here). I don't know what file type the first two movies are, the ones coming from youtube, and I'm wondering why they are playing, and mine aren't.

Have you checked if AllVideos is loading the files from the correct path? Have you tried playing those videos with a different Joomla extension? I would try to do that, to check if the problem is related to ALLVideos or to a codec/player on your system.

---

### Post by Lakeside5 on 2009-05-24
Wow, lovinglinux, that was fast lol :) That's a good idea, I will do that, as I don't mind saying I am getting a little frustrated :)  As for the path, I am following AllVideos instructions, the path is images/stories/videos, and that's where they are.

---

### Post by lovinglinux on 2009-05-24
> **Lakeside5 said:**
> Wow, lovinglinux, that was fast lol :) That's a good idea, I will do that, as I don't mind saying I am getting a little frustrated :)  As for the path, I am following AllVideos instructions, the path is images/stories/videos, and that's where they are.

It should be working then. Probably is codec issue or something, but would test it anyway, specially because I remember having troubles with AllVideos in Windows too.

---

### Post by Lakeside5 on 2009-05-24
Ok, thanks.

---

### Post by Lakeside5 on 2009-05-27
Thanks for all the help lovinglinux.  It seems the problem was two-part: I was probably using videos that weren't good (I tried to convert my camera videos to .flv's, they did but I dont' think they are right) and second, I thought I had all the right permissions on my video files, but I went back in and chown'ed everything, and now 'demo.flv' will play on the frontpage, and also plays properly now on the 'contents component' link page!! :) (before it would play and keep stopping) I am finding that often, when I have a problem, it has to do with permissions, so I hope some other 'newbie' can learn from my mistake.

---

### Post by lovinglinux on 2009-05-27
You are welcome. I'm glad you figured it out.

---

