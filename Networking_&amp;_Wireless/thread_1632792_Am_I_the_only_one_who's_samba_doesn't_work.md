---
title: "Am I the only one who's samba doesn't work?"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2010-11-28
I'm really getting sick of beating my head against the wall over this.
Is there some magic button I need to push to get samba to just f***ing work?!  When I first switch to linux, I started using Gutsy and networking worked just fine!  But pretty much ever since about 8.10 I haven't been able to get file or print sharing to work properly.  I can "connect to server" and type in the ip address of another computer and access shared files but I've completely given up on sharing a printer, it just isn't going to happen.
Is there another distribution who's samba is horribly crippled?

---

### Post by guest5 on 2010-11-28
I'm on 10.10 and haven't gotten the help I used to get.  My two Ubuntu computers cannot see one another at all.  I have posted multiple requests in various forums too.  I am surprised there isn't a sticky on this issue.  I also feel like I can't be the only one with this problem.

---

### Post by endotherm on 2010-11-28
ok, samba is in a weird spot right now in the linux ecosystem, because it has always been a server technology, but now we want to integrate it into desktop systems like ubuntu.

as such, if you want to use the gui to share stuff, things work a little differently than when you are working with classic samba. 

lets see where you are at. please post back the output of these commands, and a summary of what you have already done, and what you are trying to do (naming service, etc):
```

net usershare info
testparm -s
cat /etc/samba/smb.conf

```

as for printing, I am not the guy to ask. there is a lot more than just samba involved in online printing, so there is lots of room for crossvendor confusion.

---

### Post by guest5 on 2010-11-28
this is how i set mine up, but doesn't work:

[http://uppix.net/9/2/a/1b630f5b00e50b68f4a0ebd09f289.png](http://uppix.net/9/2/a/1b630f5b00e50b68f4a0ebd09f289.png)

---

### Post by endotherm on 2010-11-28
> **guest5 said:**
> this is how i set mine up, but doesn't work:

[http://uppix.net/9/2/a/1b630f5b00e50b68f4a0ebd09f289.png](http://uppix.net/9/2/a/1b630f5b00e50b68f4a0ebd09f289.png)
indeed
it looks like it doesn;t think samba is installed. did you get anything from testparm -s?

---

### Post by guest5 on 2010-11-28
yes, and I think mine is solved, but helen went to bed so I can't check it further.  i can see her and get in as well, she can see mine, but can't get in-so I think it means to give it a few more minutes, but thats tomorrow...

The problem seems to have been that when I installed them, I gave them both the same host name.  I found a good link on how to change that:
[http://www.liberiangeek.net/2010/08/change-hostname-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/08/change-hostname-ubuntu-10-10-maverick-meerkat/)

so the things is is that ubuntu to ubuntu doesn't use samba, it uses nfs but still gets listed under a windows network for some reason...

---

### Post by guest5 on 2010-11-29
Resolved, finally.  Hope the other thread can help you, it's here:

[http://ubuntuforums.org/showthread.php?p=10175033#post10175033](http://ubuntuforums.org/showthread.php?p=10175033#post10175033)

---

