---
title: "Wireless hangs periodically"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by pb3004 on 2009-11-17
I have an issue with Xubuntu/Ubuntu where the network connection hangs every 60 seconds or so (see below). My setup is Xubuntu 9.10 running on a Intel Mac Mini.

I know the following:
[LIST]
[*]This is not an issue with the hardware, as I have also tried the ping test (below) with Mac OSX installed and don't get this issue.
[*]It's not an issue with the router channel interference, as I cycled through multiple channels and it made no difference.
[*]The same connection is also fine with my Eee PC also running Xubuntu. 
[/LIST]

I presume it's a driver issue with the Mac Mini hardware but does anyone have any ideas how to resolve it?

```

ping google.com
64 bytes from 74.125.53.100: icmp_seq=274 ttl=50 time=173 ms
64 bytes from 74.125.53.100: icmp_seq=275 ttl=50 time=159 ms
64 bytes from 74.125.53.100: icmp_seq=276 ttl=50 time=170 ms
64 bytes from 74.125.53.100: icmp_seq=277 ttl=50 time=169 ms
64 bytes from 74.125.53.100: icmp_seq=278 ttl=50 time=165 ms
64 bytes from 74.125.53.100: icmp_seq=279 ttl=50 time=177 ms
64 bytes from 74.125.53.100: icmp_seq=280 ttl=50 time=183 ms
64 bytes from 74.125.53.100: icmp_seq=281 ttl=50 time=160 ms
64 bytes from 74.125.53.100: icmp_seq=282 ttl=50 time=161 ms
[B]64 bytes from 74.125.53.100: icmp_seq=285 ttl=50 time=4937 ms
64 bytes from 74.125.53.100: icmp_seq=284 ttl=50 time=5946 ms
64 bytes from 74.125.53.100: icmp_seq=286 ttl=50 time=3931 ms
64 bytes from 74.125.53.100: icmp_seq=288 ttl=50 time=1916 ms
64 bytes from 74.125.53.100: icmp_seq=287 ttl=50 time=2925 ms
64 bytes from 74.125.53.100: icmp_seq=289 ttl=50 time=910 ms[/B]
64 bytes from 74.125.53.100: icmp_seq=290 ttl=50 time=170 ms
64 bytes from 74.125.53.100: icmp_seq=291 ttl=50 time=162 ms
64 bytes from 74.125.53.100: icmp_seq=292 ttl=50 time=168 ms
64 bytes from 74.125.53.100: icmp_seq=293 ttl=50 time=172 ms
64 bytes from 74.125.53.100: icmp_seq=294 ttl=50 time=163 ms
64 bytes from 74.125.53.100: icmp_seq=295 ttl=50 time=165 ms
64 bytes from 74.125.53.100: icmp_seq=296 ttl=50 time=185 ms
64 bytes from 74.125.53.100: icmp_seq=297 ttl=50 time=200 ms
64 bytes from 74.125.53.100: icmp_seq=298 ttl=50 time=175 ms
64 bytes from 74.125.53.100: icmp_seq=299 ttl=50 time=164 ms
64 bytes from 74.125.53.100: icmp_seq=300 ttl=50 time=162 ms
64 bytes from 74.125.53.100: icmp_seq=301 ttl=50 time=160 ms
64 bytes from 74.125.53.100: icmp_seq=302 ttl=50 time=168 ms
64 bytes from 74.125.53.100: icmp_seq=303 ttl=50 time=172 ms
64 bytes from 74.125.53.100: icmp_seq=304 ttl=50 time=165 ms

```

---

