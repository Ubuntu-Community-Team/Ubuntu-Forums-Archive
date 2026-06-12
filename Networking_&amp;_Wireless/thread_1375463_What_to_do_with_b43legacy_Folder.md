---
title: "What to do with b43legacy Folder"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by Uruz on 2010-01-07
Got a desktop computer and have been working to enable wifi on it. I ran into some trouble (you think I would have figured out how to do it after the first 5 times), and now I'm stuck. I b43-fwcutter'd wl_apsta.o and ended up with a folder full of .fw files in my /home/ folder. The question now is, what do I do with it? I've never enabled wifi using b43-fwcutter and I've only done it once using ndiswrapper (don't ask how I managed the other times, I don't know).

Note: I don't seem to have a "restricted drivers" button like I did when I installed on my laptop.

I'm using 9.04

Thanks and such,
Uruz


(PS: File Viewer crashes when I insert a CD and won't work again until I remove the CD. Anyone know what this is?)

---

### Post by chili555 on 2010-01-08
Assuming you have a folder at */home/user_name/b43legacy* containing a lot of .fw files, open a terminal and do:```
sudo cp ~/b43legacy/* /lib/firmware/b43legacy/
sudo chmod 644 /lib/firmware/b43legacy/*
sudo chown root:root /lib/firmware/b43legacy/*
ls -al /lib/firmware/b43legacy
```Are all the firmware files there all nice and happy?

---

