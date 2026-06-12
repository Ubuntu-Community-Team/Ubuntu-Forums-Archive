---
title: "Ad-hoc networks and mobile broadband"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by apkent on 2009-05-17
Hi all, a couple of queries from a very new user....

I'm planning a dedicated home wireless server but as a test, thought I'd better install a copy of Ubuntu 9.04 to try things out.

So, I installed off the live CD to a new partition, no problems. I plugged in my Huawei E160G mobile broadband dongle and got it connected to the net, no problem.

Then I decided to set up an ad-hoc network to firstly share files to my Vista laptop- obviously no problem with my PCI wireless adapter. I used the 'Create New Wireless Network' option and it all seemed ok - the network appeared on Vista's 'Connect to a network' page. But in Vista I get no internet connection from the Ubuntu host, nor any way to access files or settings.

Other than the above, I've not changed the default 9.04 install at all.

What am I doing wrong?

Cheers,
Andy

---

### Post by apkent on 2009-05-17
Right, bit of progress, but still don't feel any nearer.....

I've installed Samba, and chosen my local drive to be shared.

However, I'm still getting nothing through to the Vista laptop.

'Connect to a network' in Vista says the machines are connected, but I can't get them to ping each other? I'm having trouble even working out whether the two machines are on different IP addresses to be honest.

Can any one help or point me in the right direction? It seems like I've looked over tons of tutorials and I'm still no where near :(

---

### Post by superprash2003 on 2009-05-18
in your ubuntu machine go to the terminal and type ifconfig and post output here
in your windows machine go to the command prompt and type ipconfig and post output here

 we first need to see if both the machines have an ip

---

### Post by apkent on 2009-05-19
Right, well it did miraculously start working all by itself I think. I followed a whole load of tutorials doing this that and the other, and then bam, it was working. I could access files from the desktop and the internet was working.

Now all of a sudden, it has decided to stop sharing the internet. I didn't change anything further, just turned the machine on and off as I have been doing for a couple of days.

So, as requested, the output of ifconfig is:

eth0      Link encap:Ethernet  HWaddr 00:12:3f:a4:c6:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31864 (31.8 KB)  TX bytes:31864 (31.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:94.197.223.158  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1440  Metric:1
          RX packets:7523 errors:11 dropped:0 overruns:0 frame:0
          TX packets:6352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:8241269 (8.2 MB)  TX bytes:790392 (790.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:f5:db:6c  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fef5:db6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144775 (144.7 KB)  TX bytes:105604 (105.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-F5-DB-6C-62-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

And the result from ipconfig in Vista is:

Wireless LAN adapter Wireless Network Connection:

      Connection-specific DNS Suffix   . :
      Link-local IPv6 Address  .  .  .  .  . : fe80::50e5:7e67:1aa1:395c%9
      IPv4 Address  .  .  .  .  .  .  .  .  .  . : 10.42.43.10
      Subnet Mask  .  .  .  .  .  .  .  .  .  . : 255.255.255.0
      Default Gateway   .  .  .  .  .  .  .  . : 10.42.43.1

......plus a load of other 'Media Disconnected' connections

Now to me that looks ok? I can still access the files on the desktop, but no internet? I have internet on the desktop itself so that is working, just not being shared properly.....

---

### Post by apkent on 2009-05-19
Oh......I might have fixed it. The 'Available to all users' option seems to be been un-ticked in the wireless connection properties. I ticked it and it worked again.

But why would that un-tick itself?

---

### Post by apkent on 2009-05-20
This is just rediculous. It worked perfectly for a couple of days, now its absolutely useless. It would drop and regain the connection at start-up seemingly randomly. Sometimes I could access files & the internet, sometimes just the internet and sometimes just the files.

So, I reinstalled the OS hoping to get back to a fresh install.

I've been trying for ages looking for a simple tutorial on how to set this up but its hopeless. I've now tried about 3 different routes, all with no different result and with a system that now been messed about with all over again.

So, I'm going to try one last time with a fresh install. 

Can someone please tell me how to get this up and running please. As yet, I've just installed the OS, I haven't even plugged the mobile broadband in yet.

Cheers,
Andy

---

### Post by apkent on 2009-05-21
Pretty please? :)

---

### Post by superprash2003 on 2009-05-21
adhoc setup [http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html](http://www.prash-babu.com/2009/05/how-to-setup-wireless-adhoc-network-in.html)

---

### Post by apkent on 2009-05-21
Thanks prash. I've got the ad-hoc successfully up and running. Both computers have their own IP and can ping each other without problem. 

But, whenever I plug the mobile broadband modem in now, it won't connect to the internet on the Ubuntu machine?

I didn't use the DNS settings in your article as it breaks stops me accessing the internet on the Vista machine (DNS not found errors) but as I say, I now can't get the internet in Ubuntu.

I thought Ubuntu was supposed to be easy to work with :popcorn: :)

---

### Post by apkent on 2009-05-21
In fact Prash, what Ubuntu install are you using?

Would it be easier if I just went back to 8.04 LTS instead?

My original plan was to get everything up and running on the desktop version, then reinstall on the server edition to run headless - at least by that time I would have some sort of idea what I'm doing! Not really going to plan to be honest.....

---

### Post by superprash2003 on 2009-05-22
what did you use for ICS?? try this [http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html](http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html) ..

---

### Post by apkent on 2009-05-22
I didn't even get as far as ICS, as the mobile broadband isn't being properly recognised Ubuntu. It says it has connected, but is unable to connect to any websites.
 
I followed your tutorial to the letter, with the exception of specifying DNS servers on either the host (Ub) or client (Vista).

---

### Post by superprash2003 on 2009-05-22
oh , mobile broadband doesnt work on the main machine as well?

---

### Post by apkent on 2009-05-22
Mobile works perfect on the Vista laptop (with the proprietary connection software), but not the Ubuntu desktop (where it is supposed automatically set-up a working connection but for some reason I get nothing)

---

### Post by superprash2003 on 2009-05-23
ok so you first need to get internet access.try this [http://forums.whirlpool.net.au/forum-replies-archive.cfm/1046813.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1046813.html)

---

