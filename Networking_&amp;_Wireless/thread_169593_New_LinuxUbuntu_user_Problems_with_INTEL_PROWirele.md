---
title: "New Linux/Ubuntu user: Problems with INTEL PRO/Wireless 3945ABG"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by bodean on 2006-05-02
Just installed linux for the first time. Have a dual boot with windows xp on my ASUS V6J laptop.  I do not have the network working in ubuntu.  How can I get my wireless network working, the card is listed in the topic?

Only way I can dl is in windows xp, so if i have to dl a driver, i am not sure how to move it from a ntfs  partition in winxp to my linux partition to install it.

---

### Post by bugme on 2006-05-02
Well, I could tell you how to move stuff from one partition to another...
First read this guide: [https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin](https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin)
1.)Then, login to root, either by graphical login or by command line.
2.)Next look on your desktop and double-click on HD1 or whatever the name of your harddrive is. 
3.)Look through the contents and find the file you want then drag it to your ubuntu desktop.
4.)Go to places > computer (I forgot what it was called but it had computer in the name) 
5.)then when that window comes up double-click **file system** 
6.)then double-click **Home** 
7.)then double click **<your username>**
8.)then double click **Desktop** and you can do whatever you want with it from there.

---

### Post by bugme on 2006-05-02
Well, I could tell you how to move stuff from one partition to another...
First read this guide: [https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin](https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin)
1.)Then, login to root, either by graphical login or by command line.
2.)Next look on your desktop and double-click on HD1 or whatever the name of your harddrive is. 
3.)Look through the contents and find the file you want then drag it to your ubuntu desktop.
4.)Go to places > computer (I forgot what it was called but it had computer in the name) 
5.)then when that window comes up double-click **file system** 
6.)then double-click **Home** 
7.)then double click **<your username>**
8.)then double click **Desktop** 
9.)then drag the file that you recently put on your desktop in the desktop folder.
10.)log out of root and and back into your normal username so as to avoid destroying your computer, and take note of the file waiting for you on your desktop.
And you can do whatever you want with it from there.

---

### Post by bodean on 2006-05-03
Thats a start to this issue................

---

### Post by bodean on 2006-05-03
[QUOTE=bodean]Thats a start to this issue................[/QUOTE]

Anyone?

---

### Post by bugme on 2006-05-03
What kind of wireless card do you have?

---

### Post by bodean on 2006-05-03
[QUOTE=bugme]What kind of wireless card do you have?[/QUOTE]
Intel 3945abg, as stated in the topic

---

### Post by mips on 2006-05-04
There is a thread/script in the Dapper forum that might help you.

---

### Post by bodean on 2006-05-05
[QUOTE=mips]There is a thread/script in the Dapper forum that might help you.[/QUOTE]
link?

---

### Post by mips on 2006-05-06
[QUOTE=bodean]link?[/QUOTE]

Thats really cheeky, you expect me to go and search for it while you sit on your arse :rolleyes: 

While all you have to do is search in the Dapper forum for "3945".

There you go, [http://www.ubuntuforums.org/showthread.php?t=140085](http://www.ubuntuforums.org/showthread.php?t=140085)

---

### Post by bodean on 2006-05-06
[QUOTE=mips]Thats really cheeky, you expect me to go and search for it while you sit on your arse :rolleyes: 

While all you have to do is search in the Dapper forum for "3945".

There you go, [http://www.ubuntuforums.org/showthread.php?t=140085](http://www.ubuntuforums.org/showthread.php?t=140085)[/QUOTE]
Thanks found it

---

