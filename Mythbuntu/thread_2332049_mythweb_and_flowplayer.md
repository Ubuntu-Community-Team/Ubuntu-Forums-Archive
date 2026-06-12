---
title: "mythweb and flowplayer"
date: 2016-07-27
forum: Mythbuntu
---

### Post by benlyboy on 2016-07-27
hi all.. 

I'm a long time user and big fan of mythtv and mythbuntu, i miss a feature that used to work on earlier versions on myth but hasn't for me since maybe before 12. that feature is a embedded  player in mythweb to watch my recording when I'm away from home. It wasn’t perfect but it worked. But now the only wiki i can find on it says that this wiki in out of date and not compatible with.28

When I look at the page on mythweb I used to set up this feature. I see this.

Fatal error: Uncaught Error: Call to undefined function split() in /usr/share/mythtv/mythweb/modules/mythweb/tmpl/default/set_flvplayer.php:26 Stack trace: #0 /usr/share/mythtv/mythweb/modules/settings/handler.php(60): require_once() #1 /usr/share/mythtv/mythweb/mythweb.php(35): require_once('/usr/share/myth...') #2 {main} thrown in /usr/share/mythtv/mythweb/modules/mythweb/tmpl/default/set_flvplayer.php on line 26

Has anyone still got this feature working?
 Thanks for any feed back

---

### Post by Espryon on 2016-07-28
> **benlyboy said:**
> hi all.. 

I'm a long time user and big fan of mythtv and mythbuntu, i miss a feature that used to work on earlier versions on myth but hasn't for me since maybe before 12. that feature is a embedded  player in mythweb to watch my recording when I'm away from home. It wasn’t perfect but it worked. But now the only wiki i can find on it says that this wiki in out of date and not compatible with.28

When I look at the page on mythweb I used to set up this feature. I see this.

Fatal error: Uncaught Error: Call to undefined function split() in /usr/share/mythtv/mythweb/modules/mythweb/tmpl/default/set_flvplayer.php:26 Stack trace: #0 /usr/share/mythtv/mythweb/modules/settings/handler.php(60): require_once() #1 /usr/share/mythtv/mythweb/mythweb.php(35): require_once('/usr/share/myth...') #2 {main} thrown in /usr/share/mythtv/mythweb/modules/mythweb/tmpl/default/set_flvplayer.php on line 26

Has anyone still got this feature working?
 Thanks for any feed back

Check the mythtv wiki, thats how I got most of the features I wanted working i.e. [https://www.mythtv.org/wiki/MythWeb](https://www.mythtv.org/wiki/MythWeb)

---

### Post by benlyboy on 2016-07-28
I know only a very little about coding, I played with basic 30 years ago, and now have look at python, but the truth is i couldnt code my way out of a wet paper bag.  But I took a look at this file /usr/share/mythtv/mythweb/modules/mythweb/tmpl/default/set_flvplayer.php and I think I found a couple of problems.

First the fill is looking for a file named ffmpeg that I believe is called actually called mythffmpeg.

The second thing is that after doing some research I have found that the Split() statment was removed from php 7.0.0 so I think this whole file would need to be rewritten. 

So i'm thinking that till someone that knows a lot more than me decides to fix it this feature is dead. which is to bad:(

---

### Post by benlyboy on 2016-08-13
Hi all :)

I thought I would update this and set it as solved. I got flowplayer working in mythweb last night. 

This is what I did

First up as I said in the above post all the problems relate to the file /usr/share/mythtv/mythweb/modules/mythweb/tmpl/default/set_flvplayer.php, 

There are two main problems.

First is that the program or script (to be honest not sure which is the right term) is looking for a file called ffmpeg that I believe is actually called mythffmpeg. This was an easy fix, i simply went in and made a copy of the file and named this copy ffmpeg. I kept the original as it maybe need somewhere else.

The second thing is that the Split() statement was removed from php 7.0.0 . I know nothing about PHP so I went looking on line for info, i found that split() had been replaced with explode(), but i couldn&#8217;t find much on if they were formatted the same, in the end I just replaced Split with explode and it just worked, so i guess they are formatted the same:) .

Hope this helps someone else

---

