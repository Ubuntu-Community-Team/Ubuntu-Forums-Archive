---
title: "Port 21 is blocked?  can't connect with gFTP"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by Lakeside5 on 2010-09-18
I googled around a bit and tried a few things and this is going to drive me batty for sure :confused: I can't seem to establish a conncction to my site (that I'm hosting in the same computer as the gFTP client- running Lucid Lynx desktop as a server). My site is 'out there', with a domain etc. and also I work on it with localhost.  I wanted to use ftp as Joomla has a 'ftp layer' for files permissions etc.  But it keeps saying that I can't connect,  or the connection 'was reset by a peer'  whatever that means.  For 'hostname' I use  site.com (site is my site's name) and even tried the whole thing like  [http://www.site.com](http://www.site.com) (I clicke on 'connect to remote, and enter that in the url).  or just put it where 'host' goes (when I'm not using localhost)  For user name and pass, I just enter what I usually put to access the administrator's back panel in joomla,  but maybe I am supposed to use what I use to log on to ubuntu when I start my computer? note sure.  Anyway I used a telnet command in the terminal and found that port 21 was blocked.  MY isp says they don't block any ports so I don't know.  I was able to do this last year so I don't know what is so hard about this lol  In the router, I have  'ftp  21 to 21 and ip address 192.168.1.100  (ip is the same for http which is working as I have my site up)
now it seems to be open as I used a command at the terminal (found from google). It's open but my ftp still can't connect to my server either localhost or to my site. there is no firewall blocking it and I think my router is set right.

---

### Post by Lakeside5 on 2010-09-19
No one? lol  I looked at my configuration.php file and wonder if I have a wrong setting for ftp. Should I show a screenshot of my router and conf. file? thanks.
*edit*  I found the terminal command to unblock that port and it is unblocked accordyt to 'shieldsup!' a port tools website...problem is something keeps blocking it as I've had to unblock it a few times and Shields keep showing it's blocked, then open, then blocked again...wonder what keeps blocking it.  I don't think ubuntu has a firewall.  Should I use one of the ftp programs that comes with lucid lynx, or is it ok to use FireFTP (what I'm using now, and seem to be able to use localhost with it)  or filezilla or w/e?

---

