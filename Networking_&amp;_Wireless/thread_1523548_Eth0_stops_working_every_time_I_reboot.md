---
title: "Eth0 stops working every time I reboot"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by Poparad on 2010-07-03
I've been using Ubuntu for about a month with no trouble, and out of the blue today my internet stopped working.  I booted from the Live CD and was able to get online, and found a thread with this command:

```
sudo dhclient -r eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```When I do this, suddenly my internet works again.  However, I have to do this *every* time I start up Ubuntu, which is a major pain in the ***.  I have absolutely no idea what caused this or what I should do to fix this.

Also, although I found a way to disable this, Firefox was always automatically in "Offline Mode" whenever I started it, even after I got the internet connection working.  This never happened before today.

The only thing that I was doing today was trying to get my DVD player to read a DVD.  I installed 'libdvdread4,' but that was it, and I don't see how that would screw up my ethernet card.[IMG]chrome://dictionarytip/skin/dtipIconHover.png[/IMG]

---

### Post by Poparad on 2010-07-03
Ok, I think I may have solved it.  I saw this thread:

[http://ubuntuforums.org/showthread.php?t=1523360](http://ubuntuforums.org/showthread.php?t=1523360)

My 'Notification Area' button had disappeared somehow (I noticed this when I booted from the Live CD).  I added that back to the panel, as sure enough as the other thread said, the networking was disabled.

---

### Post by Poparad on 2010-07-03
Yes, that solved it.

---

### Post by Iowan on 2010-07-03
CONGRATS!!!
[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is how to mark the thread [SOLVED]. :)

---

