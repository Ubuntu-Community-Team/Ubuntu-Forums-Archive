---
title: "Bind Wont Start || Lucid"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2011-08-24
Hi,
I am trying to create a caching name server. I have installed Bind9 & configured it by following instructions from [here]("https://help.ubuntu.com/community/BIND9ServerHowto").

But when I try to restart the service I get 

  ```
$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                        rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [ OK ]
 * Starting domain name service... bind9                                 [COLOR=Red][fail][/COLOR]
```

[COLOR=Black]I found several threads related to this issue but didn't find a fix. [/COLOR]

This is my  /etc/bind/named.conf.options

```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
// the all-0's placeholder.
     forwards {
         8.8.8.8;
                8.8.4.4;
           156.154.70.1;
           156.154.71.1;
           208.67.222.222;
           208.67.220.220;
           198.153.192.1;
           198.153.194.1;
};

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};


```

---

### Post by linuxyogi on 2011-08-24
Changed forwards to forwaders & no more issues. 

I don't remember changing that. :o

---

