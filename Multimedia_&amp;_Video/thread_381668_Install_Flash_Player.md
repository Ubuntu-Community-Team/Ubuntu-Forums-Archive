---
title: "Install Flash Player"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by novavon on 2007-03-11
I understand that there are many other posts regarding flash plug-in for Firefox on UBUNTU 6.10 edgy. I've tried to install it for 2 weeks now. I tried every possible technique that I could find on Google. However, I was unable to get flash player running.

I tried...  (many times reinstalling UBUNTU several times, updating and upgrading several times)
moving ".so" file in to /usr/lib/firefox/plugins
linking it (ex. ln -s *.so)
automatix2
.bin install
trvino's repositories
putting it in to /home/(username)/.mozilla/plugins
and few more techniques, but all of them was BULL.

I would appreciate any comment regarding this issue (an ultimate one).

---

### Post by yabbadabbadont on 2007-03-11
You wouldn't happen to be using a 64bit version of Ubuntu would you?  If so, there are very limited options for using flash.  I believe most involve setting up a 32-bit chroot environment.

---

### Post by chewearn on 2007-03-11
Here is how I did it on my system:
Go to a website with flash.  Firefox will pop-up a bar at the top, saying that a plugin is needed.  I just click on the icon to the right, everything is straight forward after that.

---

### Post by novavon on 2007-03-11
Right...
I use AMD64
I just found [this link on ubuntu forums]("http://www.ubuntuforums.org/showthread.php?t=341727&highlight=flash+player").

and I finally figured it out.
It's working.:guitar:

---

