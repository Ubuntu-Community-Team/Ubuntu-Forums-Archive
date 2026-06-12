---
title: "Youtube won't go full screen"
date: 2008-07-11
forum: Multimedia Software
---

### Post by Bucky Ball on 2008-07-11
Hi all. I have the same problem as described on this closed thread:

[http://ubuntuforums.org/showthread.php?p=5301574#post5301574](http://ubuntuforums.org/showthread.php?p=5301574#post5301574)

It didn't get me anywhere. Compiz is mentioned but I know nothing about it. Wondering if anyone has any simple solution.

Hit full screen button in youtube, full screen for split second then back to embedded in youtube page. Annoying. Doesn't seem to happen with anyother software so wondering if this might be a Firefox setting. Have looked about but no luck there either (yet!).

I will keep crawling for info but any ideas appreciated.

---

### Post by designerinc on 2009-10-10
if the screen is not going to full screen mode then right click on the screen and on the flash Display setting uncheck the Enable Hardware Acceleration and wala! the screen does go to the full screen mode magic,aye.no simple google search gets you a lot of answers.

It worked for me

---

### Post by Bucky Ball on 2009-10-10
...

---

### Post by schizferatu on 2011-08-14
not long solved for me... here at August 14th 2011 I greatly appreciate it:guitar:

---

### Post by safinr on 2011-09-20
That didn't work for me, I'm still searching for a solution. This must have something to do with the Nvidia driver/settings

---

### Post by safinr on 2011-09-20
found another solution on youtube ```
http://www.youtube.com/watch?v=SeO8YytqEKE
```
In terminal
```
sudo mkdir /etc/edobe
sudo su
sudo echo "OverrideGPUValidation =1" >> /etc/adobe/mms.cfg
```

That worked for me.

---

