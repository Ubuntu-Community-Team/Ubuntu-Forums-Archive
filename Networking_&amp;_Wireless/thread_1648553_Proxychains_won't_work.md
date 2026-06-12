---
title: "Proxychains won't work?"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by chroniccommand on 2010-12-18
Well I just installed proxychains, tor and polipo. I edited my /etc/proxychains.conf file and added some to the bottom. Heres my list:
```

# proxychains.conf  VER 3.1
#
#        HTTP, SOCKS4, SOCKS5 tunneling proxifier with DNS.
#    

# The option below identifies how the ProxyList is treated.
# only one option should be uncommented at time,
# otherwise the last appearing option will be accepted
#
dynamic_chain
#
# Dynamic - Each connection will be done via chained proxies
# all proxies chained in the order as they appear in the list
# at least one proxy must be online to play in chain
# (dead proxies are skipped)
# otherwise EINTR is returned to the app
#
#strict_chain
#
# Strict - Each connection will be done via chained proxies
# all proxies chained in the order as they appear in the list
# all proxies must be online to play in chain
# otherwise EINTR is returned to the app
#
#random_chain
#
# Random - Each connection will be done via random proxy
# (or proxy chain, see  chain_len) from the list.
# this option is good to test your IDS :)

# Make sense only if random_chain
#chain_len = 2

# Quiet mode (no output from library)
#quiet_mode

# Proxy DNS requests - no leak for DNS data
proxy_dns 

# Some timeouts in milliseconds
tcp_read_time_out 15000
tcp_connect_time_out 8000

# ProxyList format
#       type  host  port [user pass]
#       (values separated by 'tab' or 'blank')
#
#
#        Examples:
#
#                socks5    192.168.67.78    1080    lamer    secret
#        http    192.168.89.3    8080    justu    hidden
#         socks4    192.168.1.49    1080
#            http    192.168.39.93    8080    
#        
#
#       proxy types: http, socks4, socks5
#        ( auth types supported: "basic"-http  "user/pass"-socks )
#
[ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
socks4     127.0.0.1 9050
socks5  74.140.169.41 27977
socks5  72.218.43.131 5033
socks4  178.239.57.16 1080
socks4  117.79.94.160 1080
socks4  209.203.51.34 1080
```

So I start running polipo, then I open another terminal tab and type:
```
proxychains wget http://ipchicken.com/
```

And this is the output I get every time:
```

chronic@ubuntu:~$ proxychains wget http://ipchicken.com/
ProxyChains-3.1 (http://proxychains.sf.net)
--2010-12-18 23:22:32--  http://ipchicken.com/
Resolving ipchicken.com... |DNS-request| ipchicken.com 
|D-chain|-<>-127.0.0.1:9050-<>-74.140.169.41:27977-<>-72.218.43.131:5033-<>-178.239.57.16:1080-<>-117.79.94.160:1080-<>-209.203.51.34:1080-<--timeout
|D-chain|-<>-127.0.0.1:9050-<>-74.140.169.41:27977-<>-72.218.43.131:5033-<>-178.239.57.16:1080-<>-117.79.94.160:1080-<><>-4.2.2.2:53-<><>-OK
|D-chain|-<>-127.0.0.1:9050-<>-74.140.169.41:27977-<--denied
|D-chain|-<>-127.0.0.1:9050-<>-72.218.43.131:5033-<>-178.239.57.16:1080-<>-117.79.94.160:1080-<><>-4.2.2.2:53-<><>-OK
|D-chain|-<>-127.0.0.1:9050-<>-72.218.43.131:5033-<>-178.239.57.16:1080-<>-117.79.94.160:1080-<><>-4.2.2.2:53-<><>-OK
|DNS-response|: ipchicken.com is not exist
failed: Unknown error.
wget: unable to resolve host address `ipchicken.com'

```
Could anybody help me with this problem?

---

### Post by Calimo on 2010-12-19
Hi,
You have a line "proxy_dns" enabled. Most likely you're still using you ISP DNS, which are often disabled for "outside" use (and with proxy you're looking like being "outside").

Try a public DNS like google's 8.8.8.8 (add a new line "nameserver 8.8.8.8" without the quotes at the top of your /etc/resolv.conf file) to see if I'm right.

---

### Post by dodo3773 on 2010-12-22
> **Calimo said:**
> Hi,
You have a line "proxy_dns" enabled. Most likely you're still using you ISP DNS, which are often disabled for "outside" use (and with proxy you're looking like being "outside").

Try a public DNS like google's 8.8.8.8 (add a new line "nameserver 8.8.8.8" without the quotes at the top of your /etc/resolv.conf file) to see if I'm right.

Tried your solution with proxy_dns commented and uncommented. Also with tor running and not running. It did not work for me. I am very interested in getting this to work. If you have any further advice I will happily guinea-pig it.  I have tried almost everything. Been banging my head against the wall for like 4 or 5 months. Thanks in advance.

---

