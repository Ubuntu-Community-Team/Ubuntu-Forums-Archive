---
title: "Issue viewing Flash/Apreso lecture recording system"
date: 2008-09-15
forum: Multimedia Software
---

### Post by dashdave on 2008-09-15
Hi! For my university, lectures are posted online using Adobe Flash Player. The way they are done is there is sound associated with the lecture that plays, while a powerpoint slide is visible on the screen. On the side is a bar to navigate from one powerpoint to another. I am having an issue when viewing these presentation in that the powerpoint slide part of the video only shows the left 1/3 of the slide, tiled 3 times horizontally across the place where the entire slide should be. I can still use the navigation sidebar, and when the instructor's mouse moves over the left 2/3 of the slide I can see what should really be in those portions, but only for a short amount of time before it reverts to being tiled. Does anyone know how this kind of problem could occur? I know people using windows with firefox haven't had the problem, so I was thinking it was some problem with the settings of flash player in ubuntu. Also, I tried upgrading to flash player 10 but that did not help. Supposedly flash player 7 works with this, but I haven't be able to find it and am kind of shaky on how to install, and am also unsure if it would work with google video. Any ideas?

A screenshot I took of the problem is here: [http://img.photobucket.com/albums/v418/dhesve89/Screenshot.png](http://img.photobucket.com/albums/v418/dhesve89/Screenshot.png)
Thanks for the help!

---

### Post by swegner on 2008-09-28
Hi dashdave,

I was just looking for a solution to the same problem.  My university has a whole catalog of lectures for viewing online, but there is a problem that the video content is strangely tiled and overlapping in the viewer.  I did a quick google search, and found a reference to confirm the behavior:

[https://agora.cs.uiuc.edu/display/I2CS/2007/08/27/Apreso,+Flash+on+Linux](https://agora.cs.uiuc.edu/display/I2CS/2007/08/27/Apreso,+Flash+on+Linux)

From the page:
> "After testing Flash 8 and 9 playback we have found a bug in Flash player on Firefox in all platform of linux. We are currently opening case with Adobe see if they will fix this issue. The only workaround we currently have is to rollback to Flash 7 for linux."

Unfortunately, Ubuntu currently ships flash 9, and I'm not aware of any easy way to roll-back to version 7.  I believe flash 10 is slated for Intrepid which releases in October-- let's hope it gets better then.

I think I'm also going to try installing a different Flash package (other than flash-nonfree); I'll let you know if I have any success.

---

