---
title: "pdnsd permanent cache with adsl failure"
date: 2013-06-27
forum: Networking &amp; Wireless
---

### Post by lollover72 on 2013-06-27
hi all, 


i have installed on my linux pdnsd and asterisk with a 2 sip trunk e 1 dongle for a backup line and all work fine!


my problem is that when dsl fall, the sip protocol in asterisk stop working, and the ip phone inside the lan don't work! this is a know bug that is no still fix by the developer; 
My goal is ensure that the phone still work so that, in case of no dsl i can use dongle for calling!


i have try to simulate adsl failure: unplugging the line cable of my router, pdnsd still resolve the provider ip for 2 minutes, after that stop work:


[root@myserver ~]# nslookup voip.voxvoip.com
Server:         127.0.0.1
Address:        127.0.0.1#53


Non-authoritative answer:
Name:   voip.voxvoip.com
Address: 82.98.86.163


after about 2 minutes nslookup not resolve anymore and tell me
; cannot connect to the server


is possible extend the time for example to 1 hours?

this is my configuration of pdnsd.conf:

global {
        perm_cache=2048;
        cache_dir="/var/cache/pdnsd";
        max_ttl=1w;
        min_ttl=15m;
#       timeout=100;
        run_as="pdnsd";
        paranoid=on;
        server_port=53;
        debug = on;
        server_ip="any";
}
server {
        ip="8.8.8.8";
        timeout=140;
        interval=900;
        uptest=none;
        ping_timeout=600;
        purge_cache=off;
        caching=on;
}
server {
        ip="8.8.4.4";
        timeout=140;
        interval=900;
        uptest=none;
        ping_timeout=600;
        purge_cache=off;
        caching=on;
}
source {
        ttl=86400;
        owner="localhost.";
        serve_aliases=on;
        file="/etc/hosts";
}

rr      {
        ttl=86400;
        owner="localhost.";
        name="1.0.0.127.in-addr.arpa.";
        ptr="localhost.";
        soa="localhost.","root.localhost.",42,86400,900,86400,86400;
}



my /etc/resolv.conf:

nameserver 127.0.0.1


regards

---

