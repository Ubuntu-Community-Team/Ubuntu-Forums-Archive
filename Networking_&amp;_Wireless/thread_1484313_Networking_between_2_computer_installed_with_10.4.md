---
title: "Networking between 2 computer installed with 10.4"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Houchy on 2010-05-15
Hello,

I need some help to share files ...

I have 2 computers at home. A desktop with ubuntu 9.04 that I just updgraded to ubuntu 10.4 and a laptop on which I freshly install 10.4 also.

On both computers, I shared the /home/public folder as well as another folder located on another partition. 


**_From the desktop_**
I can see the laptop, but when I try to access the shared folder, I got this message asking for a password, and whatever password I type in, it is never accepted:
[ATTACH]157047[/ATTACH]

**_From the laptop_**
I just cannot see the desktop.
However, the remote desktop connection works perfectly.


I just don't understand why this simple networking doesn't work right away since I have the same OS installed.


Does anybody have an idea how to fix this?

Thank you in advance for your help.

---

### Post by 2hot6ft2 on 2010-05-15
This may help some, especially the second post.
[http://forumubuntusoftware.info/viewtopic.php?f=68&t=4789](http://forumubuntusoftware.info/viewtopic.php?f=68&t=4789)

---

### Post by Iowan on 2010-05-16
You didn't mention whether connection is wired or wireless = guess it really doesn't matter, since the basic networking part seems to be working. Not to add misdirection, but [NFS]("http://ubuntuforums.org/showthread.php?t=249889") is another option between Ubuntu machines...

---

### Post by Morbius1 on 2010-05-16
(1) Desktop to laptop share problem:

From the laptop post the output of the following commands:
```
net usershare info
sudo net usershare info
testparm -s
smbtree

```(2) Laptop to desktop share problem:
 
On the desktop:

Preliminary checklist:
(a) Make sure samba and it's little brother are running:

```
sudo service smbd restart
sudo service nmbd restart

```(b) If you have configured the default firewall in any way disable it.

(c) Check the netbios name ( has to be <= 15 characters )

Just open a terminal. Samba defaults to the machine name which appears after the @ sign. If it's more than 15 character you'll have to fix it - a simple fix using samba itself.

(d) Permissions on entire path have to be set to at least read and execute.

If your shared folder is ... /home/username/Public the parent directory:
/home/username must have permissions of at least:

```
ls -dl /home/username
```> [COLOR=Blue]drwxr-xr-x[/COLOR] 87 username username

---

