---
title: "subdomain or dyndns server"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by xmanhattan on 2012-12-16
I have just setup ubuntu server v12 and it appears to be working on my internal server using a static ip address 192.168.1.10 and server domain as example.com.
Now I would like to connect it to the internet.  I have a domain name, eg. mydomainname.com.

Is it possible to setup the ubuntu server to use a subdomain name as ubuntu.mydomainname.com.  My second thoughts are to use it via dyndns but I don't know which is easier.

---

### Post by Cheesehead on 2012-12-16
Certainly it's possible.
Your subdomain server (indeed, any server) will handle whatever incoming traffic arrives.
The job of your DNS forwarder (like DynDns or others) is to resolve the domain/subdomain into the correct IP for your server so the correct traffic arrives to the correct server.

---

### Post by xmanhattan on 2012-12-17
So if these are my dns files, what would be added and where?

```

//--------------------------------
// named.conf
//--------------------------------
options {
    directory "/var/named";
    allow-query{
        127/8;
        192.168.1/24;
    };
    listen-on port 53{
        127/8;
        192.168.1/24;
    };
    pid-file "/var/run/named/named.pid";
};
// secret must be the same as in /etc/rndc.conf
    key "key"{
    algorithm hmac-md5;
    secret "xxxxxxxxxxxxxxx";
};
controls{
    inet 127.0.0.1 allow{
        any;
    }    keys{
        "key";
    };
};
//--------------------------------
// caching only nameserver config
//--------------------------------
zone "." {
    type hint;
    file "named.ca";
};

//--------------------------------
//  zone setups
//--------------------------------
zone "example.com" {
    type master;
    file "named.example.com";
    notify no;
};

//--------------------------------
//  reverse lookups
//--------------------------------
zone "0.0.127.in-addr.arpa" {
    type master;
    file "named.local";
    notify no;
};
zone "1.168.192.in-addr.arpa" {
    type master;
    file "named.1.168.192";
    notify no;
};
//--------------------------------
// end named.conf
//--------------------------------


//--------------------------------
//  dns lookups
//    named.example
//--------------------------------
$TTL    86400
@        IN    SOA    stardust.example.com.    admin.example.com. (
            01 ; serial
            8H ; refresh
            2H ; retry
            7D ; expire
            1D ; default_ttl
            )
@        IN    NS    stardust.example.com.
@        IN    A    192.168.1.10
@        IN    MX    10    mail.example.com.
localhost    IN    A    127.0.0.1
mail        IN    A    192.168.1.10
www        IN    A    192.168.1.10
stardust        IN    A    192.168.1.10



//--------------------------------
//  reverse lookups
//    named.1.168.192
//--------------------------------
$TTL    86400
@        IN    SOA    stardust.example.com.    admin.example.com. (
            01 ; serial
            8H ; refresh
            2H ; retry
            7D ; expire
            1D ; default_ttl
            )
@        IN    NS    stardust.example.com.
10.1.168.192.in-addr.arpa.        IN    PTR    www.example.com.
10.1.168.192.in-addr.arpa.        IN    PTR    mail.example.com.
10        IN    PTR    stardust.example.com.

```

Should I be adding any info into named.ca?

---

### Post by Cheesehead on 2012-12-18
Usually, you want to add a feature to your existing DNS forwarder, not edit your local resolving. That will only affect your machine or LAN.

In other words, you need a service like dyndns if you want to access the server from the internet.

---

### Post by nishant1234 on 2012-12-19
help me to establish a connection in ubuntu through dns

---

### Post by xmanhattan on 2012-12-19
I have setup a dyndns account in the past and from what I remember I can pick a fndn such as myname.linux.dyndns.org.  From there I give access through my adsl router to the account to the static ip address of the ubuntu server but don't I have to add or do anything on the server side?

Additionally, my own domain name has a place for ns3 and ns4.  Couldn't I use these to setup the subdomain that links to the ubuntu server?

---

### Post by Cheesehead on 2012-12-19
Perhaps I misunderstand your need or intent.

I have been trying to tell you about name resolution at the DNS level.
Take a look at [http://dyn.com/support/webhops-and-redirections/](http://dyn.com/support/webhops-and-redirections/)

For example,
myserver.org would resolve to xxx.xxx.xxx.xxx
sybdomain.myserver.our would resolve to xxx.xxx.xxx.xxx:yyyy (same address, but a nonstandard port)

Your router needs a rule to forward port yyyy to the subdomain server.

Your primary server requires no special resolving tools or rules, since all the name resolution is done upstream.

Your subdomain server does need the normal ddns client software, to keep the DDNS provider updated on the current IP address of the server.


However, perhaps you have a different approach?
You seem to be trying to re-route packets to the subdomain, but without any clues about which packets need to go there. That clue is usually the port number.

For example,

mydomain.com resolves to xxx.xxx.xxx.xxx
The router at xxx.xxx.xxx.xxx doesn't receive the name, just the IP address. There is no clue which subdomain the packet is for, so it correctly assumes the sender wants it to go to the default.



Er, does that help more?

---

### Post by xmanhattan on 2012-12-19
Okay, I am now perceiving the whole logic of it.

I will have to try it and see what happens.

Thanks

---

