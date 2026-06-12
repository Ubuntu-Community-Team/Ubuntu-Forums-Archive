---
title: "Video is realy fast and no sound"
date: 2012-02-07
forum: Multimedia Software
---

### Post by xylophone on 2012-02-07
Hello all.
I am running Ubuntu 10.04 LTS off of a USB stick. Whenever I try to play any sound, nothing happens. I have double check that the volume is turned up and in the sound manager it recognizes my sound card. Also, whenever I try to play a video, either on a flash one from youtube or one on my computer, it is extremely fast ( x20) and there is no sound. I tried booting on another computer and everything worked fine. I have no clue what is wrong. I have installed and reinstalled flash. I tried different movie players. Nothing worked.

I would appreciate any help anyone would be able to give me on this.

Thanks.

---

### Post by gufghur on 2012-02-08
Hi, I've got the same, or maybe the same problem, and am looking for a solution to. So i cant be of help to you. In my case the problem came either by updating my system, or by watching a movie on youtube (but i don't have enough knowledge about viruses and all that to know if this is possible).

It's a pity nobody seems to have a clue here about what's wrong.

---

### Post by Johnny Buffalkill on 2012-02-09
I had this happen once.  I don't remember exactly what I did to fix it, but as its been a day without replies, I'll give it a shot.

It seems like this was actually a sound issue, where the video was trying to catch up or something like that.  A "magic" fix for some of these issues is to either delete, or rename the home/.pulse folder.  Rename it, then log out and back in and see if that fixes things.  Your sound settings will all be reset to default.  If it doesn't fix anything, you can always change the folder name back.

---

### Post by xylophone on 2012-02-14
I did what you suggested, and now the entire OS doesn't work. All it does is load the default background without any icons or the bar across the top. I can't even shut it off without doing it manually. Thanks. 

I think I'll just try to reinstall Ubuntu 11.10. Hopefully that will work.

@gufghur What OS are you running?

---

### Post by Yellow Pasque on 2012-02-14
> **xylophone said:**
> I did what you suggested, and now the entire OS doesn't work.

I find it hard to believe that renaming/deleting ~/.pulse did that. Are you sure you didn't typo the command and move/delete your /home folder?

---

### Post by gufghur on 2012-02-17
Hi Xylophone, sorry for reacting so late. Have been very bussy the last days.

I'm working on 11.10 32bit.

It's a pity there's so little reaction to this thread. I start another one ... would like to get this solved.

---

### Post by xylophone on 2012-02-17
Oops.

I couldn't find the .pulse (I now know that the dot means hidden), so I deleted /home (don't know what I was thinking). I had to reinstall Linux, so I used 11.10. Flash videos (youtube) play but the sound and video are really jerky to the point of not being able to watch anything. It isn't my connection because I let the video load all the way first (my connection is very slow). 

please post a link to the new thread.

---

### Post by bludshot on 2012-02-17
I have a computer where the video and sound in youtube is jerky and it's not because of my internet connection - it's because my computer is old and can't handle doing steaming videos (unless they are 240p... )  So, it may be that things are functioning properly and you have an old crummy machine??

---

### Post by Johnny Buffalkill on 2012-02-18
@xylophone:  Sorry about that - I should have been more clear.  I've been using Ubuntu for about two years now and I'm starting to forget what is intuitive, and what would be totally foreign to new users.  I hope you didn't permanently lose any data.

If you did a re-install your .pulse folder would of course be re-created, so if you are still having the same problem, then it must be caused by something else.  I'm out of ideas now, but maybe if you post your hardware specs, and also try some different video file types, like throwing a DVD in there and see what happens it might give some more specific information that someone can use to diagnose this.

---

### Post by gufghur on 2012-02-19
Hi Xylo,

this is the thread for my post. sadly it didn't get any answers up to this moment.

[http://ubuntuforums.org/showthread.php?t=1927218&highlight=movie](http://ubuntuforums.org/showthread.php?t=1927218&highlight=movie)


One of the comments on your thread was about this .pulse file ... I had no idea as well that the dot means its about a hidden file. Have you been able to solve the issue by deleting .pulse?
By the way, as you describe your problem now, it seems to me entirely the same issue as I have now.

Hope to see some movies again soon!

---

### Post by Johnny Buffalkill on 2012-02-19
Xylophone did a reinstall to 11.10, so that would have restored the .pulse folder, as well as everything else.

You don't have to delete the .pulse folder, you can just rename it.  Either way, once there isn't a .pulse folder,  a new one will be generated with default settings, so you would have to redo any settings.  I should have been more specific about what to do with it.  If you go into your home folder in your file browser, and under 'view' check hidden folders you'll see all the hidden folders, which have a '.' in front of them (sounds like you figured that out already).  Since its your user folder, you don't need root permission, so you can just right click and select rename.  You might need to logout and back in or even restart.  If it doesn't fix anything you can always rename the original folder back to '.pulse'.  

Seems like we're 0-1 on this fixing anything, but if all you do is rename .pulse, you can always name it back if it doesn't do what you want.

---

### Post by gufghur on 2012-02-20
Thanks a lot!!

:popcorn:

this did it indeed. Congratulations to you. I'm of to watch a movie now.

---

### Post by angiolucci on 2013-01-14
Thanks [Johnny Buffalkill]("http://ubuntuforums.org/member.php?u=1317984"), I was having this problem (fast video, mute sound) after updating my kernel version at Linux Mint 14. Renaming/deleting the ~/.pulse folder and rebooting the system solved my problem.

---

