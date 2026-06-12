---
title: "Devede small output size"
date: 2008-09-16
forum: Multimedia Software
---

### Post by klemperal on 2008-09-16
I wasn't sure where to post this so forgive me if there is a more appropriate place.  I'm using Devede to convert .avi, .mp4 and .flv into .iso for DVD-5s.  The output size is supposed to be around 4.7 gigs but always ends up being around 706 mb.  Anyone familiar with Devede that might know what the problem is?  If not, can anyone suggest another good program to convert various video to DVD?

---

### Post by ksennin on 2008-09-16
I am having the same problem.  Normally an *.avi file converted to dvd format would go about from 700mb to 4gb or more, using programs like ConvertXtoDVD. 

The main screen shows a status list with bitrates and estimated size of 3938MBytes, with 92% disk occupation reported, yet the resulting ISO file is 1.5GB.

Now, I hate having to reboot the pc into windows just to do dvd clip compilations, so I really wanted to use devede, and the interface seemed friendly enough, but the small ISO file size resulting makes me fear that the change of format is not very successful.  I can see the movie alright, but I would have to do a double burn on the different programs to compare final resolutions.

I also tried ManDVD and also got small iso files, besides getting two coasters in direct burns, so I guess devede is the best option for now, but I would really like to know if I am doing something wrong.

---

### Post by tonybeccar on 2008-12-07
I am having the same problem here. I did several tests. I converted a movie that was suposed to weight 4000 megabytes, but the final iso final weighted 2800 megabytes. So there is approximately a 40 percent of difference in sizes. What i did was to increase the video bitrate in 40 percent... No succes.. The ISO file still is too small. Obviously this matter affects the final quality of the movie. It sucks.. Anyone knows if some previous version of devede hasn't got this issue? I know this post is quite old, i hope someone would help.. thanks!

---

### Post by SeePU on 2008-12-10
Hey, Tony, I have the same problem.  I hope you get a reply.

I was getting 81% of the disc occupied (instead of 92%) and the final size of iso was 1.6GB so basically the same thing.  

The last time I had 3.5GB so maybe it was getting better but I believe the final compression/encoding should be around 4.3GB or so?  

I'm not really familiar with the process but I hope someone who has experience with devede and/or other programs including the process can comment.  Hopefully...

---

### Post by notquitestr8t on 2008-12-10
I'm in the same boat. I just got a DL DVD burner. The latest version of Devede shows and 8.5 DVD will be full after conversion but it's never gone over 3.2 GB. In addition, the latest version does not allow you to remove the title and my DVD player displays only that and nothing else so I may have to go back a version or two. I'm willing to boot into Windows if I have to, to get the quality I am looking for. What is the best program for converting in Windows XP?

---

### Post by RainmanATX on 2008-12-26
I have been having this problem for quite awhile now.  From what I have found via good'ol google, is that mencoder seems to be ignoring bitrate settings passed to it by DEVEDE.  I recall that there was a thread on Mplayer's forum (I do believe the user with the issue was using a different 'frontend' for mencoder though) where a moderator addressed the issue as thus;  "...if the source file being converted does not have enough inherent quality to achieve the bitrate set by the user, it will not 'pad' the file with zeros, it will simply encode at the highest possible bitrate for the given source material."  Personally, I have tried stepping the DEVEDE versions back to 3.6, the last version I remember working properly, it was a no go.  So, either mencoder is 'fixed', where it will 'pad' the file, or someone lets us know how to load an older version of mencoder.  I will post if I find anything else, good luck.    :confused:


From what I can tell, no matter what I set the bitrate, mencoder seems to choose VBR of around 2000.

---

### Post by ksennin on 2009-02-07
> **notquitestr8t said:**
> I'm in the same boat. I just got a DL DVD burner. The latest version of Devede shows and 8.5 DVD will be full after conversion but it's never gone over 3.2 GB. In addition, the latest version does not allow you to remove the title and my DVD player displays only that and nothing else so I may have to go back a version or two. I'm willing to boot into Windows if I have to, to get the quality I am looking for. What is the best program for converting in Windows XP?
ConvertXtoDVD is the best and simplest conversion program. It can deal with different regional formats, compile different formats in single compilation, give different types of menus with text, or animated previews, etc.  However, it is propietary.  Well worth the cost, though.

---

