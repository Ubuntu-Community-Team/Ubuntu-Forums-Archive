---
title: "Much broadcast traffic from and to udp port 19375 &quot;whoisthere&quot;"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by Jay Christnach on 2012-03-17
After upgrading to Natty Narwhal I noticed there is much traffic on my lan, because the leds on my switch are blinking constantly without any internet or local network activity I knew of. I took a look using wireshark and noticed that my pc is broadcasting a few times per second always from and to the same port 19375. The data contains a human readable string "whoisthere", so I suspect it may be some discovery protocol for a networking service.

Searching the net didn't give me any clues. So maybe somebody here knows what is cluttering my lan (and wlan) with broadcasts. Also how could this request be so urgent that it has to be done several times per second? The process list didn't show me any suspect process I would try to stop.

Below I post one of the packets as extracted with wireshark:

```
No.     Time        Source                Destination           Protocol Info
    138 5.144065    192.168.1.33          192.168.1.255         UDP      Source port: 19375  Destination port: 19375

Frame 138: 80 bytes on wire (640 bits), 80 bytes captured (640 bits)
    Arrival Time: Mar 17, 2012 22:41:30.018078000 CET
    Epoch Time: 1332020490.018078000 seconds
    [Time delta from previous captured frame: 0.043571000 seconds]
    [Time delta from previous displayed frame: 0.043571000 seconds]
    [Time since reference or first frame: 5.144065000 seconds]
    Frame Number: 138
    Frame Length: 80 bytes (640 bits)
    Capture Length: 80 bytes (640 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ip:udp:data]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: AbitComp_b2:19:de (00:50:8d:b2:19:de), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
    Destination: Broadcast (ff:ff:ff:ff:ff:ff)
        Address: Broadcast (ff:ff:ff:ff:ff:ff)
        .... ...1 .... .... .... .... = IG bit: Group address (multicast/broadcast)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
    Source: AbitComp_b2:19:de (00:50:8d:b2:19:de)
        Address: AbitComp_b2:19:de (00:50:8d:b2:19:de)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.33 (192.168.1.33), Dst: 192.168.1.255 (192.168.1.255)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 66
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
        0... .... = Reserved bit: Not set
        .1.. .... = Don't fragment: Set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (17)
    Header checksum: 0xb63a [correct]
        [Good: True]
        [Bad: False]
    Source: 192.168.1.33 (192.168.1.33)
    Destination: 192.168.1.255 (192.168.1.255)
User Datagram Protocol, Src Port: 19375 (19375), Dst Port: 19375 (19375)
    Source port: 19375 (19375)
    Destination port: 19375 (19375)
    Length: 46
    Checksum: 0x1b56 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Data (38 bytes)
    Data: 77686f69737468657265003139322e3136382e312e333300...
    [Length: 38]

0000  ff ff ff ff ff ff 00 50 8d b2 19 de 08 00 45 00   .......P......E.
0010  00 42 00 00 40 00 40 11 b6 3a c0 a8 01 21 c0 a8   .B..@.@..:...!..
0020  01 ff 4b af 4b af 00 2e 1b 56 77 68 6f 69 73 74   ..K.K....Vwhoist
0030  68 65 72 65 00 31 39 32 2e 31 36 38 2e 31 2e 33   here.192.168.1.3
0040  33 00 32 35 35 2e 32 35 35 2e 32 35 35 2e 30 00   3.255.255.255.0.
```Best Greetings!

---

### Post by 123basti321 on 2012-04-16
Hi,
same problem here. But I am receiving this from my MacBook ... :-)

Greets

---

### Post by Jay Christnach on 2012-04-16
Of course because it's a broadcast you can see it on the whole subnet. At my place it somehow stopped after rebooting my desktop pc that runs ubuntu linux. The phenomenon never returned since. I really would like to know what application could have been the origin of this. 

Unfortunately we don't get many answers to our technical questions anymore from these webforums. I remember times were you got many clues from the usenet. On the other hand it shows that Linux has become much more popular.

Please let me know if you found anything. If it's still happening, you could kill one process after the other (using system monitor or top or ps and the kill command, beginnning with things you don't know the purpose) and see which one makes it stop. That way we could get a description of the application/process by searching the net for its name.

Kind greetings.

---

### Post by ccour on 2012-09-22
I had the same on my system.

The leds on my hub blink at a frequency above 2 Hz.

WIRESHARK report more than 2 packets/second. All packets are addressed in my local network. 

I use DEVOLOS on my LAN and this behavior seem to change since I deinstall DEVOLO software !!! 

Thanks for sharing your solution

---

### Post by Jay Christnach on 2012-09-22
Hi Ccour,

I almost forgot this thread. I think we have the answer here.

 I also use Devolos and had that software installed. I now passed to 32 bit Xubuntu and I have not install the devolo software until now. The problem never occured again.

I'll mark the thread as solved. Thanks for your reply!

---

