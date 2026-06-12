---
title: "Really need newbee help with ATI 320M notebook video"
date: 2011-05-05
forum: Multimedia Software
---

### Post by drguitar on 2011-05-05
I am a rank newbee to Linux and Ubuntu, so please be gentle.  I recently took my Compaq Presario 2175US notebook completely apart and resoldered the power jack so that it could be used again (after 2 years of dormancy).  After successfully putting it back together (with a handful of leftover screws :D ) , I was able to successfully install Ubuntu 10.04 (Windows XP seemed silly at this point and I really like using Open Office).  Anyway, after a couple of days looking for the wireless driver for the internal wireless, I found the answer and got that working.  

Unfortunately, the video does not seem to be working other than a basic VESA configuration.  The notebook has the ATI Radeon IGP 320M video chip installed.  I have searched for many days (about a week) on the internet for a way to get this working, but have been unsuccessful.  Although I have found many posts all over the net (here included) that list folks with similar problems, and having tried many of the "fixes", I am still unsuccessful at getting the video card to work in any more than a minimal manner (no games, no 3D of any kind...etc.)

Can someone _walk_ me through the process of getting this video card up and running properly?

Mike

---

### Post by handy on 2011-05-05
During your research, you have probably discovered that you GPU is no longer supported by the AMD/ATi proprietary drivers.

The best I can offer you is a how-to for installing a later kernel & -git driver stack.

If you want to give that a go you will find the simple how-to down a ways in the OP of this thread under the title Ubuntu Stuff:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

I've been using these cutting edge packages for over 18 months now & I'm thoroughly impressed with their reliability & stability. They have been smooth as glass over that period with only a couple of very short lived minor hiccups.

---

### Post by drguitar on 2011-05-05
Yep, I saw that thread, but was put off by the 83+ pages of posts.  Any way you can save me the 4+ hours of reading through all of that and point me at a possible solution?

---

### Post by handy on 2011-05-06
Go down to the "Ubuntu Stuff:" section in the original post (OP) of that thread. Follow the how-to there. Follow it in the exact same order as it is written.

There is no need to read the thread. 

If you do have any problems or other feedback re. having used that how-to, please post it in the thread that hosts the how-to.

---

### Post by drguitar on 2011-05-06
Handy, I really appreciate you responding to my newbie questions, but your post there points to yet another 81+ page post about kernels and such that you recommend reading before starting.  I began to read that post and realized that I have no business even trying anything you mention if I am supposed to understand modifying my "kernel".  

Again, I really, really appreciate your help, but I am a rank newcomer to linux and have no idea what or why or how I would install a new kernel and where I would need to go from there.

Is there any way you can help point me in a more specific direction so that I can just follow directions and possibly have a running video chip?

Mike

---

### Post by handy on 2011-05-06
> **drguitar said:**
> 
Handy, I really appreciate you responding to my newbie questions, but your post there points to yet another 81+ page post about kernels and such that you recommend reading before starting.  

I posted above on its own line:

**There is no need to read the thread.** 

It is out of date. Next to none of the problems that are in that thread still exist. The progress in the development of the AMD/ATi open-source driver stack (which includes changes made to the kernel) over the last 18 months or so has been nothing short of remarkable. Which is why that thread is so quiet now. :)

> **drguitar said:**
> 
I began to read that post and realized that I have no business even trying anything you mention if I am supposed to understand modifying my "kernel".  

You don't have to modify your kernel. What you are doing is installing a later version of the kernel than that shipped by Ubuntu. Even in their latest release.

> **drguitar said:**
> 
Again, I really, really appreciate your help, but I am a rank newcomer to linux and have no idea what or why or how I would install a new kernel and where I would need to go from there.

Is there any way you can help point me in a more specific direction so that I can just follow directions and possibly have a running video chip?

Mike

The how-to in the "Ubuntu Stuff:" section is complete. I do understand how incredibly steep the learning curve is when you first start using Linux/Ubuntu.

Swapping your kernel & changing your repos, so that the xorg-edgers/ppa gives you the latest packages is probably a bit much to ask when you are new to the scene.

The only other thing that comes to mind at this stage is to see if you can search out another distro that is setup to handle your GPU by default.

You could make a thread in the Other OS/Distro Talk sub-forum & ask there. You may also luck out & get some more suitable instructions than those that I know of.

I hope you find a solution.

---

### Post by www.rzr.online.fr on 2012-07-05
i have the same card. do you know a configure that support tvout ?
it worked correctly before

---

### Post by overdrank on 2012-07-05
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

