---
title: "laptop specific wireless connection problems an rfkill issue?"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by twodogsdad on 2011-01-19
Hello,
Since upgrading to 10.04, and maybe since 9.10 but it has been a while, my laptop started having wireless connection issues. Many, many other users are posting with the same problems, basically can't connect to a wireless network because it can't be found, the network won't accept the password, various reasons. 

Finally I stumbled, how I feel it is that I find solutions here via search...,  across this thread

[http://ubuntuforums.org/showthread.php?t=1526773](http://ubuntuforums.org/showthread.php?t=1526773)

In reply number 5 pkadetiloye points to his page...

[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

where he suggests that removing the rfkill file and rebooting may solve the issue. 

It has worked for me! 

Since laptops are often left on too long and crash when the battery dies, does the crash somehow mess up the rfkill file? So many people are trying to fix their problems by reinstalling drivers etc... Maybe the problem is not with the wireless but with the way Ubuntu handles the crash. 

I hope this solution is helpful for others...

---

