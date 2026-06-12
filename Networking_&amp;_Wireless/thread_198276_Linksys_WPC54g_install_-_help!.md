---
title: "Linksys WPC54g install - help!"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by mmmpancakes on 2006-06-16
I successfully installed Ubuntu onto my laptop, but need some step by step instructions on setting up my wireless. I have a WPC54G PCI wireless card. As detailed as possible would be a huge help. Thanks in advance!

---

### Post by x64Jimbo on 2006-06-17
Here's a thread with someone who got it working. First result for "linksys wpc54g ubuntu" in Google:
[http://www.ubuntuforums.org/showthread.php?t=5645](http://www.ubuntuforums.org/showthread.php?t=5645)

---

### Post by mmmpancakes on 2006-06-17
[QUOTE=x64Jimbo]Here's a thread with someone who got it working. First result for "linksys wpc54g ubuntu" in Google:
[http://www.ubuntuforums.org/showthread.php?t=5645](http://www.ubuntuforums.org/showthread.php?t=5645)[/QUOTE]

I looked at that, but I'm having difficulty in ndiswrapper. I don't know how to install it.

---

### Post by noname101 on 2006-06-17
Just type this in a terminal:
```
sudo apt-get install ndiswrapper-utils
```

---

### Post by mmmpancakes on 2006-06-17
[QUOTE=noname101]Just type this in a terminal:
```
sudo apt-get install ndiswrapper-utils
```[/QUOTE]

One more quick question. I just got updates and rebooted. Now, it reboots into a command line. Do you know how I can configure it to boot into the graphic interface? Thanks!

---

### Post by noname101 on 2006-06-17
Try sudo dpkg-reconfigure gdm and it'll ask you if you want to make it the default display manager.

---

### Post by mmmpancakes on 2006-06-17
Ok did that....I get "action reload failed" after it asks me for my password, then just goes back to the command line.

---

### Post by noname101 on 2006-06-17
Maybe try to reinstall it:
```
sudo apt-get remove gdm
sudo apt-get install gdm
```

---

### Post by mmmpancakes on 2006-06-17
Ok to solve this problem I did startx and that booted it into graphical mode...any idea how I can make this the default?

---

### Post by noname101 on 2006-06-17
Try to reinstall gdm first. If that doesn't work try [this thread]("http://ubuntuforums.org/showthread.php?t=187177&highlight=action+reload+failed").

---

### Post by mmmpancakes on 2006-06-17
Did the reinstall, and I still get the reload fail. Let me try the thread. 

Noname101, thanks a lot for your help. You're being very patient.

---

