---
title: "Ubuntu computers can't see each other"
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by XEtedBear on 2011-10-22
On my mixed Windows/Ubuntu home LAN the Ubuntu computers can see and browse the Windows Network and can see the named Workgroup of which they are both members. However they can each only see themself in the workgroup.

Although running different versions of Ubuntu their smb.conf files are identical except for the netbios name and the shared folder names.

Where do I start looking for an explanation for the missing computer names?

---

### Post by XEtedBear on 2011-10-23
I should add that each computer can ping the other - but one takes 50% longer than the other!

---

### Post by alexanderedward on 2011-10-23
hi, i cannot personally answer the problem, but i see a thread further down the list which seems to be on point..

[http://ubuntuforums.org/showthread.php?t=1861985](http://ubuntuforums.org/showthread.php?t=1861985)

---

### Post by JRV on 2011-10-23
I will look into the problem. Check back in a few hours.

---

### Post by JRV on 2011-10-23
On my network I use SFTP for Sharing Ubuntu to Ubuntu.

Click on the desktop and then move the cursor to the upper left.

Click on the "File" menu then select "Connect to Server".

Set "Type" to SSH, then fill in the rest of the blanks.

Or, from the command line:
```
nautilus sftp://USER_NAME@HOST_NAME/home/USERNAME
```

This way Windows to Windows will work normally.
Ubuntu to Ubuntu works in what I believe to be the best way possible.

Windows can not access your Ubuntu systems.  I prefer it that way.

Unless you want the Windows machines to have access to the Ubuntu machines you do not have to mess with samba.

---

### Post by XEtedBear on 2011-10-23
Yes, I saw this thread too, yesterday. I tried everything that was being suggested there. It made no difference. 

But Linux being Linux behaves differently today than it did yesterday. Now I am back to that most depressing of messages: 'cannot mount location. Failed to retrieve share list from server'.

I can find no explanation that satisfactorily solves this problem on my system after 9 days of following every lead and every post and every Google link.

---

### Post by capscrew on 2011-10-23
> **XEtedBear said:**
> Yes, I saw this thread too, yesterday. I tried everything that was being suggested there. It made no difference. 

But Linux being Linux behaves differently today than it did yesterday. Now I am back to that most depressing of messages: 'cannot mount location. Failed to retrieve share list from server'.

I can find no explanation that satisfactorily solves this problem on my system after 9 days of following every lead and every post and every Google link.
Post the output of these two commands```
testparm -s 

smbtree
```

Please place the output between the [code] brackets (use the # tab at the top of the editor).

---

