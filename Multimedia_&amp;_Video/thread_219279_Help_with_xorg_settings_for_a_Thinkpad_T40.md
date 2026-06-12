---
title: "Help with xorg settings for a Thinkpad T40"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by bepatient on 2006-07-19
Here is the issue. I've just installed Dapper onto this T40 and have a couple of video issues. 

As many have already noticed, the resolution sets itself to max 1024x768. If I were only going to use this laptop without attaching to my KVM, ever, this would be perfect.

However, that is NOT how I planned on using the machine. It spends much time attached to the kvm, lid down, running on a 19 inch LCD. 

I do not want to run it dual monitor. If I did, there are plenty of descriptions out there that explain how to do this.

What I would like to do is have Ubuntu behave (hold your breath and please don't flame me) like Windows wrt the video behavior.  When I close the lid under xp and have the 2nd monitor attached, it automatically switches to the 1280x1024 setting. Open it and activate the primary lcd and voila, its back to 1024.

Can I do this?? or am I going to be forced to manually change and remember to change back before unplugging from the kvm (so as not to fry the lcd on the lapper by blasting it with 1280x1024 mojo).

Please help.

---

### Post by bepatient on 2006-07-20
Update to previous message. I ran dpkg-reconfigure to add the 1280 setting and it failed to populate the "change screen resolution" box. SO, now it appears that my x settings are completely ignoring the config file in favor of keeping me at 1024.

---

### Post by tseliot on 2006-07-20
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by bepatient on 2006-07-20
All well and good to fix my dpkg issue, which is due, most likely, (thanks to log review) of the vertical refresh not being set correctly.

However, I don't think that the initial question is addressed at all in any of that document, nor in any of the links from that document.

Agree thats a good link if my issue was only one of correcting a simple resolution issue, but the orignal post is the pressing issue. How do I design the xorg.conf file to recongnize on the fly which monitor is which and to set the resolution accordingly.

Seems like it should be possible, I just don't know how...and after a thorough search of this board and news...it seems to be a common question that has uncommonly gone unanswered.

---

