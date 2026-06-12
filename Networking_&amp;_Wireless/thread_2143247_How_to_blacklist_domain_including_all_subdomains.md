---
title: "How to blacklist domain including all subdomains"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by InspiredIndividual on 2013-05-08
I used to blacklist certain internet sites by editing the hosts file /etc/hosts. Unfortunately, wildcards are not supported, which means that including a line like
```
0.0.0.0 example.com
```
does not block sub.example.com. I would like to be able to block *.example.com and thus I started searching for a solution to emulate this behavior.

There is a lot of information on the internet on how to use dnsmasq for this job, but unfortunately running dnsmasq manually seems to be conflicting with the Network Manager since 12.04 (see [this blog post from a Ubuntu developer]("https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/"). In the blog post the changes to DNS resolving are being explained, including how to set up resolvconf to change the required settings. However, the use of resolvconf for this purpose is apparently deprecated since 12.10?!

I'm running 13.04 and I don't know anymore where to start, very confused... I would be very grateful for any assistance.

---

### Post by Hadaka on 2013-05-08
Hi, this may be an idea to get what you want..

iptables &#8211;A INPUT &#8211;m string &#8211;algo bm &#8211;string &#8220;*blocked.domain&#8221; &#8211;j DROP
[http://eduard.linux.edu/block-domain-with-iptables/](http://eduard.linux.edu/block-domain-with-iptables/)

I know little to nothing bout iptables,but this seems a logical
way to block domains and ip addresses.
good luck.

---

