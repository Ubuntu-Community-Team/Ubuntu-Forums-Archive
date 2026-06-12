---
title: "slow connection after ubuntu install, may not be ipv6 problem"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by anthalamus on 2010-07-18
Hi #-o

So I recently installed Ubuntu 10.04 (lucid) on a new computer and I experience some serious network issues. While everything else works perfectly, there are several problems related to the internet (I think they&#8217;re all actually the same problem in fact). I am plugged directly to the wall (100mbs connection) and tests on my windows machine confirm the unusual slowness of the connection on the ubuntu machine. The problems are:

1- delay of approximately 10 seconds in accessing any web page
2- same delay when trying to ssh FROM the ubuntu machine to another one (works though). However I can ssh or use vnc TO the ubuntu machine and it's reasonnably fast
3- I can ping/traceroute (like on google.com), though it seems a bit slower than normal too.

I read this thread: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) as well as some others and it seems it may have to do with ipv6 being enabled. 

I did all this:

```
net.ipv6.conf.all.accept_ra = 0 # added in /etc/sysctl.conf
ip6tables -I INPUT -p ipv6-icmp --icmpv6-type router-advertisement -j DROP
ip -6 r # gives no &#8220;default&#8221; line
lsmod | grep ipv6 # shows nothing
```just in case I also did:
```
echo 'blacklist ipv6' | sudo tee -a '/etc/modprobe.d/blacklist.local' >/dev/null
sudo reboot
```From other threads, I tried:

```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6 # gives 1
net.ipv6.conf.all.disable_ipv6=1 # in /etc/sysctl.conf
sudo sysctl &#8211;p /etc/sysctl.conf
``````

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;ipv6.disable=1 quiet splash&#8221; # from GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221; in /etc/default/grub
Sudo update-grub
ip a | grep inet6 # show nothing after restart
```I rebooted plenty of time and... still slow...!!! maybe a tiny tiny bit faster but it could be just in my head, besides it's still significantly slower than the windows machine (which has less impressive specs, especially less RAM).

Yet all the symptoms of the ipv6 are there: &#8220;This "slow-down" results from DNS resolution failures due to broken NAT 'routers' and other DNS resolvers which don't know how to handle the AAAA DNS query. These DNS resolvers just drop the DNS query request for the AAAA record, instead of returning the appropriate negative DNS response. Because the request is dropped, the host sending the request has to time out, thus causing a perceived slow down when connecting to new hosts. » (from above thread)

I suppose there are ways to monitor more closely what&#8217;s happening, but my knowledge in network commands is insufficient...

Anyone with any idea of what else I could do?? :-k

Thanks!
Anthony

---

### Post by anthalamus on 2010-07-19
Solved!

Thanks to: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1441818&page=9](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1441818&page=9) , which in turns refers to [http://ubuntuforums.org/showthread.php?t=1283146&page=2](http://ubuntuforums.org/showthread.php?t=1283146&page=2)

bottom line being:
1. In /etc/dhcp3/dhclient.conf add the following line:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```2. In /etc/nsswitch.conf edit this line: 
```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```to this:
```
hosts: files dns
```+ restart

Looks like a pretty severe problem that many people suffer(ed) from, including users saying they consider going back to wndows (now THAT is worrying). Hopefully this will be addressed (no pun intended) in subsequent releases..!

):P

---

### Post by bottlehead on 2010-09-01
Thanks, anthalamus, the fixes in your last post fixed my ssh problems.

I had already turned off ipv6 in firefox, which helped there, but the ssh problems remained. But no longer! I think firefox is somewhat faster, too.

This is the same problem that kept me on 9.04, as it was present in 9.10. I've recently downloaded 10.04 to put on my laptop, only to find the network delays were still present.

Thanks again.

---

### Post by petatkinson on 2010-09-11
Wow.What a result.Connection is lightening fast.Thanks for that

---

### Post by landersohn on 2010-09-14
I have the same problem and I will try this solution, thanks for all the work done on this.

The funny thing is only on one of my computers. Both are connected to the same router and ISP same settings. Yet one is normally fast, the other is unusable. Any speculation how a change to DNS may play into this? BTW, on the local side of the router, speeds are great!
The "good" PC is a relatively new HP laptop wit broadcom wireless, the "bad" PC is an older Dell tower with a wired connection. Suffice it to say that the "bad" PC ran just fine under 8.10 and 9.04 before I upgraded to Lucid. So...I have some doubts about the DNS solution.

---

### Post by utilitytrack on 2010-09-14
to **anthalamus**

Please mark this thread as solved.

---

### Post by Cherr on 2010-11-22
Thank you!

---

### Post by cariocap on 2010-11-30
Congratulations,

I changed only /etc/nsswitch.conf and now my Firefox resolves quickly. No need to restart.

The question is, what proccess or maybe update/installation  has modified this line in /etc/nsswitch.conf and cause all this trouble ?

Thanks

---

### Post by cariocap on 2010-11-30
One more information.

The reason of my slow DNS problem is that my hosts: line had a "wins" entry.
Don't know why it was there, but as soon as I remove it, save /etc/nsswitch.conf my Firefox DNS resolution return to normal (fast).
You don't need to restart Ubuntu.

Now my hosts line is:
```
hosts:        files mdns4_minimal [NOTFOUND=return] dns [NOTFOUND=return] mdns4
```

I suspect that winbind package did this...

Anyone know what process or maybe update/installation  has modified this line in /etc/nsswitch.conf and cause all this trouble ?

---

### Post by yogiman.uk on 2010-12-27
> **anthalamus said:**
> Solved!

Thanks to: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1441818&page=9](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1441818&page=9) , which in turns refers to [http://ubuntuforums.org/showthread.php?t=1283146&page=2](http://ubuntuforums.org/showthread.php?t=1283146&page=2)

bottom line being:
1. In /etc/dhcp3/dhclient.conf add the following line:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```2. In /etc/nsswitch.conf edit this line: 
```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```to this:
```
hosts: files dns
```+ restart

Looks like a pretty severe problem that many people suffer(ed) from, including users saying they consider going back to wndows (now THAT is worrying). Hopefully this will be addressed (no pun intended) in subsequent releases..!

):P

Anthalamus,

I've been trying to resolve this issue on both my Desktop and Laptop for months, thanks for your hard work and resolution to this issue, it fixed both my machines and two others in the house!

Cheers

Yogiman!

---

