---
title: "Playing Nice with OS X"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by ryharv on 2006-05-31
Hello all,

I have a frustrating problem I could use some help with.  I have a desktop computer running Ubuntu 5.10 and a laptop running OS X 10.4.

The ubuntu computer (its name is "ubuntu") sees the OSX computer just fine.  I'm able to connect to it via the desktop or the command line.

But with OS X, I can only see the ubuntu computer in these ways:

[LIST]
[*]via the command line, using ssh 192.168.0.100
[*]via http and apache at [http://192.168.0.100](http://192.168.0.100)
[/LIST]

On OS X, every time I click the Ubuntu computer in Finder, in the MSHOME network, and click "Connect..." all I get is the beach ball.  

When I navigate to /Volumes on the OSX computer, I get this:

> rybook:/Volumes ryan$ ls
192.168.0.100   MSHOME;UBUNTU-1 MSHOME;UBUNTU-3 Macintosh HD
MSHOME;UBUNTU   MSHOME;UBUNTU-2 MSHOME;UBUNTU-4 ubuntu


So it looks like the OSX computer is opening connections to Ubuntu (several times -- looks like I've clicked "Connect" five times), but then Finder freezes and doesn't actually mount the Ubuntu computer or its shared drives.

Has anybody experienced this problem and solved it?

Thanks.

---

### Post by patrick295767 on 2006-05-31
:confused: 
Can my old thread help you maybe : 
[http://www.macusersforum.com/index.php?showtopic=11037&hl=nfs+manager](http://www.macusersforum.com/index.php?showtopic=11037&hl=nfs+manager)
 (ab. nfs manager) 
  
Greetings to MAC OS X world !! :-)

---

