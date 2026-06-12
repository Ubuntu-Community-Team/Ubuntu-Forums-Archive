---
title: "mDNS Issue?"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by TakeLifeEasy on 2009-07-02
After badgering my company to look at using Ubuntu for their desktop in our mainly Microsoft environment, I have hit a problem which is stopping me showing Ubuntu which I believe is a DNS standards issue.

My company seems to specify the FQDN in everything it does including all the connection strings and links on its website. The added problem is that internally it uses hostname.company.local. From what I have been reading, .local is a reserved top level domain (RFC 2606) which is adding to my problems. So here is the issue -

If I try to ping -
intranet.company.local (where “company” is the name of our company)
It does not resolve. However, if I ping
intranet
I get a succesful response.

If I edit the nsswitch.conf file and comment out the line -
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
I can successfully ping intranet and intranet.company.local.

Now I am no expert when it comes to the nsswitch.conf file but from what I have googled, the line I commented out prevents the Linux box performing a multicast DNS search? I am still trying to get my head around mDNS and struggling to see why it prevents me from using a FQDN.

However, even though I comment out this line and can ping intranet.company.local, when I put this into my web browser, it fails to connect to our Intranet site with a message “The browser could not find the host server for the provided address.”. If I just put intranet into the web browser, it works albeit not displaying the page correctly because I guess we are using Microsoft web standards rather than open standards! Everytime the site tries to use company.local in its links, those links fail. When I edit the link and remove company.local, the site works?

Now I am wondering if I have 2 problems -
1). We should not be using .local top level domain name in our company.
2).I have an issue with the way mDNS is working in our environment.

I really want to demo Linux in our environment but I seem to be failing at the first hurdle. I can hear the comments now “Our Microsoft desktop and servers do not have this problem” & “Linux does not work”. Any ideas as the first of those statements is true?

Many thanks for any help offered.

---

### Post by puppywhacker on 2009-07-02
[https://help.ubuntu.com/community/HowToZeroconf]("https://help.ubuntu.com/community/HowToZeroconf")

I have never understood the need for Multicast DNS, so I don't know how it works exactly. I know that it is for zeroconf. apple called the implementation bonjour, and in linux it's called avahi.

The way the nsswitch.conf works is that it will try to find where a host is located. first it tries to look in the /etc/hosts file and then it will search the dns servers listed in /etc/resolv.conf this order can be defined in nsswitch.conf as follows (effectively stripping the avahi resolving)

```
hosts: files dns
```

you can also ofcourse change the order of where it should resolve hostnames to ip-addresses.

in the resolv.conf you will find the default search domains. So you can have
```
search company.local
search homenetwork.local

```

```
ping www
```
will try to resolve [www.company.local](www.company.local) and if that fails also [www.homenetwork.local](www.homenetwork.local)

---

### Post by TakeLifeEasy on 2009-07-07
First of all, many thanks for your reply as it solved the problem :p

As soon as I stopped the avahi-daemon (sudo /etc/init.d/avahi-daemon stop), I could ping the FQDN and the website worked fine.  The question I now have is, is it OK to stop this and is it going to prevent other things working?  

I do not fully understand why it works, is it -

a). I have turned of a feature which is intended for Linux to function in a small network but not when you utilise your own DNS (if how do companies use Linux in their enterprise).

b). By turning it off, I am now only using our own DNS which ignores the fact that .local should not be used e.g. is .local a reserved name and that is why I am hitting the problem.

Again, many thanks for pointing me to that link, it lead me to solve it!

---

