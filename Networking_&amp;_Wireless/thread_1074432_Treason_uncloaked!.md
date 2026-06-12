---
title: "Treason uncloaked!"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by lordbah on 2009-02-19
I'm seeing the "Treason uncloaked!" message on my ReadyNAS, but only during an rsync backup from Ubuntu 8.04 to the ReadyNAS. This is **not** a network attack of any sort, it's always only the local IP of the Ubuntu. This is **not harmless** in my case - the rsync backup never completes. When one of these messages is logged there is a two minute pause before a retransmission, after which there is another two minute pause. Rinse and repeat. The connection never recovers until the backup is canceled. There is no trouble at all with network copies from a Windows XP box to the ReadyNAS. That's why I'm thinking the fix may have to be on the Ubuntu side even though that isn't where the messages are logged. (I concede that I don't know whether the message is a cause or a symptom of some other problem which causes the breakage)

I have posted in the ReadyNAS forum but not found any help yet.

I have tried tweaking various TCP parameters according to posts which my searches have turned up, but the most they appear to do is to delay the onset of the problem. It doesn't occur immediately when the rsync begins, it takes some minutes to occur.

At the point where the connection gets jammed up, netstat shows data in the send-q and recv-q on Ubuntu and data in the send-q on ReadyNAS.

ReadyNAS v4.1.4
# uname -r
2.6.17.8ReadyNAS
kernel: TCP: Treason uncloaked! Peer 192.168.218.104:873/4058 shrinks window 615001824:615007360. Repaired.
(the numbers were different before I expanded the queue length and memory settings)

Ubuntu 8.04
$ uname -r
2.6.24-23-generic

Items I've tweaked while trying to fix this:
net.ipv4.tcp_rmem
net.ipv4.tcp_wmem
net.ipv4.tcp_window_scaling
net.ipv4.tcp_rfc1337
txqueuelen

There is a new NetGEAR GS105 Gigabit Ethernet switch in between the computers. New cat6 cable everywhere. The ReadyNAS makes a gigabit connection to the switch. The Ubuntu only connects at 100mb (I was trying a new NetGEAR GA311 card but could not make a gigabit connection - it wouldn't even make a 100mb connection with the default driver - so I returned it and went back to the motherboard connection which is an Intel 82562V-2 10/100). The Windows XP box only connects at 100mb as well, with that GA311 or the Broadcom card it's had for years - I don't know why. All ports on the switch appear okay as I can move the ReadyNAS's connection to each and still get a working gigabit connection.

I am at a loss what to try next.

---

### Post by lordbah on 2009-02-22
I haven't made any progress on this. Any suggestions?

---

### Post by capscrew on 2009-02-22
See Simon Farnsworth comments to this blog post:
[http://ubuntu-tutorials.com/2008/07/04/tcp-treason-uncloaked/]("http://ubuntu-tutorials.com/2008/07/04/tcp-treason-uncloaked/")

In addition I believe that a bug was repaired in the kernel around 2.6.10 or so.  What kernel version are you running?

---

### Post by lordbah on 2009-02-22
> **capscrew said:**
> See Simon Farnsworth comments to this blog post:
[http://ubuntu-tutorials.com/2008/07/04/tcp-treason-uncloaked/]("http://ubuntu-tutorials.com/2008/07/04/tcp-treason-uncloaked/")

In addition I believe that a bug was repaired in the kernel around 2.6.10 or so.  What kernel version are you running?

Yes that was one of the pages I've read.

For versions, see original post. Both sides are beyond 2.6.14 when the kernel bug was fixed.

---

### Post by lordbah on 2009-02-23
Both sides have tcp_window_scaling=0 and have been rebooted a few times since that was set, yet I'm still seeing this message which should only be the result of bad window scaling. Bizarre. I must be missing something, but I don't know what ...

---

### Post by capscrew on 2009-02-23
I have done some googling with the terms [ReadyNAS * "treason uncloaked"] (the * means *near*).
[http://www.google.com/search?q=ReadyNAS+*+treason&btnG=Go%21]("http://www.google.com/search?hl=en&q=ReadyNAS+*+%22treason+uncloaked%22&btnG=Search")

Read the comments by the user TGL in this (the last 2 posts on the first page:
[http://www.readynas.com/forum/viewtopic.php?f=20&t=13296]("http://www.readynas.com/forum/viewtopic.php?f=20&t=13296")

And here too:
[http://kerneltrap.org/index.php?q=mailarchive/linux-netdev/2008/5/20/1881444]("http://kerneltrap.org/index.php?q=mailarchive/linux-netdev/2008/5/20/1881444")

It looks like it's a problem in the TCP binary for the kernel of the ReadyNAS O/S!

---

### Post by lordbah on 2009-02-25
I don't understand why, but the problem went away when I enabled hardy-backports and got rsync 3.0.4 (which is also the version on the NAS). How an app can cause window scaling to happen when window scaling has been disabled is a mystery to me.

---

### Post by capscrew on 2009-02-25
> **lordbah said:**
> I don't understand why, but the problem went away when I enabled hardy-backports and got rsync 3.0.4 (which is also the version on the NAS). How an app can cause window scaling to happen when window scaling has been disabled is a mystery to me.

Glad t see you got it working!  Some mysteries never get solved.

---

### Post by lordbah on 2009-03-01
It's back :(

What's changed from when it was working is that now the Ubuntu box has a working gigabit ethernet connection.

---

### Post by capscrew on 2009-03-01
> **lordbah said:**
> It's back :(

What's changed from when it was working is that now the Ubuntu box has a working gigabit ethernet connection.

Wow!  This must be a somthing to do with timing.  The card is a layer 1 to 2 device.

Edit: I just re-read your original post.  I wonder if this is pertinent:> New cat6 cable everywhere. The ReadyNAS makes a gigabit connection to the switch.   Copper gig cabling should be certified.  It can cause transmission problems that don't show up in when used with fast ethernet (100 Mbs).

How about forcing the speed to 100Mbs and see what happens.  Leave the gig card you just installed in place but run as 100Mbs.

---

