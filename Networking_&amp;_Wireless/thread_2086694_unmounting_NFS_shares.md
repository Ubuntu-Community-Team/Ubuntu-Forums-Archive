---
title: "unmounting NFS shares"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by Simoo on 2012-11-21
Hi,

I mount NFS shares like this:

```
:~$ sudo mount -t nfs4 myserver:nethomes/me /nfs/myserver-myhome
```

Why when I umount do I get this error?

```
:~$ sudo umount /nfs/myserver-myhome
/nfs/myserver-myhome was not found in /proc/mounts
/nfs/myserver-myhome was not found in /proc/mounts
```

Thanks

---

### Post by papibe on 2012-11-21
Hi Simoo.

Could you post the results of these commands?
```
mount -l | grep nfs

grep nfs /proc/mounts

grep nfs /proc/mounts | od -a
```
Regards.

---

### Post by Simoo on 2012-11-21
Thanks:

```
simon@icarus:~$ mount -l | grep nfs
juliet:archive on /nfs/juliet-archive type nfs4 (rw,addr=10.1.0.254,clientaddr=10.1.0.111)
juliet:audio on /nfs/juliet-audio type nfs4 (rw,addr=10.1.0.254,clientaddr=10.1.0.111)
juliet:images on /nfs/juliet-images type nfs4 (rw,addr=10.1.0.254,clientaddr=10.1.0.111)
juliet:photos on /nfs/juliet-photos type nfs4 (rw,addr=10.1.0.254,clientaddr=10.1.0.111)
juliet:video on /nfs/juliet-video type nfs4 (rw,addr=10.1.0.254,clientaddr=10.1.0.111)
juliet:nethomes/simon on /nfs/juliet-nethome type nfs4 (rw,addr=10.1.0.254,clientaddr=10.1.0.111)
```

```
simon@icarus:~$ grep nfs /proc/mounts
juliet:/archive/ /nfs/juliet-archive nfs4 rw,relatime,vers=4,rsize=524288,wsize=524288,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=10.1.0.111,minorversion=0,local_lock=none,addr=10.1.0.254 0 0
juliet:/audio/ /nfs/juliet-audio nfs4 rw,relatime,vers=4,rsize=524288,wsize=524288,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=10.1.0.111,minorversion=0,local_lock=none,addr=10.1.0.254 0 0
juliet:/images/ /nfs/juliet-images nfs4 rw,relatime,vers=4,rsize=524288,wsize=524288,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=10.1.0.111,minorversion=0,local_lock=none,addr=10.1.0.254 0 0
juliet:/photos/ /nfs/juliet-photos nfs4 rw,relatime,vers=4,rsize=524288,wsize=524288,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=10.1.0.111,minorversion=0,local_lock=none,addr=10.1.0.254 0 0
juliet:/video/ /nfs/juliet-video nfs4 rw,relatime,vers=4,rsize=524288,wsize=524288,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=10.1.0.111,minorversion=0,local_lock=none,addr=10.1.0.254 0 0
juliet:/nethomes/simon /nfs/juliet-nethome nfs4 rw,relatime,vers=4,rsize=524288,wsize=524288,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=10.1.0.111,minorversion=0,local_lock=none,addr=10.1.0.254 0 0
```

