---
title: "Gthumb opens Places"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by markthecarp on 2010-09-21
Today I installed gthumb on Maverick. Now everything in the Places menu opens in gthumb instead of Nautilus. Including connecting to remote server.

That's the problem in a nutshell. I installed gthumb because it is what I'm used to and I like it. Sequence of events: a friend that doesn't have a computer came by asking to put some pictures of his son on his Facebook page. (yeah I know, no computer but he has a Facebook page) I opened the photo cd w/Nautilus; moved five files to a directory on a thumbdrive; realized I didn't have gthumb; installed gthumb; right clicked the directory on the thumbdrive and opened it with gthumb; used gthumb to rotate some images and resize all; uploaded to Facebook.

The only step that I can see that may have changed a default setting was opening that directory with gthumb. I've looked at Preferred Applications and Configuration Editor for ways to change this behaviour without success. I have searched this forum for similar issues and found none. I have not searched Launchpad yet.

I suspect the problem can be solved by changing something with the Configuration Editor.

TIA,
-Mark

---

### Post by mc4man on 2010-09-21
simple 'fix'
[http://ubuntuforums.org/showthread.php?p=9870576#post9870576](http://ubuntuforums.org/showthread.php?p=9870576#post9870576)

If you want to 'pre-anticipate'  other apps from being set as default 
[http://ubuntuforums.org/showthread.php?p=9870613#post9870613](http://ubuntuforums.org/showthread.php?p=9870613#post9870613)

bug that if it goes anywhere will most likely be a circle
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833)

---

### Post by markthecarp on 2010-09-22
> **mc4man said:**
> simple 'fix'
[http://ubuntuforums.org/showthread.php?p=9870576#post9870576](http://ubuntuforums.org/showthread.php?p=9870576#post9870576)

If you want to 'pre-anticipate'  other apps from being set as default 
[http://ubuntuforums.org/showthread.php?p=9870613#post9870613](http://ubuntuforums.org/showthread.php?p=9870613#post9870613)

bug that if it goes anywhere will most likely be a circle
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833)

Thanks mc4man; those explained the situation perfectly.

A friend (mikeh789) on my LoCo IRC channel found...
[https://answers.launchpad.net/ubuntu/+source/nautilus/+question/46631]("https://answers.launchpad.net/ubuntu/+source/nautilus/+question/46631")

-mark

---

