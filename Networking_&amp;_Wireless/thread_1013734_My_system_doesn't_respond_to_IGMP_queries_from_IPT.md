---
title: "My system doesn't respond to IGMP queries from IPTV server"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by bulek on 2008-12-17
Hi,

I'm receiving IPTV stream from my ISP provider on separate network card with VLC. But I'm loosing streams after determined amount of time, cause it seems that IPTV server is sending IGMP queries every minute and my system doesn't respond. In VLC community they say that IP stack is responsible to generate/act upon IGMP packets.

It's interesting that when vlc connects to multicast stream, proper IGMP report packet is send and also when stream dies and VLC disconnects from stream, it properly sends IGMP leave packet. Only between those events it doesn't respond to periodic IGMP queries...

I'm attaching tcpdump logs (XXX.XXX.XXX.XXX is ip of network interface receiving multicast stream)

Any way to fix this behavour ?

Thanks in advance,

regards,

Bulek.

> 11:09:36.603980 IP (tos 0xc0, ttl 1, id 0, offset 0, flags [DF], proto IGMP (2), length 32, options (RA)) XXX.XXX.XXX.XXX > 239.255.0.124: igmp v2 report 239.255.0.124
        0x0000:  46c0 0020 0000 4000 0102 692b 0a86 7feb
        0x0010:  efff 007c 9404 0000 1600 f983 efff 007c
11:09:37.383951 IP (tos 0xc0, ttl 1, id 0, offset 0, flags [DF], proto IGMP (2), length 32, options (RA)) XXX.XXX.XXX.XXX > 239.255.0.124: igmp v2 report 239.255.0.124
        0x0000:  46c0 0020 0000 4000 0102 692b 0a86 7feb
        0x0010:  efff 007c 9404 0000 1600 f983 efff 007c
11:09:42.171937 IP (tos 0xc0, ttl 1, id 0, offset 0, flags [DF], proto IGMP (2), length 32, options (RA)) XXX.XXX.XXX.XXX > 239.255.0.124: igmp v2 report 239.255.0.124
        0x0000:  46c0 0020 0000 4000 0102 692b 0a86 7feb
        0x0010:  efff 007c 9404 0000 1600 f983 efff 007c
11:09:50.687119 IP (tos 0x0, ttl 1, id 60806, offset 0, flags [none], proto IGMP (2), length 28) 10.134.64.1 > ALL-SYSTEMS.MCAST.NET: igmp query v2
        0x0000:  4500 001c ed86 0000 0102 a1d1 0a86 4001
        0x0010:  e000 0001 1164 ee9b 0000 0000 0000 0000
        0x0020:  0000 0000 0000 0000 0000 0000 0000
11:10:51.228286 IP (tos 0x0, ttl 1, id 61324, offset 0, flags [none], proto IGMP (2), length 28) 10.134.64.1 > ALL-SYSTEMS.MCAST.NET: igmp query v2
        0x0000:  4500 001c ef8c 0000 0102 9fcb 0a86 4001
        0x0010:  e000 0001 1164 ee9b 0000 0000 0000 0000
        0x0020:  0000 0000 0000 0000 0000 0000 0000
11:11:51.665890 IP (tos 0x0, ttl 1, id 61742, offset 0, flags [none], proto IGMP (2), length 28) 10.134.64.1 > ALL-SYSTEMS.MCAST.NET: igmp query v2
        0x0000:  4500 001c f12e 0000 0102 9e29 0a86 4001
        0x0010:  e000 0001 1164 ee9b 0000 0000 0000 0000
        0x0020:  0000 0000 0000 0000 0000 0000 0000
11:12:52.253514 IP (tos 0x0, ttl 1, id 62239, offset 0, flags [none], proto IGMP (2), length 28) 10.134.64.1 > ALL-SYSTEMS.MCAST.NET: igmp query v2
        0x0000:  4500 001c f31f 0000 0102 9c38 0a86 4001
        0x0010:  e000 0001 1164 ee9b 0000 0000 0000 0000
        0x0020:  0000 0000 0000 0000 0000 0000 0000
11:13:52.515966 IP (tos 0x0, ttl 1, id 62775, offset 0, flags [none], proto IGMP (2), length 28) 10.134.64.1 > ALL-SYSTEMS.MCAST.NET: igmp query v2
        0x0000:  4500 001c f537 0000 0102 9a20 0a86 4001
        0x0010:  e000 0001 1164 ee9b 0000 0000 0000 0000
        0x0020:  0000 0000 0000 0000 0000 0000 0000
11:14:53.446270 IP (tos 0x0, ttl 1, id 63185, offset 0, flags [none], proto IGMP (2), length 28) 10.134.64.1 > ALL-SYSTEMS.MCAST.NET: igmp query v2
        0x0000:  4500 001c f6d1 0000 0102 9886 0a86 4001
        0x0010:  e000 0001 1164 ee9b 0000 0000 0000 0000
        0x0020:  0000 0000 0000 0000 0000 0000 0000
11:14:54.373948 IP (tos 0xc0, ttl 1, id 0, offset 0, flags [DF], proto IGMP (2), length 32, options (RA)) XXX.XXX.XXX.XXX > ALL-ROUTERS.MCAST.NET: igmp leave 239.255.0.124
        0x0000:  46c0 0020 0000 4000 0102 79a4 0a86 7feb
        0x0010:  e000 0002 9404 0000 1700 f883 efff 007c
11:14:54.389898 IP (tos 0x0, ttl 1, id 63193, offset 0, flags [none], proto IGMP (2), length 28) 10.134.64.1 > 239.255.0.124: igmp query v2 [max resp time 10] [gaddr 239.255.0.124]
        0x0000:  4500 001c f6d9 0000 0102 8804 0a86 4001
        0x0010:  efff 007c 110a fe79 efff 007c 0000 0000
        0x0020:  0000 0000 0000 0000 0000 0000 0000


---

