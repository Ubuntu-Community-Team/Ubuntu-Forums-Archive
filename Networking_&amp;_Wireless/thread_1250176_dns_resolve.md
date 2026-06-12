---
title: "dns resolve"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by bokiv_mkd on 2009-08-26
Hi , 
i just installed Ubuntu-server 9.04, everything is fine except DNS resolving.  i install bing9 (i will use as a caching only server) ,  when i try to test it with " dig domain.com it resolve. But when i try to resolve from another computer in my network it couldn't.

here is my named.conf.option :

dns6@DNS6:/etc/bind$ more named.conf.options
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      0.0.0.0;
        // };
        max-ncache-ttl 1000;
        max-cache-ttl 1000;
        max-cache-size 150m;
        recursive-clients 4000;
        notify no;
        cleaning-interval 60;
        recursion yes;
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

Also i try to use port scanner to see if port 53 is open, that is ok.  

Can anyone help me solving this problem.

---

### Post by superprash2003 on 2009-08-26
have you configured ICS?

---

### Post by bokiv_mkd on 2009-08-26
No, how should i do??

---

### Post by Iowan on 2009-08-26
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a place to start.

---

### Post by bokiv_mkd on 2009-08-27
Thanks for your reply,
:)

At this moment i am using other DNS servers which are configured without ICS, previously i installed Ubuntu 8.04 desktop (for testing) and everything works fine, so i decided to pre-install it and put Ubuntu 9.04 sever edition. Also there are other 2 servers (Debian, SUSE) which are working perfectly for me i didn`t configure ICS on then. That are directly connected on a switch , using public ip-add....all other computers in my network are resolving with the other 2 DNS, but when i try to resolve it from this it not work.

regards 
Bojan

---