```
simon@icarus:~$ grep nfs /proc/mounts | od -a
0000000   j   u   l   i   e   t   :   /   a   r   c   h   i   v   e   /
0000020  sp   /   n   f   s   /   j   u   l   i   e   t   -   a   r   c
0000040   h   i   v   e  sp   n   f   s   4  sp   r   w   ,   r   e   l
0000060   a   t   i   m   e   ,   v   e   r   s   =   4   ,   r   s   i
0000100   z   e   =   5   2   4   2   8   8   ,   w   s   i   z   e   =
0000120   5   2   4   2   8   8   ,   n   a   m   l   e   n   =   2   5
0000140   5   ,   h   a   r   d   ,   p   r   o   t   o   =   t   c   p
0000160   ,   p   o   r   t   =   0   ,   t   i   m   e   o   =   6   0
0000200   0   ,   r   e   t   r   a   n   s   =   2   ,   s   e   c   =
0000220   s   y   s   ,   c   l   i   e   n   t   a   d   d   r   =   1
0000240   0   .   1   .   0   .   1   1   1   ,   m   i   n   o   r   v
0000260   e   r   s   i   o   n   =   0   ,   l   o   c   a   l   _   l
0000300   o   c   k   =   n   o   n   e   ,   a   d   d   r   =   1   0
0000320   .   1   .   0   .   2   5   4  sp   0  sp   0  nl   j   u   l
0000340   i   e   t   :   /   a   u   d   i   o   /  sp   /   n   f   s
0000360   /   j   u   l   i   e   t   -   a   u   d   i   o  sp   n   f
0000400   s   4  sp   r   w   ,   r   e   l   a   t   i   m   e   ,   v
0000420   e   r   s   =   4   ,   r   s   i   z   e   =   5   2   4   2
0000440   8   8   ,   w   s   i   z   e   =   5   2   4   2   8   8   ,
0000460   n   a   m   l   e   n   =   2   5   5   ,   h   a   r   d   ,
0000500   p   r   o   t   o   =   t   c   p   ,   p   o   r   t   =   0
0000520   ,   t   i   m   e   o   =   6   0   0   ,   r   e   t   r   a
0000540   n   s   =   2   ,   s   e   c   =   s   y   s   ,   c   l   i
0000560   e   n   t   a   d   d   r   =   1   0   .   1   .   0   .   1
0000600   1   1   ,   m   i   n   o   r   v   e   r   s   i   o   n   =
0000620   0   ,   l   o   c   a   l   _   l   o   c   k   =   n   o   n
0000640   e   ,   a   d   d   r   =   1   0   .   1   .   0   .   2   5
0000660   4  sp   0  sp   0  nl   j   u   l   i   e   t   :   /   i   m
0000700   a   g   e   s   /  sp   /   n   f   s   /   j   u   l   i   e
0000720   t   -   i   m   a   g   e   s  sp   n   f   s   4  sp   r   w
0000740   ,   r   e   l   a   t   i   m   e   ,   v   e   r   s   =   4
0000760   ,   r   s   i   z   e   =   5   2   4   2   8   8   ,   w   s
0001000   i   z   e   =   5   2   4   2   8   8   ,   n   a   m   l   e
0001020   n   =   2   5   5   ,   h   a   r   d   ,   p   r   o   t   o
0001040   =   t   c   p   ,   p   o   r   t   =   0   ,   t   i   m   e
0001060   o   =   6   0   0   ,   r   e   t   r   a   n   s   =   2   ,
0001100   s   e   c   =   s   y   s   ,   c   l   i   e   n   t   a   d
0001120   d   r   =   1   0   .   1   .   0   .   1   1   1   ,   m   i
0001140   n   o   r   v   e   r   s   i   o   n   =   0   ,   l   o   c
0001160   a   l   _   l   o   c   k   =   n   o   n   e   ,   a   d   d
0001200   r   =   1   0   .   1   .   0   .   2   5   4  sp   0  sp   0
0001220  nl   j   u   l   i   e   t   :   /   p   h   o   t   o   s   /
0001240  sp   /   n   f   s   /   j   u   l   i   e   t   -   p   h   o
0001260   t   o   s  sp   n   f   s   4  sp   r   w   ,   r   e   l   a
0001300   t   i   m   e   ,   v   e   r   s   =   4   ,   r   s   i   z
0001320   e   =   5   2   4   2   8   8   ,   w   s   i   z   e   =   5
0001340   2   4   2   8   8   ,   n   a   m   l   e   n   =   2   5   5
0001360   ,   h   a   r   d   ,   p   r   o   t   o   =   t   c   p   ,
0001400   p   o   r   t   =   0   ,   t   i   m   e   o   =   6   0   0
0001420   ,   r   e   t   r   a   n   s   =   2   ,   s   e   c   =   s
0001440   y   s   ,   c   l   i   e   n   t   a   d   d   r   =   1   0
0001460   .   1   .   0   .   1   1   1   ,   m   i   n   o   r   v   e
0001500   r   s   i   o   n   =   0   ,   l   o   c   a   l   _   l   o
0001520   c   k   =   n   o   n   e   ,   a   d   d   r   =   1   0   .
0001540   1   .   0   .   2   5   4  sp   0  sp   0  nl   j   u   l   i
0001560   e   t   :   /   v   i   d   e   o   /  sp   /   n   f   s   /
0001600   j   u   l   i   e   t   -   v   i   d   e   o  sp   n   f   s
0001620   4  sp   r   w   ,   r   e   l   a   t   i   m   e   ,   v   e
0001640   r   s   =   4   ,   r   s   i   z   e   =   5   2   4   2   8
0001660   8   ,   w   s   i   z   e   =   5   2   4   2   8   8   ,   n
0001700   a   m   l   e   n   =   2   5   5   ,   h   a   r   d   ,   p
0001720   r   o   t   o   =   t   c   p   ,   p   o   r   t   =   0   ,
0001740   t   i   m   e   o   =   6   0   0   ,   r   e   t   r   a   n
0001760   s   =   2   ,   s   e   c   =   s   y   s   ,   c   l   i   e
0002000   n   t   a   d   d   r   =   1   0   .   1   .   0   .   1   1
0002020   1   ,   m   i   n   o   r   v   e   r   s   i   o   n   =   0
0002040   ,   l   o   c   a   l   _   l   o   c   k   =   n   o   n   e
0002060   ,   a   d   d   r   =   1   0   .   1   .   0   .   2   5   4
0002100  sp   0  sp   0  nl   j   u   l   i   e   t   :   /   n   e   t
0002120   h   o   m   e   s   /   s   i   m   o   n  sp   /   n   f   s
0002140   /   j   u   l   i   e   t   -   n   e   t   h   o   m   e  sp
0002160   n   f   s   4  sp   r   w   ,   r   e   l   a   t   i   m   e
0002200   ,   v   e   r   s   =   4   ,   r   s   i   z   e   =   5   2
0002220   4   2   8   8   ,   w   s   i   z   e   =   5   2   4   2   8
0002240   8   ,   n   a   m   l   e   n   =   2   5   5   ,   h   a   r
0002260   d   ,   p   r   o   t   o   =   t   c   p   ,   p   o   r   t
0002300   =   0   ,   t   i   m   e   o   =   6   0   0   ,   r   e   t
0002320   r   a   n   s   =   2   ,   s   e   c   =   s   y   s   ,   c
0002340   l   i   e   n   t   a   d   d   r   =   1   0   .   1   .   0
0002360   .   1   1   1   ,   m   i   n   o   r   v   e   r   s   i   o
0002400   n   =   0   ,   l   o   c   a   l   _   l   o   c   k   =   n
0002420   o   n   e   ,   a   d   d   r   =   1   0   .   1   .   0   .
0002440   2   5   4  sp   0  sp   0  nl
0002450
```

---

### Post by papibe on 2012-11-21
Thanks.

It seems that nothing is mount on /nfs/myserver-myhome (from mount -l).

Whatever the error was, it seems 'umount' actually un mount it.

Can you confirm that?

Regards.

---

### Post by Simoo on 2012-11-21
Sorry, I've caused confusion by not using the real names for things in my initial post.

```
simon@icarus:~$ sudo umount -t nfs4 /nfs/juliet-archive/
[sudo] password for simon: 
/nfs/juliet-archive was not found in /proc/mounts
/nfs/juliet-archive was not found in /proc/mounts
```

^ That (or any of the other NFS mounts is what I should have initially posted)

---

