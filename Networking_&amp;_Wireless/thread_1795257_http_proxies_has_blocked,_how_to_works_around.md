---
title: "http proxies has blocked, how to works around?"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by inject0r on 2011-07-02
Hello every one,

Recently My ISP provider blocked any kind of http proxies can be used in browsers. When I put my proxy settings in my browser, it keeps loading with no response.  I've squid proxy running on my own server and worked fine before that modification.
I tried to do traceroute and found interesting thing "line in red":
> traceroute to google.com (209.85.148.103), 30 hops max, 60 byte packets
 1  * * *
 2  172.17.0.xxx (172.17.0.xxx)  166.481 ms *  194.361 ms
 3  172.17.0.xxx (172.17.0.xxx)  194.291 ms  214.242 ms  234.189 ms
[COLOR="Red"] 4  10.0.5.2 (10.0.5.2)  274.135 ms  326.137 ms  159.830 ms[/COLOR]
 5  172.17.1.1 (172.17.1.1)  167.689 ms  179.645 ms  179.582 ms
 6  82.137.192.194 (82.137.192.194)  220.266 ms  220.195 ms  199.930 ms
 7  82.137.192.206 (82.137.192.206)  219.673 ms  231.821 ms  231.796 ms
 8  pos2-0.cr01.ldn01.pccwbtn.net (63.218.54.85)  271.785 ms  267.755 ms  267.659 ms
 9  TenGE11-2.br02.ldn01.pccwbtn.net (63.218.12.146)  271.760 ms  279.780 ms  291.626 ms
10  195.66.226.125 (195.66.226.125)  286.950 ms 195.66.224.125 (195.66.224.125)  298.889 ms 195.66.226.125 (195.66.226.125)  291.695 ms
11  64.233.175.27 (64.233.175.27)  291.805 ms 209.85.255.175 (209.85.255.175)  267.771 ms 64.233.175.27 (64.233.175.27)  287.788 ms
12  72.14.233.63 (72.14.233.63)  219.817 ms  199.754 ms  231.653 ms
13  209.85.248.183 (209.85.248.183)  227.846 ms  219.801 ms  235.821 ms
14  209.85.254.41 (209.85.254.41)  219.544 ms 209.85.254.57 (209.85.254.57)  227.707 ms 209.85.254.41 (209.85.254.41)  407.638 ms
15  fra07s07-in-f103.1e100.net (209.85.148.103)  379.794 ms  411.762 ms  371.844 ms


Now the questions:
- How they succeeded in denying http proxies?
- Is the ip address in the red line above means that ISP put us in vpn network so that prevent using proxies?
- Is it possible to bypass that?, something like encrypt my request using such middle software which can act as following:
client ==HTTP request==>  Middle software (client side) ==encrypted request==> Squid proxy ==Original HTTP request==> Target

Any suggestions to bypass sure will be welcome,

Thanks for help in advance, and sorry for my bad language ^_^

inject0r,

---

### Post by inject0r on 2011-07-02
up

---

### Post by kerry_s on 2011-07-02
The forum code does not allow helping on this matter. 
You'll need to settle with your isp

---

### Post by Iowan on 2011-07-02
Bypassing limitations placed by your ISP is not a valid topic for these forums.

---

