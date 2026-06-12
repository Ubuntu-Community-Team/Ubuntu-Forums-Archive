---
title: "Wine ASIO freezes applications"
date: 2010-10-11
forum: Multimedia Software
---

### Post by proxess on 2010-10-11
I know this seem like a double post, but I decided to put this in the two places I found most appropriate.

Here's a link to the original post explaining the problem:
[http://ubuntuforums.org/showthread.php?p=9955431#post9955431]("http://ubuntuforums.org/showthread.php?p=9955431#post9955431")

Here's what it says:
I just compiled the latest Wine ASIO (0.8.0) on my 64 bit machine and all went pretty well if I have to add. regsvr32 wineasio.dll went fine too. The problem is when I start up the applications that use it. When I choose the Wine ASIO driver, the applications completely freeze up. No output error anywhere tho, which makes things much more difficult. I run jackd with qjackctl and it starts up fine. Something weird tho is that when I choose the WineASIO driver, jackd trys to start again, but I doubt that's the problem.

Wine version is 1.3 and ASIO SDK is 2.2.

---

### Post by NodeEndo on 2012-12-20
:KS
I realize that I'm replying to an outdated post, however their are people still out who may need a solution to this very same problem with WineASIO as I also faced at one point.
 
Every time I selected "WineASIO" as my device driver in the DAW's audio preferences, it would render my entire DAW inoperable(no interaction). The solution for me was to simply disable "Realtime" in the JACK "Setup".


For anyone still having trouble installing and configuring WineASIO 0.9.0 with Wine 1.5 on Ubuntu 12.10 (amd64), I've started a dedicated blog on blogger.com to host a complete tutorial that I've written on how to accomplish this. 
*Tell me what you think, feedback on my blog will be very much appreciated.
-Enjoy!
[http://linuxmusiciansunite.blogspot.com/](http://linuxmusiciansunite.blogspot.com/)

---

