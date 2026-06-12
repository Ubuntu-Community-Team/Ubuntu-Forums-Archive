---
title: "Samba shares on Ubuntu"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by karmic-koala on 2010-08-06
I have an external 2 TB drive which is attached to my Ubuntu 9.10 x64_86 Desktop. The drive contains a folder that's shared using Samba.

Every time I make changes to folder names/rename shares the new share is visible on other Windows PCs but the old share also continues to show up although it doesn't do anything.

I have tried restarting Samba and Networking but the old entries continue to show up. 

Can someone please shed some light why does this happen and is there a way around the issue?

---

### Post by sikander3786 on 2010-08-06
Hi.

Did you take a look at your smb.conf file? How many shares are defined in the file? How did you share the files, from smb.conf or nautilus-share?

Regards.

---

### Post by karmic-koala on 2010-08-06
Because I used nautilus to share folders (right click > properties > share) my smb.conf is intact with only default share for print$

Should have shared using samba conf file.

---

### Post by Morbius1 on 2010-08-06
Post the output of the following commands to see how your shares are set up :

```
net usershare info
``````
sudo net usershare info
```

[COLOR=Blue]EDIT: In my experience although you can use both methods to share folders it's bet to use only one method. [/COLOR]

---

### Post by karmic-koala on 2010-08-06
Here's the output of net usershare info
[http://ubuntu.pastebin.com/rSbLtpx4](http://ubuntu.pastebin.com/rSbLtpx4)

same command as root produced no results

I now know how to share folders using the terminal using net usershare, thanks for that :D

I suspect way forward is to delete all shares and start from a scratch only this time round I'll create shares using net usershare add

---

### Post by Morbius1 on 2010-08-06
Using the command line to create Nautilus-shares kind of defeats the purpose of using Nautilus-share, but that's up to you.

I suspect the problem is this error message from net usershare info:
> info_fn: file /var/lib/samba/usershares/basic_linux_server is not a well formed usershare file.
  info_fn: Error was Path is not a directory.
If you do a > cat /var/lib/samba/usershares/basic_linux_serverYou'll probably find out it's path is pointing to a directory that no longer exists. If that's true then you can delete it using:
```
net usershare delete basic_linux_server
```

Or you can go into nautilus as root and delete /var/lib/samba/usershares/basic_linux_server

---

### Post by karmic-koala on 2010-08-06
Thanks for that :)

Also, if I am sharing subfolders (folders within my main share) do I need to manually specify those or does add usershare permissions get filtered through to subfolders?

---

### Post by Morbius1 on 2010-08-06
You don't want to create shares within shares using either samba method.

For example, let's say you create a parent share as allowing guests and then you create a child share requiring credentials. If you access the child share directly it will ask for credentials. If you access the parent share it will not ask for credentials AND it will give the guest access to the child without asking for credentials.

---

