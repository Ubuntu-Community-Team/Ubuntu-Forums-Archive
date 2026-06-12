---
title: "sharing files with Windows 7"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by kidguayas on 2009-01-19
I would like to thank you in advance for reviewing my post and try to help.
 I have installed samba and works like a charm in windows xp. However a new windows beta version is in the market and the sharing folder is a bit confusing. If you know how to share folders between these two systems. I'll appreciate it.

Thanks,

kidguayas

---

### Post by theozzlives on 2009-01-19
right-click on the folder and share with home group (either read or read and write)

---

### Post by kidguayas on 2009-01-19
I tried to do the righ-click and it ask me about homegroup if I create one or join a homegroup windows 7 machine disapears from the nautilus. When I don't have a homegroup I can ping the machine, but I cannot see the files.

---

### Post by superprash2003 on 2009-01-19
you could try accessing windows shared folders from ubuntu like this [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by kidguayas on 2009-01-20
I have tried to connect to my windows 7 machine as instructed crt+L and typing the smb:\\IPADDRESS but still cannot see the folders I shared neither pops up a message for password and user name.

---

### Post by superprash2003 on 2009-01-22
its smb:// not smb:\\

---

### Post by pajarraco on 2009-07-21
I having problems with this. I have share my folder on my win7 machine and I can access from other windows machines. but when i try to access from my ubuntu box, I get a pop up window asking me for password and no matter what i put there is not connection

---

### Post by elitenoobboy on 2009-07-28
> **pajarraco said:**
> I having problems with this. I have share my folder on my win7 machine and I can access from other windows machines. but when i try to access from my ubuntu box, I get a pop up window asking me for password and no matter what i put there is not connection

Try rebooting win7 to see if that fixes it. Its samba server isn't particularly stable for me, and sometimes it needs to be restarted to work properly.

---

### Post by pajarraco on 2009-07-28
Hi, I did that, but still the same.

---

### Post by MaLaCoiD on 2009-08-04
> **pajarraco said:**
> I having problems with this. I have share my folder on my win7 machine and I can access from other windows machines. but when i try to access from my ubuntu box, I get a pop up window asking me for password and no matter what i put there is not connection
I'm having the same problem. XP can access the share, but not Jaunty. In Win 7, I changed the setting that requires a local account for access to make the XP box work.

---

### Post by poet_will on 2009-08-12
This is the problem that I am having too.  Windows 7 desktop with shared folders.  When I try to access them with Ubuntu 9.04 I get a windows with a password.  Am I doing something wrong?

Thanks

---

### Post by servicetech on 2009-09-16
Mine just says "unable to mount windows share".

---

### Post by Xpire on 2009-11-11
> **servicetech said:**
> Mine just says "unable to mount windows share".
I get this problem too :( Anyone know what the problem is?

---

### Post by Hiperi0n on 2009-11-12
I think Windows 7 sharing system is quite different, it is possible samba developers have not implemented it yet. Anyway, when creating a home group Windows gives you a password. You may try with that (I have had no luck at all).

---

### Post by Xpire on 2009-11-14
> **servicetech said:**
> Mine just says "unable to mount windows share".
Just updated samba and it works now.

---

### Post by dmizer on 2009-11-14
> **Xpire said:**
> I get this problem too :( Anyone know what the problem is?

See the 6th link in my sig.

---

### Post by MaLaCoiD on 2010-08-08
> **dmizer said:**
> See the 6th link in my sig.

Yes:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

I walked through all the steps in the first post, and it still didn't work. Then I read it again and saw that I overlooked one. As soon as I uninstalled Windows Live Sign In Assistant in Windows 7, it started working. The other change I had made before that was making sure I was on Home instead of Unknown network. I had to change my Group Policy to allow that to happen- seems I checked Always Mark Network as Public or whatever.

---

