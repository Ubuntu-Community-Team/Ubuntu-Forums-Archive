---
title: "Songbird 0.7 disapeared from my Computer"
date: 2008-08-29
forum: Multimedia Software
---

### Post by Prisma on 2008-08-29
After upgrading to the new version of Songbird 0.7 (from get deb) I cant find it anymore. When I fire it up, it shows that Songbird is running in system monitor but I cant find it in my desktop. 

I already deleted the .songbird folder, but it doesn't work. All it does is to start the installation wizard. When I finish with the wizard the application doesn't show on the desktop. 

I am using ubuntu 8.04 clean install 

Any suggestions? :confused:

---

### Post by Crafty Kisses on 2008-08-29
Try running it in Terminal, what happens?

---

### Post by Prisma on 2008-08-29
> **Codename said:**
> Try running it in Terminal, what happens?

It just hangs, nothing happens but it shows as running on the monitor. Actually it shows 2 songbirds processes running.

---

### Post by Crafty Kisses on 2008-08-29
This is weird, try to open Songbird again, and then post the results of this command > top

---

### Post by Prisma on 2008-08-29
mycomputer@Ubuntu-Desktop:~$ songbird
doMainwinStart
SBAppInitialize
SBVideoInitialize

this is what it shows when I run songbird from terminal

---

### Post by Prisma on 2008-08-29
well.. songbird suddently appeared...:confused: wtf???

---

### Post by Prisma on 2008-08-29
thank you Codename for your help, :) I don't know what the problem was but it took like 10 minutes to load songbird. now its working I don't know why but its working :popcorn:

---

### Post by chavanak on 2008-08-29
I suggest you file a bug report with the songbird dev team. They are quite friendly people and will help you out if you face further problem. Btw why do u need to install the software when it runs out of the tar file perfectly.??

---

### Post by Crafty Kisses on 2008-08-29
No problem, that was a really weird issue, I'd do as stated above, file a bug report.

---

### Post by alexeix on 2008-10-21
I'm also experiencing this problem.  I've installed the DEB package of Songbird 0.7 on Mythbuntu 8.04.1 (64 bit), but when I try to launch it, nothing happens.

The Songbird process is running (twice), but the status is 'sleeping'.

I tried running it from Terminal, but no difference.  Unfortunately, it didn't start after 10 minutes...

Any suggestions how I can get this working?
Thanks.

---

