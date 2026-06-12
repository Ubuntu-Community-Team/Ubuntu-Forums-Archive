---
title: "Samsung 226BW widescreen resolution issues in Gutsy"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by speirint on 2007-11-12
The formatting should be 1680 x 1050, and is currently not recognized in gutsy.  This problem was resolved for me earlier a month or two ago by pasting in this line to the terminal:

sudo aptitude install xserver-xorg-video-intel

Problem is, it hasn't done me any wonders so far and I'm seeing everything stretched out and fuzzy on my monitor.  Is there a way to inform the guys working on gutsy to include this resolution (I assume go to launchpad)?

[edit]
When going to screens and graphics under administration and selecting the specific monitor model that I have from the menu (Samsung SyncMaster 227 BW widescreen), the default settings that are available are consistantly incorrect and strange:


1024 x 768
1280 x 1024
1920 x 1200

Again, I must reiterate that the correct formatting is 1680 x 1050.


[end editation]
I really do believe this might be an issue I need to bring up to the guys at launchpad, if so, I'll dig up whatever my account was to report it there then.


Here's my other post to someone that had a similar problem in Fiesty:

Hey Jpross, if you still have that monitor and got it working-and haven't upgraded to gutsy yet, don't do it. I have the same problems all over again and now there are no other posts that I know of that mention this issue.

I tried using the (which is what successfully made the initial correction for my monitor in feisty earlier):

sudo aptitude install xserver-xorg-video-intel

again and it doesn't work in Gutsy, someone must not have configured the right resolution for 
Gah! As an aside, my sound still doesn't work right... Gah!

---

### Post by trappist on 2007-11-14
You probably need to go back to the i810 driver, and fix it the same way you did in Feisty.  That's what I had to do for gutsy.

---

### Post by ken_vh on 2007-12-10
I might have a solution for you at my posting here:
[http://ubuntuforums.org/showpost.php?p=3928636&postcount=17](http://ubuntuforums.org/showpost.php?p=3928636&postcount=17)

---

### Post by bvanaerde on 2007-12-17
I'm subscribing to this thread, as I'm thinking of buying this screen :)
Thanks for already giving a solution...

---

