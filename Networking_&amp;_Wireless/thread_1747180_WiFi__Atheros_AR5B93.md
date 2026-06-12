---
title: "WiFi : Atheros AR5B93"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by Dr. Quack on 2011-05-02
Hi!

My computer was, until recently, running windows 7. It crashed at the beginning of the weekend, and I decided to switch to ubuntu.

Everything seems to be working fine apart from the wireless card.

My computer is an Acer Aspire 5251-1513, and my wireless card is an Atheros AR5B93.

I've already searched and tried multiple solutions in the forums, and none of them seem to work for me. Maybe I'm not doing something right?

Thanks for your reply!

---

### Post by Decline- on 2011-05-02
I had some trouble with my Atheros card as well. Have u tried installing wicd? Run "sudo stop network-manager" and run wicd...

---

### Post by Dr. Quack on 2011-05-03
Hi again!

I found a solution that seems to be working so far in this thread: [http://ubuntuforums.org/showthread.php?t=1744892]("http://ubuntuforums.org/showthread.php?t=1744892")

First off, I entered this and came up with two different things, one was acer_wmi:
```
sudo rfkill list
```
The result was that I had a 'Soft block' by acer_wmi. I tried to unblock it with this command:
```
Sudo rfkill unblock all
```
After that had no effect, I tried what the forum the forum post (link above) said I should do, and it totally worked:
```
sudo rmmod acer_wmi
```

I really hope this works for anyone else who might have this problem!

Dr. Quack

---

### Post by Dr. Quack on 2011-05-03
Unfortunately, this solution is only temporary. The command needs to be executed a EACH BOOT.

I created a new thread to try and solve this problem (since I am but a humble noob end user):

[http://ubuntuforums.org/showthread.php?p=10765562#post10765562](http://ubuntuforums.org/showthread.php?p=10765562#post10765562)

---

### Post by perspectoff on 2011-05-03
What happens when you install Wicd and remove Network Manager?

Do the problems persist?

---

