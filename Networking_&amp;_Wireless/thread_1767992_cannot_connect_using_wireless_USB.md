---
title: "cannot connect using wireless USB"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by moisea on 2011-05-26
hi i just got a P4 PC did a clean installation of xp (wireless connection works fine), then made a dual boot with ubuntu 10 latest version (No wireless connection).
Then went to this [link]("http://ubuntuforums.org/showthread.php?t=972060")followed the steps nothing happened.
My WUSB600N folder has been extracted on my Desktop and I am not sure that I've done this bit  "and navigate to the newly created WUSB600N folder" because I just drag the folder to the terminal. I am not sure what they meant by _navigate to the newly created WUSB600N folder_. Anyway, did not get ANY ERROR MESSAGES. followed the steps and nothing.
True newbie needs help. Thanks.

---

### Post by StrayEddy on 2011-05-26
To open a terminal:

Ctrl+Alt+T

To navigate in a terminal:

ls (list files and folders where you are)

cd (navigate threw folders)


When you extracted the folder it should create a new folder with the same name with all files in it.

Go into that folder and right click -> open a terminal here

---

### Post by chili555 on 2011-05-26
Did you notice the date on that post? 2008? About 108 years in Linux time. The module rt2870sta is built in to recent versions of Ubuntu but there is often a driver conflict. Please open the terminal and run and post:```
lsusb
```We'll tell you how to "navigate to the newly created WUSB600N folder" later; it's probably not needed here.

---

