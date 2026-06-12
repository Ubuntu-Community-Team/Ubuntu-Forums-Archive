---
title: "another mt-daapd call for help"
date: 2010-12-18
forum: Multimedia Software
---

### Post by theross03 on 2010-12-18
Hello,

I know there are a ton of threads on this topic, but nothing has seemed to work for me so far.  I have a ubuntu machine running Rhythmbox (also tried mt-daapd and forked-daapd) and none of these solutions will successfully show my library in itunes on my wife's winXP machine running itunes 10 (i have also tried itunes 9 with same results).

I am able to hit [http://myip:3689](http://myip:3689) from the winXP machine and get the firefly web GUI, so I don't think its a port configuration issue.

I have also run packet sniffing on the WinXP machine and it appears that when itunes loads, it broadcasts a multicast query looking for a _daap._tcp provider, and then my ubuntu machine responds with its information to the multicast address, but after that, no communication occurs between the two machines.  I am no expert at getting more information out of the packet data, so below is a snippet of the request and response packets from wireshark.

Any ideas why no handshake occurs after both machines send multicast messages regarding _daap._tcp?\

Thanks,
Ross

```


ALPHA (10.0.0.4) is the WinXP machine running iTunes
ross-laptop (10.0.0.2) is the Ubuntu machine (10.04) running Rhythmbox 0.12.8 (firefly gives same results as well)

========
REQUEST
========

No.     Time                       Source                Destination           Protocol Info
    187 2010-12-17 23:45:28.001344 ALPHA.local           224.0.0.251           MDNS     Standard query PTR _appletv-pair._tcp.local, "QM" question PTR _appletv._tcp.local, "QM" question PTR _00000000-51b2-8979-cd97-2d15081d46d9._sub._home-sharing._tcp.local, "QM" question PTR _daap._tcp.local, "QM" question PTR _touch-remote._tcp.local, "QM" question PTR _raop._tcp.local, "QM" question

Frame 187 (206 bytes on wire, 206 bytes captured)
    Arrival Time: Dec 17, 2010 23:45:28.001344000
    [Time delta from previous captured frame: 4.916495000 seconds]
    [Time delta from previous displayed frame: 4.916495000 seconds]
    [Time since reference or first frame: 35.318822000 seconds]
    Frame Number: 187
    Frame Length: 206 bytes
    Capture Length: 206 bytes
    [Frame is marked: True]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: ALPHA.local (00:50:8d:9c:8c:52), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: ALPHA.local (00:50:8d:9c:8c:52)
        Address: ALPHA.local (00:50:8d:9c:8c:52)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: ALPHA.local (10.0.0.4), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 192
    Identification: 0xa0a3 (41123)
    Flags: 0x00
        0.. = Reserved bit: Not Set
        .0. = Don't fragment: Not Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0x2f8a [correct]
        [Good: True]
        [Bad : False]
    Source: ALPHA.local (10.0.0.4)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 172
    Checksum: 0xf79b [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    Transaction ID: 0x0000
    Flags: 0x0000 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 6
    Answer RRs: 0
    Authority RRs: 0
    Additional RRs: 0
    Queries
        _appletv-pair._tcp.local: type PTR, class IN, "QM" question
            Name: _appletv-pair._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        _appletv._tcp.local: type PTR, class IN, "QM" question
            Name: _appletv._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        _00000000-51b2-8979-cd97-2d15081d46d9._sub._home-sharing._tcp.local: type PTR, class IN, "QM" question
            Name: _00000000-51b2-8979-cd97-2d15081d46d9._sub._home-sharing._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        _daap._tcp.local: type PTR, class IN, "QM" question
            Name: _daap._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        _touch-remote._tcp.local: type PTR, class IN, "QM" question
            Name: _touch-remote._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False
        _raop._tcp.local: type PTR, class IN, "QM" question
            Name: _raop._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = "QU" question: False


========
RESPONSE
========

No.     Time                       Source                Destination           Protocol Info
    188 2010-12-17 23:45:28.049932 ross-laptop.local     224.0.0.251           MDNS     Standard query response PTR rhythmbox._daap._tcp.local TXT, cache flush SRV, cache flush 0 0 3689 ross-laptop.local AAAA, cache flush fe80::213:ceff:fe52:ce4b A, cache flush 10.0.0.2

Frame 188 (197 bytes on wire, 197 bytes captured)
    Arrival Time: Dec 17, 2010 23:45:28.049932000
    [Time delta from previous captured frame: 0.048588000 seconds]
    [Time delta from previous displayed frame: 0.048588000 seconds]
    [Time since reference or first frame: 35.367410000 seconds]
    Frame Number: 188
    Frame Length: 197 bytes
    Capture Length: 197 bytes
    [Frame is marked: True]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: TTL low or unexpected]
    [Coloring Rule String: ( ! ip.dst == 224.0.0.0/4 && ip.ttl < 5) || (ip.dst == 224.0.0.0/24 && ip.ttl != 1)]
Ethernet II, Src: IntelCor_52:ce:4b (00:13:ce:52:ce:4b), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
    Destination: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        Address: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: IntelCor_52:ce:4b (00:13:ce:52:ce:4b)
        Address: IntelCor_52:ce:4b (00:13:ce:52:ce:4b)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: ross-laptop.local (10.0.0.2), Dst: 224.0.0.251 (224.0.0.251)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 183
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0.. = Reserved bit: Not Set
        .1. = Don't fragment: Set
        ..0 = More fragments: Not Set
    Fragment offset: 0
    Time to live: 255
        [Expert Info (Note/Sequence): "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Message: "Time To Live" > 1 for a packet sent to the Local Network Control Block (see RFC 3171)]
            [Severity level: Note]
            [Group: Sequence]
    Protocol: UDP (0x11)
    Header checksum: 0x9038 [correct]
        [Good: True]
        [Bad : False]
    Source: ross-laptop.local (10.0.0.2)
    Destination: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
    Source port: mdns (5353)
    Destination port: mdns (5353)
    Length: 163
    Checksum: 0xd311 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    Transaction ID: 0x0000
    Flags: 0x8400 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .1.. .... .... = Authoritative: Server is an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...0 .... .... = Recursion desired: Don't do query recursively
        .... .... 0... .... = Recursion available: Server can't do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 0
    Answer RRs: 5
    Authority RRs: 0
    Additional RRs: 0
    Answers
        _daap._tcp.local: type PTR, class IN, rhythmbox._daap._tcp.local
            Name: _daap._tcp.local
            Type: PTR (Domain name pointer)
            .000 0000 0000 0001 = Class: IN (0x0001)
            0... .... .... .... = Cache flush: False
            Time to live: 1 hour, 15 minutes
            Data length: 12
            Domain name: rhythmbox._daap._tcp.local
        rhythmbox._daap._tcp.local: type TXT, class IN, cache flush
            Name: rhythmbox._daap._tcp.local
            Type: TXT (Text strings)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 1 hour, 15 minutes
            Data length: 15
            Text: Password=false
        rhythmbox._daap._tcp.local: type SRV, class IN, cache flush, priority 0, weight 0, port 3689, target ross-laptop.local
            Name: rhythmbox._daap._tcp.local
            Type: SRV (Service location)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 20
            Priority: 0
            Weight: 0
            Port: 3689
            Target: ross-laptop.local
        ross-laptop.local: type AAAA, class IN, cache flush, addr fe80::213:ceff:fe52:ce4b
            Name: ross-laptop.local
            Type: AAAA (IPv6 address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 16
            Addr: fe80::213:ceff:fe52:ce4b
        ross-laptop.local: type A, class IN, cache flush, addr 10.0.0.2
            Name: ross-laptop.local
            Type: A (Host address)
            .000 0000 0000 0001 = Class: IN (0x0001)
            1... .... .... .... = Cache flush: True
            Time to live: 2 minutes
            Data length: 4
            Addr: 10.0.0.2

```

---

