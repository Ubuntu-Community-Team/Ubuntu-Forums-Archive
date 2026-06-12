---
title: "Terminal does not connect to internet (Proxy)"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by kashiqirphan on 2013-07-15
I am using Ubuntu 12.04 LTS on my school`s network, which has a proxy
I am able to go online on Firefox but Terminal is not able to connect, 
Example I try
```
$ ping google.com
```
I get this and there are no more ping replies
```
PING google.com (74.125.236.110) 56(84) bytes of data.
```

Most of the post I read suggested adding the following to /etc/apt/apt.conf
```
Acquire::http::Proxy “http://172.16.0.2:8080/”;
Acquire::ftp::Proxy “http://172.16.0.2:8080/”;
```

Even after doing so there is no luck.

also most people who had similar problems have posted that there Ubuntu Software Center also to be not able to connect to Internet, but mine seems to be working fine.

The following are the network setting information
> IP address: 10.1.104.58
Broadcast Address: 10.1.104.255
Subnet Mask: 255.255.255.0
Default Gateway: 10.1.104.1
Primary DNS: 172.16.111.113
Proxy: 172.16.0.2:8080

I would be very glad if someone could help me with this, Thanks in advance.

---

### Post by slickymaster on 2013-07-15
See this: [No internet for terminal - connect through a proxy]("http://askubuntu.com/questions/308809/no-internet-for-terminal-connect-through-a-proxy")

---

