---
title: "How do I get streaming HD video from ABC's website?"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by diablo75 on 2008-02-17
I want to watch Lost on ABC's website, but it says it requires windows to install their plugin.  Anybody know a work around?

---

### Post by Metaljaz on 2008-02-17
Read through the first link make sure that you have the proper plugins installed and you should be okay. Then take a look at the second link for more information that maybe helpful. I checked out the website and can view the videos just fine with firefox. I do have all the plugins installed.

[https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo](https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo)

[https://help.ubuntu.com/community/RestrictedFormats#head-79bfba9a0e96d62a622a47430239a1d49454c953](https://help.ubuntu.com/community/RestrictedFormats#head-79bfba9a0e96d62a622a47430239a1d49454c953)

---

### Post by diablo75 on 2008-02-17
Please try to stream one of ABC's shows from abc.go.com

They have install this "move media" (I think that's what it was called) plugin.  I managed to get it to work on a Windows version of Firefox running on top of wine but playback was too jerky....

---

### Post by drcookie on 2008-02-17
I've tried getting the move network plugin to work under Ubuntu myself with no luck.  One thing that I didn't try was installing IE under Ubuntu.  There is some software that helps get everything installed called IEs4Linux.  The only caveat would be that you would be dealing with the IE licensing, which is a *little* more restrictive than...lets say firefox.

I haven't tried it myself, but here is a walkthrough: 

[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

Let me know if you have any good results, with IEs4Linux or otherwise, as I too would love to get the move network content to work under linux.

---

### Post by rosegarden78 on 2008-02-17
Search the forums for "abc.com streaming" I posted the solution here:
[http://ubuntuforums.org/showthread.php?t=679165&highlight=abc.com+streaming](http://ubuntuforums.org/showthread.php?t=679165&highlight=abc.com+streaming)
Note: Max out your RAM 1 Gb+ and I'm totally <u>Lost</u> you should try RecordMyDesktop.

---

### Post by diablo75 on 2008-02-18
> **rosegarden78 said:**
> Search the forums for "abc.com streaming" I posted the solution here:
[http://ubuntuforums.org/showthread.php?t=679165&highlight=abc.com+streaming](http://ubuntuforums.org/showthread.php?t=679165&highlight=abc.com+streaming)
Note: Max out your RAM 1 Gb+ and I'm totally <u>Lost</u> you should try RecordMyDesktop.

I already did that, and yes, it worked.  But playback was less than desirable (I need a faster CPU).  I have other ways of getting my fix of Lost.  Though if ABC would put out a Linux binary of that Make Media plugin, everybody would be happy (including ABC in the long run, since Linux is on the rise in popularity, and so would follow a Linux based viewership).  They'll do something about it eventually... on of these years.

---

### Post by Metaljaz on 2008-02-18
> **diablo75 said:**
> Please try to stream one of ABC's shows from abc.go.com

They have install this "move media" (I think that's what it was called) plugin.  I managed to get it to work on a Windows version of Firefox running on top of wine but playback was too jerky....

I missed that..sorry. I get the same message as others. Still trying.

---

### Post by rosegarden78 on 2008-02-19
I think abc.com servers are based in Los Angeles.  Visit [www.speedtest.net](www.speedtest.net) to check connection speed.  Then check System Monitor to see if you have network activity.  You cannot multi-task or ever move the Wacom tablet without draining CPU.  My CeleronM 1.4 can only play Lost in Normal screen size which is fine for me.  Big and full screen cannot be handled by the Inspiron 1200 with 1280 MB of memory.  Just sit back and watch and don't fiddle with the mouse cursor or use anything else that drains the CPU even try disabling the swap file using sudo swapoff /dev/sda5 at th terminal.  Anything you can do to ease the load will help.  Only disable swap file if you have more than 1 GB of memory.

---

