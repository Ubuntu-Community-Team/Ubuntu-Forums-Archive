---
title: "S-chain timeout while using proxychains"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by maysamsh on 2013-05-29
I'm getting this messages when i'm using proxuchains:
```
|S-chain|-<>-[IP]:1234-<--timeout
|DNS-response|: fhr.data.mozilla.com is not exist
|DNS-request| fhr.data.mozilla.com 
|S-chain|-<>-[IP]:1234-<--timeout
|DNS-response|: fhr.data.mozilla.com is not exist
|DNS-request| fhr.data.mozilla.com 
|S-chain|-<>-[IP]:1234-<--timeout
|DNS-response|: fhr.data.mozilla.com is not exist

```
it's my proxyresolv config:
```
#!/bin/sh
# This script is called by proxychains to resolve DNS names


# DNS server used to resolve names
DNS_SERVER=8.8.8.8




if [ $# = 0 ] ; then
    echo "    usage:"
    echo "        proxyresolv <hostname> "
    exit
fi




export LD_PRELOAD=libproxychains.so.3
dig $1 @$DNS_SERVER +tcp | awk '/A.+[0-9]+\.[0-9]+\.[0-9]/{print $5;}'

```

and it's proxychains.conf content (end of file):

```
socks5    [IP]    1234    user    password
```

---

