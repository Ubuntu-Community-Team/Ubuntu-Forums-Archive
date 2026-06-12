---
title: "Problem accessing XP share from Lucid"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by Hevydani on 2010-08-23
I've been having this problem for days and it's really starting to p**s me right off. I'm nearly ready to go back to XP for the simple reason, it's easier to host/access shares.

I can smb://IP into my XP box and see the shares, but upon trying to open the folders, am presented with a login box. I've read around the forums but nothing I do seems to work. Any help would be much appreciated.

---

### Post by e79 on 2010-08-23
As far as I can understand you have an authentication problem. When trying to access a Windows share from my own Lucid installation, all as I have to do is input a user/password valid for the XP machine and make sure both machine are in the same workgroup/domain.
 
So here's what I do (there might be other ways though) :
 
1. Got to : Places --> Connect to Server
2. Select 'Windows Share' and enter the IP address of your XP box, the name of your Share folder (in Share input box)as well as the user you want to connect with, click on 'Add Bookmark' and click connect.
3. Verify that your XP box is under 'Workgroup' and enter the password for the user you decided to connect with, and Voila !
 
This worked for me everytime I want to connect to a Windows share under a workgroup (not speaking of an internal domain here).
 
Hope this help :p
 
e79

---

### Post by Morbius1 on 2010-08-23
> I can smb://IP into my XP box and see the shares, but upon trying to open the folders, am presented with a login box.Did you create shares on the XP box? 

Or do all the shares you see from Linux have a "$" at the end of them, like "C$" for example. Those are all "administrative shares" and are really not meant to be accessed. But it is Windows so you can access them but it's looking for the administrators password.

---

### Post by pricetech on 2010-08-23
Use your windows credentials.  If you don't have a password in windows, it won't work.

---

