---
title: "HMA VPN and proxy authentication: &quot;No route to host&quot; error"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by mr.interested on 2011-12-03
Hi there,

I'm connected to the internet that requires proxy authentication. So obviously, when I type, say

```

sudo bash ./hma-start "United Kingdom, Manchester"

```

I get

```

Options error: You must define TUN/TAP device (--dev)
Use --help for more information.

```

So to go through proxy I type

```

sudo http_proxy="http://username:password@proxy:port" bash ./hma-start "United Kingdom, Manchester"

```

and I get

```

Sat Dec  3 13:36:39 2011 OpenVPN 2.2.0 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Jul  4 2011
Enter Auth Username:*****
Enter Auth Password:
Sat Dec  3 13:37:00 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sat Dec  3 13:37:00 2011 WARNING: file './keys/hmauser.key' is group or others accessible
Sat Dec  3 13:37:00 2011 Control Channel MTU parms [ L:1543 D:140 EF:40 EB:0 ET:0 EL:0 ]
Sat Dec  3 13:37:00 2011 Socket Buffers: R=[87380->131072] S=[16384->131072]
Sat Dec  3 13:37:00 2011 Data Channel MTU parms [ L:1543 D:1450 EF:43 EB:4 ET:0 EL:0 ]
Sat Dec  3 13:37:00 2011 Local Options hash (VER=V4): 'db02a8f8'
Sat Dec  3 13:37:00 2011 Expected Remote Options hash (VER=V4): '7e068940'
Sat Dec  3 13:37:00 2011 Attempting to establish TCP connection with [AF_INET]89.238.165.132:443 [nonblock]
Sat Dec  3 13:37:01 2011 TCP: connect to [AF_INET]89.238.165.132:443 failed, will try again in 5 seconds: No route to host
Sat Dec  3 13:37:07 2011 TCP: connect to [AF_INET]89.238.165.132:443 failed, will try again in 5 seconds: No route to host
Sat Dec  3 13:37:13 2011 TCP: connect to [AF_INET]89.238.165.132:443 failed, will try again in 5 seconds: No route to host
Sat Dec  3 13:37:19 2011 TCP: connect to [AF_INET]89.238.165.132:443 failed, will try again in 5 seconds: No route to host
Sat Dec  3 13:37:28 2011 TCP: connect to [AF_INET]89.238.165.132:443 failed, will try again in 5 seconds: No route to host
Sat Dec  3 13:37:37 2011 TCP: connect to [AF_INET]89.238.165.132:443 failed, will try again in 5 seconds: No route to host
Sat Dec  3 13:37:46 2011 TCP: connect to [AF_INET]89.238.165.132:443 failed, will try again in 5 seconds: No route to host

```

It asks me for a username and password, so the proxy authentication works, but no matter to which server I'm trying to connect, I get "No route to host" error. What's the problem?

(The original post on HMA's forum: [http://forum.hidemyass.com/index.php?/topic/5188-connecting-through-proxy-error-no-route-to-host/](http://forum.hidemyass.com/index.php?/topic/5188-connecting-through-proxy-error-no-route-to-host/))

---

