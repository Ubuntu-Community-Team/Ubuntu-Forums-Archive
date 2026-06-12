---
title: "NFS problems?"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by Gondee on 2010-05-30
I installed the NFS functionality into Ubuntu 10.04, hoping to have a home file system. However, mounting it seems to be a challenge. 

When i mount on the server its self, it works fine. But on other computers. Such as my windows 7 machine, the connection times out. 

It seems to make the inital connect, then none after that.

(The windows 7 machine does have the NFS files installed) 

You guys have any idea whats going on here? =)

---

### Post by ender8282 on 2010-05-30
Timeouts are often caused by not being able to find the server, or not actually having the service running.  With that in mind...

Have you gotten the shares to work on a different Linux machine? 
Are you sure the server's network interfaces are properly configured?

Why are you trying to use NFS instead of samba? (I use NFS but I have no Windows machines to worry about.)

---

### Post by Gondee on 2010-06-02
So i did try my other linux machines, and they connected without hassle to the NFS. I did some further reasearch and I think theres a bug with the windows 7 NFS support. 

I had planed on using it because others on the forum had said. "Samba is sooooooooo"

---

### Post by ender8282 on 2010-06-02
I would say that NFS is far better then Samba when deployed in an entirely Linux environment.  As soon as you start adding Windows machines Samba looks a lot more appealing.  (You don't have to modify the windows machines.)  Keep in mind nothing says that you can't use both.  If you have NFS working between Linux machines you might try adding Samba so that you can also get access from the Windows box.  Nothing prevents you from using both NFS and Samba at the same time.

---

