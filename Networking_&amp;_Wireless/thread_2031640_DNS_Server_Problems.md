---
title: "DNS Server Problems"
date: 2012-07-22
forum: Networking &amp; Wireless
---

### Post by xtropx on 2012-07-22
[FONT=Arial]I am trying to set up a simple caching name server with Bind. All I did was install it and change the /etc/bind/named.conf.options file to:


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

         forwarders {
                208.67.222.222;
                208.67.220.220;
         };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
```THEN

[/FONT][FONT=Arial]```
/etc/init.d/bind9 restart
```THEN

[/FONT]```
ufw disable
```[FONT=Arial]

But when I point my windows machine to use the IPv4 address of this caching DNS server, it will not resolve anything. Maybe I am mistaken in the first place thinking it will?
[/FONT][FONT=Arial]



[/FONT]

---

### Post by efflandt on 2012-07-22
Although defaults should be to listen-on any interfaces and allow queries from all, I wonder if for safety it defaults to none.  Wouldn't hurt to try something like:

```
listen-on port 53 { 127/8; 192.168/16; };

allow-query { 127/8; 192.168/16; };
```

Do **netstat -ltn**  and **natstat -lun** show anything listening on port 53?

---

