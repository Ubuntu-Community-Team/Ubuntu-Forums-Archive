---
title: "Intermittent Internet connection"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by iprolonged on 2008-12-02
Hi all,

As per the title: running 8.04 on a desktop, wireless net connection using a Linksys USB. The net connection works fine on my wife's laptop (also running 8.04), and on this Windows XP laptop I'm currently connected with, so I guess it's either a problem with the adapter, or something to do with my network config on the desktop.

The problem is weird: I seem to have an extremely slow connection for a short while, then it completely dies. For example, I can connect to Gmail, but then the page errors out, saying that there was a connection problem. Also, Ubuntu is aware that there are updates available (icon appears in the notification panel), but when I go to download the packages, I get an error like "113 No route to host".

I don't even know where to start with this, so any help much appreciated - I don't want to be lugging this heap of junk XP brick home from work every evening!! :)

Regards,

Dave

---

### Post by t4e on 2008-12-04
i have the same problem and read thru all the "slow internet" threads, i disabled IPv6 in FF, and still no luck...after it works for a while than pages say "waiting for ]www. blah blah" than i get a pop up telling me i am trying to open a php type file, same connection works flawlessly in XP 

someone please help :)

---

### Post by t4e on 2008-12-04
ok...found another thread that i missed before, done all the IPv6 changes suggested there in post #5 and #9 and everything seems to be running as it should now....will report back if that is not the case

[http://ubuntuforums.org/showthread.php?t=181171](http://ubuntuforums.org/showthread.php?t=181171)

---

### Post by iprolonged on 2008-12-08
thanks for the replies - I tried every suggestion in that link, but nothing seems to have worked, and I think I've spotted the problem.

One of the suggestions was to change my DNS entry to use my ISP's servers, which I did, but when I rebooted the machine, something had set the server back to 192.168.1.1

Is this something I need to amend on the router, or is something in Ubuntu hijacking this?

Really appreciate any replies on this, and thanks again to above responder...

Dave

---

### Post by iprolonged on 2008-12-12
Bumping this as I'm still having problems, to the point where I've just done a clean install, and I'm still having the same issue! I can get on the net, but the connection is gone even before a site has finished loading. Also have  issues with BOINC, and Ubuntu updates. I'm pretty sure from reading other posts (above) that this is an issue with my DNS. Below is the output from my hosts and resolv.conf settings:

dave@scanlon-machine:~$ cat /etc/hosts 
127.0.0.1       localhost 
127.0.1.1       scanlon-machine 

# The following lines are desirable for IPv6 capable hosts 
::1     ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts 

dave@scanlon-machine:~$ cat /etc/resolv.conf  
### BEGIN INFO 
# 
# Modified_by:  NetworkManager 
# Process:      /usr/bin/NetworkManager 
# Process_id:   4822 
# 
### END INFO 
 
search home 
nameserver 192.168.1.1

I also have a laptop on the network (also running 8.04), and it has no problem with net access, so it's definitely not the router or my connection to the ISP.

Really appreciate some direction with this!!

Thanks, Dave

---

### Post by razy60 on 2008-12-12
If you look at the wireless connection that is not having the problem and the connection that is what similarities are there. certain settings will be the same(dns etc) but others, IP address for instance need to be different, also check your mtu settings to see that they match. check to see which channel you are using and how the router or pc is set, is it running 802.1x ab or g or all of them, any of these can cause intermittent failures.

Hope its of some help.

Raz

---

### Post by koelec on 2008-12-14
> **razy60 said:**
> If you look at the wireless connection that is not having the problem and the connection that is what similarities are there. certain settings will be the same(dns etc) but others, IP address for instance need to be different, also check your mtu settings to see that they match. check to see which channel you are using and how the router or pc is set, is it running 802.1x ab or g or all of them, any of these can cause intermittent failures.

Hope its of some help.

Raz

Had the same problem after installing ubuntu 8.10 and using level one wnc-0301usb wireless usb stick.
When I changed WEP setting from 48/128bit encryption to 128-bit passphrase it started working properly. Although still once every minute level drops from 100% to less than 50% and web pages take longer to load then.

Chris

---

