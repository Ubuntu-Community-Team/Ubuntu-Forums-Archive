---
title: "Problem setting up MythBuntu Live CD Environment"
date: 2009-02-05
forum: Mythbuntu
---

### Post by Mythgruntled on 2009-02-05
[SIZE=1]I've been trying to check out the Live CD Environment but am having a very basic problem right at the start, setting up the Live CD Frontend.[/SIZE]
 
[SIZE=1]At the 'Master Backend Information' tab of the 'Live Session Configuration' window, I don't know what to type into the 'MySQL MythTV Password' field, or into the 'MySQL Server' field.[/SIZE]
[SIZE=1]The PDF Manual doesn't say, because in the pictures, those fields are left blank, but when I press the 'Test Connection' button it always fails, no matter what I write into those fields.[/SIZE]
 
[SIZE=1]Can someone please let me know what to type into those two fields? Thanks.[/SIZE]

---

### Post by dontpntpool on 2009-02-05
I assume your using the newest build like me...mine got set with what seemed to be a random password... also other things were set not how I set them up.. I think this is why they call it beta because its not noob proof yet

---

### Post by Mythgruntled on 2009-02-05
I'm using 8.10 which is the latest build, I don't think it's a beta.
This is what the window looks like:
[IMG]http://www.ce4k.com/images/mythbuntu1.jpg[/IMG]
Just need to know what to type into those two blank fields...

---

### Post by superm1 on 2009-02-05
If it's failing, then that means that your backend likely isn't listening properly.  You can get the information that should go into those boxes from /etc/mythtv/mysql.txt on your backend though.

---

### Post by Mythgruntled on 2009-02-05
Thanks - [SIZE=1]this is what I get:[/SIZE]
 
```
DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=C1RFOKlE
```[SIZE=1]I’ve tried every combination I can think of, including ‘C1RFOKlE’ and ‘mythtv’ for the Password, and ‘localhost’, ‘ubuntu’, ‘127.0.0.1’ and ‘192.168.0.5’ (the box’s IP address) for the Server. None of them work when I press the ‘Test Connection’ button.[/SIZE]
 
[SIZE=1]Ignoring the fact that ‘Test Connection’ doesn’t work, and pressing the ‘Start Session’ button anyway... after selecting the default US English, then just pressing Enter twice to accept the default settings in each field, I either get ‘No UPnP backends found’ or ‘Cannot login to database?’[/SIZE]
 
[SIZE=1]I did try installing Mythbuntu to hard drive instead of using the Live CD, and got to the point where I could actually run MythTV and MythTV Setup, but it would always complain that it couldn’t connect to the master backend server, and I suspect the same issue is the cause here.[/SIZE]
 
[SIZE=1]The same hardware is working fine with KnoppMyth - tuner is an AVerMedia AVerTV DVB-T 771.[/SIZE]

---

### Post by tgm4883 on 2009-02-05
> **Mythgruntled said:**
> Thanks - [SIZE=1]this is what I get:[/SIZE]
 
```
DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=C1RFOKlE
```[SIZE=1]I’ve tried every combination I can think of, including ‘C1RFOKlE’ and ‘mythtv’ for the Password, and ‘localhost’, ‘ubuntu’, ‘127.0.0.1’ and ‘192.168.0.5’ (the box’s IP address) for the Server. None of them work when I press the ‘Test Connection’ button.[/SIZE]
 
[SIZE=1]Ignoring the fact that ‘Test Connection’ doesn’t work, and pressing the ‘Start Session’ button anyway... after selecting the default US English, then just pressing Enter twice to accept the default settings in each field, I either get ‘No UPnP backends found’ or ‘Cannot login to database?’[/SIZE]
 
[SIZE=1]I did try installing Mythbuntu to hard drive instead of using the Live CD, and got to the point where I could actually run MythTV and MythTV Setup, but it would always complain that it couldn’t connect to the master backend server, and I suspect the same issue is the cause here.[/SIZE]
 
[SIZE=1]The same hardware is working fine with KnoppMyth - tuner is an AVerMedia AVerTV DVB-T 771.[/SIZE]

This might sound odd, but you do actually have a master backend somewhere right?

---

### Post by Mythgruntled on 2009-02-06
> **tgm4883 said:**
> This might sound odd, but you do actually have a master backend somewhere right?
I'm assuming that the default Live CD Environment just sets up the box as both a backend and frontend?

---

### Post by tgm4883 on 2009-02-06
> **Mythgruntled said:**
> I'm assuming that the default Live CD Environment just sets up the box as both a backend and frontend?

You do not get a backend from running just the live CD, the backend has to be installed to the hard disk.

---

### Post by Mythgruntled on 2009-02-06
Ahh... now it's all becoming clear to me - thanks for that. I'll have another crack at the hard drive install.

---

### Post by ryansebiz on 2009-02-22
> **tgm4883 said:**
> You do not get a backend from running just the live CD, the backend has to be installed to the hard disk.

So will the backend not work if I'm using wubi? I don't want to repartition and wipe out my Windows install to test Mythbuntu.

---

### Post by Mythgruntled on 2009-02-23
> **ryansebiz said:**
> So will the backend not work if I'm using wubi? I don't want to repartition and wipe out my Windows install to test Mythbuntu.
I'm willing to stand corrected if anyone knows better, but I think you're right, it wouldn't work - installing Mythbuntu over Wubi would be like installing one distro over another. You could probably install MythTV itself in Wubi, though it would no doubt be tricky. But if you need a Mythbuntu backend, I don't think it could be installed on a Windows hard drive.

---

### Post by tgm4883 on 2009-03-11
> **ryansebiz said:**
> So will the backend not work if I'm using wubi? I don't want to repartition and wipe out my Windows install to test Mythbuntu.

The backend will not work from wubi by design.  It would be a really bad idea trying to keep recordings in the loop mounted ntfs partition.  This may be fixed in the future, but the pain it would cause probably justifies the cost of another hard drive.

---

