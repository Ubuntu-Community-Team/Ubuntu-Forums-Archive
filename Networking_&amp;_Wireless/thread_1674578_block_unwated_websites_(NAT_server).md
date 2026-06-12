---
title: "block unwated websites (NAT server)"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by shafi on 2011-01-24
Hey Guys,
I have a NAT server that shares the bandwidth among many clients. Recently some users are downloading lots of movies and opening flash videos that cause bandwidth problems in the network. How can I block the unwanted websites specially flash videos and some other specific sites from the server? Thanks in advance.

---

### Post by SeijiSensei on 2011-01-24
> **shafi said:**
> Hey Guys,
I have a NAT server that shares the bandwidth among many clients. Recently some users are downloading lots of movies and opening flash videos that cause bandwidth problems in the network. How can I block the unwanted websites specially flash videos and some other specific sites from the server? Thanks in advance.

Run squid in transparent proxy mode on the NAT router box and use iptables to force all HTTP traffic through squid.  You can write rules to block specific locations and even specific mimetypes, like "video/x-flv" for Flash.

Just do a Google search for "squid transparent ubuntu", and you'll see lots of help.

If you're not running a Linux-based router, you'll need to put another box between it and the rest of the network to run Squid.

---

### Post by sikander3786 on 2011-01-25
For setting up Squid Transparent, this might help.

[http://ubuntu4beginners.blogspot.com/2011/01/how-to-setup-transparent-proxy-with.html](http://ubuntu4beginners.blogspot.com/2011/01/how-to-setup-transparent-proxy-with.html)

For filtering content, here is another useful resource.

[http://www.cyberciti.biz/faq/squid-content-filter-block-files/](http://www.cyberciti.biz/faq/squid-content-filter-block-files/)

On my own network, people used to download large files so I defined some delay pools. Here is what it looks like.

```
#############################################################
###################      DELAY POOLS      ###################
#############################################################
acl magic_words1 url_regex -i 192.168
acl magic_words2 url_regex -i ftp .exe .mp3 .vqf .tar.gz .gz .rpm .zip .rar .avi .mpeg .mpe .mpg .qt .iso .raw .wav .mov .flv
acl day time 09:00-22:59

delay_pools 2

delay_class 1 2
delay_parameters 1 -1/-1 -1/-1
delay_access 1 allow magic_words1

delay_class 2 2
delay_parameters 2 384000/384000 40000/384000
delay_access 2 allow day
delay_access 2 deny !day
delay_access 2 allow magic_words2
```

These delay pools limit the download speeds to 40KBps for the file types that have been defined above. There is also a timed delay pool which allows unlimited download speeds from mid-night to 9 a.m. You can tweak them according to your requirements.

---

### Post by shafi on 2011-01-25
> **SeijiSensei said:**
> Run squid in transparent proxy mode on the NAT router box and use iptables to force all HTTP traffic through squid.  You can write rules to block specific locations and even specific mimetypes, like "video/x-flv" for Flash.

Just do a Google search for "squid transparent ubuntu", and you'll see lots of help.

If you're not running a Linux-based router, you'll need to put another box between it and the rest of the network to run Squid.

Thanks, very helpful. Now I got a problem, when I apply the iptables rules 
[HTML]
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.10.1:3128

sudo iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
[/HTML]
then I can not browse any URL, I'm getting the ERR_ACCESS_DENIED message. Any idea?

---

### Post by shafi on 2011-01-26
> **sikander3786 said:**
> For setting up Squid Transparent, this might help.

[http://ubuntu4beginners.blogspot.com/2011/01/how-to-setup-transparent-proxy-with.html](http://ubuntu4beginners.blogspot.com/2011/01/how-to-setup-transparent-proxy-with.html)

For filtering content, here is another useful resource.

[http://www.cyberciti.biz/faq/squid-content-filter-block-files/](http://www.cyberciti.biz/faq/squid-content-filter-block-files/)

On my own network, people used to download large files so I defined some delay pools. Here is what it looks like.


Thank you Sikandar. 
Is this line " delay_parameters 2 384000/384000 40000/384000 " specifies the file size in Bytes? if no, can I specify the file size? e.g; If a file is grater than 5 Mb then define the delay pool.

One thing more, is it possible to define some specific IPs to have normal downloads?

Thanks in advance!

---

### Post by SeijiSensei on 2011-01-26
> **shafi said:**
> One thing more, is it possible to define some specific IPs to have normal downloads?

You can do nearly anything with Squid acl's.  For instance,

```

acl MYNETWORK src 192.168.1.0/24
acl BIGBOSS src 192.168.1.37
acl facebook dstdom_regex \.facebook\.com$
[...]

http_access allow BIGBOSS
http_access deny facebook

http_access allow localhost
http_access allow MYNETWORK
http_access deny all

```

This grants the IP at 192.168.1.37 unfiltered access, but the rest of 192.168.1.0/24 will be blocked from Facebook.

(I use upper-case characters for acl's that grant permissions and lower-case characters for acl's that block. That's a personal convention to help readability in long ACL lists.)

If people move around and use different machines during the day, IP-based rules might not work.  You'll then need to look into authentication in Squid and grant access based on the user's name.

---

