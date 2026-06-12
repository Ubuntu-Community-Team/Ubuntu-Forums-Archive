---
title: "Windows XP"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by ArSarge7 on 2009-09-03
Will Ubuntu server see WinXP machines?

---

### Post by fatbotgw on 2009-09-03
What do you mean by "see" them?

---

### Post by Shibblet on 2009-09-03
Yes, download Samba.

---

### Post by ArSarge7 on 2009-09-04
I have been a windows user for years. I want to use ubuntu server in a network for my church. I am interested in setting up a file server and print server for starters. We have a Win 2003 DC, can I add ubuntu servers to the domain so the church doesn't have to spend money on buying Win 2003 svr licenses?

---

### Post by Whiffle on 2009-09-04
Sure.  I have one (well, its running debian, but its functionally the same), that serves up files and printers to the network in my house.  

All you need is samba, and cups (for printers).

---

### Post by linuxwl on 2009-09-05
I install windows xp in virtualbox,then I set a share Directory&#65292;the xp could read and write the Directory&#12290;

---

### Post by brainspank on 2009-09-05
You should be able to get set up fast with basic functionality.  Once you get it working, I'd suggest continuing to read up on it to a) be familiar enough to troubleshoot it and b) secure/tune it to the required level.  It helps if you're familiar with the Windows side of it.

starter links
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Samba's howto (not Ubuntu specific):
[http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2555984](http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2555984)

good luck.

bs

---

### Post by ArSarge7 on 2009-09-07
Thank you all for your replies.
I loaded the server version tonight. When it finished loading it started at the cmd line. How do I bring up the gui after I login? Is there one even to bring up? Better yet! What is URL can I go to that well walk me through the process?
 
Thanks for helping a newbie!

---

### Post by falconindy on 2009-09-07
The server edition of Ubuntu has no graphical interface. If you want to install one (let's say Gnome), you can do this:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by interval1066 on 2009-09-08
> **linuxwl said:**
> I install windows xp in virtualbox,then I set a share Directory&#65292;the xp could read and write the Directory&#12290;

Samba's a more elegant solution.

---

### Post by linuxwl on 2009-10-10
> **interval1066 said:**
> Samba's a more elegant solution.
 
Maybe ,but I am so lazy,:)

---

