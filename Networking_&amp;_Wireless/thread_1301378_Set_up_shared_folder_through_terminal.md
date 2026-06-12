---
title: "Set up shared folder through terminal"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by donkeypuncharex on 2009-10-26
I recently downloaded a driver that has stopped me from being able to view my desktop. But if i type in my username and password I can access my shared folders from my other computer. If I could just take the info from my shared folders and put them on my laptop I wouldn't mind doing a fresh install. My only problem is one of my primary folders (my music folder) is set up as a read only folder, so I am not able to take the information and paste it to my laptop. 

Is there a way I can set up this folder to be a read&write folder through the recovery mode terminal?

Please any help with this process would be fantastic.

---

### Post by donkeypuncharex on 2009-10-26
Any help?

---

### Post by ST3ALTHPSYCH0 on 2009-10-26
I think the command you're looking for is:  sudo chmod -R 777 \mydirectory

where "mydirectory" is obviously the name of your directory. There's a beginner's guide to terminal in one of the forums around here that lists basic commands, but I don't remember off hand where I found it. The disclaimer here is that I'm a n00b,m and this could be incorrect, but as I understand it this command changes the permission of the directory tree to read/write access for all users.

Good luck. BTW, have you tried reinstalling your desktop? I don't know the command, but I know it's possible to do.

---

### Post by donkeypuncharex on 2009-10-26
I have not tried to reinstall it. I also don't know the command. If you find out please post back on this thread.

---

### Post by donkeypuncharex on 2009-10-27
Also thank you for the command. I am now able to take all of my music which is the one thing I was very concerned about losing.

---

### Post by ST3ALTHPSYCH0 on 2009-10-27
Quick google search brought me back to this forum... funny how that happens.
Anyway, try this:
sudo aptitude reinstall ubuntu-desktop


You're backed up so you can reinstall now, but I'd say this is worth a try first.

---

