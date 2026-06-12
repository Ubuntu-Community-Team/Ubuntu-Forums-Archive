---
title: "Slow internet connection"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by ellesgaard on 2011-04-21
Hi!

I am totally new to ubuntu and linux. I work on MacOS before but now I have to see what it all is about.
I have installed Ubuntu 10.10 dekstop edition.

My problem is on the Ubuntu-machine the internet is slow. I have tried to take a speedtest, and on the Ubuntu i am downloading with about 1,8Mbit and on the Mac and Windows machines i am downloading around 18Mbit.

I have tried this: [http://ubuntuforums.org/showthread.php?t=1690870](http://ubuntuforums.org/showthread.php?t=1690870), but no luck. As [gdshukla]("http://ubuntuforums.org/member.php?u=1241615") writes in the last post, when I run the command: 

```
echo "#disable ipv6" | gksudo tee -a /etc/sysctl.conf && echo "net.ipv6.conf.all.disable_ipv6 = 1" | gksudo tee -a /etc/sysctl.conf && echo "net.ipv6.conf.default.disable_ipv6 = 1" | gksudo tee -a /etc/sysctl.conf && echo "net.ipv6.conf.lo.disable_ipv6 = 1" | gksudo tee -a /etc/sysctl.conf
```the terminal don't return back.


I hope you can help me.

---

### Post by azkraja on 2011-04-21
Hi, I am also a newbie to Ubuntu, i have installed Ubuntu 10.10 and having same problem with my EVDO CDMA connection, after installation in a separate drive on same machine where windows seven already installed (Duel Boot) try to update via Update Manager but due to very low download speed 4.1k/b to 8.9 k/b unable to update. while i am getting 300 k/b download speed on same machine by Windows 7. (My connection is EVDO CDMA Wireless 3.1 MB. 
If some one let us now step by step settings of EVDO / Wireless an lan connections with screen short will be highly appropriated.

---

