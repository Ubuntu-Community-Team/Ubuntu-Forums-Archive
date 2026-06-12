---
title: "Enable wireless greyed out"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by Invalid Opcode on 2010-09-16
Anybody know what is going on with the dell-laptop module that is causing the system to think the hardware disable is on?

Today for the first time, all of my wireless connections stop working.  Doing all the research and debugging ([http://ubuntuforums.org/showthread.php?t=1423477&page=2](http://ubuntuforums.org/showthread.php?t=1423477&page=2)), the only way to get it back working was to disable the dell-laptop module and put it on the blacklist.conf.

Anybody know why it would work since the initial release of 10.04 and suddenly stop working?  I keep my machine up date but could not pinpoint the update that relates to the network manager, kernel, or dell stuff.

[]("http://ubuntuforums.org/showthread.php?t=1423477&page=2")

---

### Post by as29 on 2010-09-17
I'm facing a similar problem. Unfortunately my problem goes way beyond:
[http://ubuntuforums.org/showthread.php?t=1576081](http://ubuntuforums.org/showthread.php?t=1576081)

Do you have the same issue?

---

### Post by RowanEmslie on 2012-04-23
I have the same problem but I have a Packard Bell Etna-Gl. I haven't seen anything that has helped me so far. I tried to change the NetworkManager.state file into all 'true's but it says I don't have permission (I don't understand why not - I am the only user of this laptop). I'm a almost complete beginner. My wireless has worked fine for the last 6 months, only from yesterday it stopped detecting wireless networks. I'm pretty sure it's because my wireless is disabled but a) my wifi button on my keyboard doesn't function anymore and b) I can't enable it in the network manager. Please help!

---

### Post by coffeecat on 2012-04-23
Old thread closed.

@RowanEmslie, you will be able to get help in the thread you started here:

[http://ubuntuforums.org/showthread.php?t=1963969](http://ubuntuforums.org/showthread.php?t=1963969)

---

