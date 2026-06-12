---
title: "ubuntu 9.10 wireless some pages will not load (32 bit)"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by David-IT on 2009-11-18
Ok let me start off by saying i have been searching google for the past 1 and a half hours but most of the links will not load. then i went through ubuntuforums.org and i cant seem to find a solution. i will go through system>administration>networktools then ping say [www.youtube.com](www.youtube.com) packets sent 5 received 5 ok that is cool went fine but when i ping [www.myspace.com](www.myspace.com) or hotmail i will send 5 and receive 0. and please i have been on google and most pages or links do not work sadly so please do not send me any outside links besides ubuntuforums.org because they simply might not work i am also on a hp pavilion dv2419us. i am on a pppoe wireless network at&t dsl please help me :( any help or even idea will be greatly appreciated.


p.s. tried wget [myspace.com](myspace.com) and i get
 --2009-11-18 00:30:54--  [http://myspace.com/](http://myspace.com/)
Resolving myspace.com... 216.178.38.116, 63.135.80.49
Connecting to myspace.com|216.178.38.116|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.myspace.com/](http://www.myspace.com/) [following]
--2009-11-18 00:30:55--  [http://www.myspace.com/](http://www.myspace.com/)
Resolving [www.myspace.com](www.myspace.com)... 216.178.39.11
Connecting to [www.myspace.com|216.178.39.11|:80](www.myspace.com|216.178.39.11|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 42035 (41K) [text/html]
Saving to: `index.html'

100%[======================================>] 42,035       155K/s   in 0.3s    

but when i do wget [www.myspace.com](www.myspace.com) it gets 

cristina@cristina-laptop:~$ wget [www.myspace.com](www.myspace.com)
--2009-11-18 00:32:23--  [http://www.myspace.com/](http://www.myspace.com/)
Resolving [www.myspace.com](www.myspace.com)... 63.135.80.46
Connecting to [www.myspace.com|63.135.80.46|:80](www.myspace.com|63.135.80.46|:80)... 
and never seems to cross that point.....
i also tried to type in the ip directly and nothing... this is wierd...


:( i am also looking through this thread i found here 
[http://ubuntuforums.org/showthread.php?t=557736&page=2](http://ubuntuforums.org/showthread.php?t=557736&page=2)

and i try to do this step this guy said:
<================================================================>
Hey thanks again! This one worked for me:

Code:

pre-up /sbin/ifconfig $IFACE mtu 1492

I put this under the

iface eth0 inet dhcp

section of

/etc/network/interfaces

using gedit as root like this (in terminal):

Code:

gksudo gedit

Now I have a completely unfettered Internet experience with Ubuntu.

This rocks!

Hope this thread can help someone else with the same problem someday! 
<=====================================================================>
so then i add 
pre-up /sbin/ifconfig $IFACE mtu 1492
under everything in that file which is not much lol and reboot but nothing still the same problem... please help me anyone? i really would appreciate it



<======================================================================>
ok wierd i believe adding pre-up /sbin/ifconfig $IFACE mtu 1492 might have fixed my problem as i kept googling trying to find my problem like 3ominutes later my wget [www.myspace.com](www.myspace.com) actually went through so then i tried the webiste and bam goes through fine no problems then hotmail works great but if it did fix my problem why was it not picked up right after i rebooted it....

---

