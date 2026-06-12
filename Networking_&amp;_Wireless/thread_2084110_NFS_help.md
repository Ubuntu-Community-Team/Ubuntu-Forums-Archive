---
title: "NFS help"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by williammanda on 2012-11-14
I have been using nfs for years now but since this last Ubuntu upgrade to 12.10 things have changed. I have two issues currently:

1. While viewing videos on a client (using vlc) from a server, the video will pause from time to time, no real repeatable qualities. I have mythtv and this issue doesn't occur when viewing the same video.

2. During boot up on the clients for nfs, an error message comes up alerting me to continue waiting or skip mounting. If I allow it to wait I never have seen it correct itself but I usually select s for skip. Upon boot completion there isn't any access for nfs mounts. This never use to happen unless there was something wrong with the server.

Here is an example of my export and fstab files look like:

export on server
/var/lib/mythtv/recordings *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/videos    *(rw,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/music    *(rw,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/pictures   *(rw,async,no_root_squash,no_subtree_check)
/home    192.***.***.0/24(rw,async,no_root_squash,no_subtree_check)

fstab client
192.***.***.1:/home  /servercomputer nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.2:/home  /otherclientcomputer nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.3:/home  /otherclientcomputer1 nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/videos  /home/william/Videos nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/music  /home/william/Music nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/pictures  /home/william/Pictures nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/music  /var/lib/mythtv/music nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/pictures  /var/lib/mythtv/pictures nfs rsize=8192,wsize=8192,timeo=14,intr

So I decided to try and find out what was wrong. I changed my fstab to only include the first mythtv mount:

fstab
192.***.***.1:/var/lib/mythtv/videos  /home/william/Videos nfs rsize=8192,wsize=8192,timeo=14,intr

This worked. I then add the rest of the mythtv mounts:

fstab
192.***.***.1:/var/lib/mythtv/videos  /home/william/Videos nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/music  /home/william/Music nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/pictures  /home/william/Pictures nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/music  /var/lib/mythtv/music nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/pictures  /var/lib/mythtv/pictures nfs rsize=8192,wsize=8192,timeo=14,intr

This worked as well. I then tried to add the other home directory mounts and got the continue to wait or skip message.

192.***.***.1:/home  /servercomputer nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/videos  /home/william/Videos nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/music  /home/william/Music nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/pictures  /home/william/Pictures nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/music  /var/lib/mythtv/music nfs rsize=8192,wsize=8192,timeo=14,intr
192.***.***.1:/var/lib/mythtv/pictures  /var/lib/mythtv/pictures nfs rsize=8192,wsize=8192,timeo=14,intr

So has something changed with nfs? If not please advise.
Thanks

---

### Post by williammanda on 2012-11-15
anyone?

---

### Post by cjhabs on 2012-11-15
I saw something similar when using Cinammon - doesn't happen under Unity. Are you using Cinammon? I am now running Unity again.

---

### Post by williammanda on 2012-11-15
> **cjhabs said:**
> I saw something similar when using Cinammon - doesn't happen under Unity. Are you using Cinammon? I am now running Unity again.

I'm using cairo dock.

---

### Post by williammanda on 2012-11-17
anyone?

---

### Post by williammanda on 2012-11-18
Is this still the best way to setup nfs?

export
/files 192.168.1.0/24(rw,no_root_squash,async)

fstab
server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr

This info was gathered from this tutorial:

[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs)

---

### Post by williammanda on 2012-11-18
I decided to change the fstab file after doing some research:

from this 
server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr

to this
server.mydomain.com:/files /files nfs4 rw,hard,intr 0 0

So far I haven't had any pausing or drop outs.

---

