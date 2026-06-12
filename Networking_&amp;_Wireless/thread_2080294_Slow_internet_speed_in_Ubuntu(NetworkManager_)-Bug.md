---
title: "Slow internet speed in Ubuntu(NetworkManager )-Bug"
date: 2012-11-03
forum: Networking &amp; Wireless
---

### Post by amahi on 2012-11-03
> I have searched many websites trying to find the solution to this problem. I tried such things as disabling IPv6, reconfiguring Firefox, etc... But I could not solve this problem. The problem occurs in each new version of Ubuntu and never gets fixed.

You can see some of my efforts at ([http://forum.ubuntu.ir/index.php/topic,22957.0.html](http://forum.ubuntu.ir/index.php/topic,22957.0.html)) and ( [http://tinyurl.com/9ekhmm5](http://tinyurl.com/9ekhmm5) ) and many other people that mentioned this problem at [http://ubuntuforums.org/](http://ubuntuforums.org/) ...

Description

When I use pppoeconf in a terminal to connect to the Internet, every time I get this warning (in the terminal):

WARNING: ifup -a is disabled in favour of NetworkManager.
Set ifupdown:managed=false in /etc/NetworkManager/NetworkManager.conf.
Plugin rp-pppoe.so loaded

After I fixed this warning (by changing true to false), my Internet speed in Ubuntu has been working such as win7 without any poor perfomance; and when I restore the value to the default the Internet speed is very slow.

Some of information about the case where managed=true:


[COLOR="Red"]more[/COLOR]:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1072916](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1072916)

---

