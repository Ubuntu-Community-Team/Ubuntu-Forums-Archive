---
title: "Network Chaos"
date: 2006-02-12
forum: Networking &amp; Wireless
---

### Post by alphabono on 2006-02-12
Seemingly randomly my network upload rate skyrockets to 5 MB/s and then stays at that rate, blocking all internet activity from my Ubuntu machine and all other machines connected to the LAN via a common router.  The only way I've found to stop it from transmitting and blocking activity is to reboot the ubuntu machine.  The machine is running ubuntu 5.10 and is setup a server (apache, mysql, php, etc).

Things I've tried:

- restart only the network with "sudo /etc/init.d/networking force-reload" also stop, start.  When I restart the network, it instantly jumps back up to 5 MB/s and the internet connection is blocked.
- removing the ethernet cable connecting the router to the PC.  Again, as soon as I reconnect the cable, the problem reoccurs
- removing the cable from the cable modem to the router.  This has NO effect on the 5 MB/s upload speed suggesting the problem is local.  Also the fact that the rate is well beyond my net service providers upload rate quota suggests the problem is local.
- removing all other computers connected to the router.  This has NO effect.

The last time it happened I noticed a coninciding "serious" threat reported in Firestarter firewall.  The offending IP address was 200.140.27.70.  After rebooting, I was able to reproduce the problem by trying to access 200.140.27.70 via my web browser.  Running nslookup on this address returns: 200-140-27-70.cpece705.e.brasiltelecom.net.br

From all these observations, it seems as though the problem is able to be initiated remotely, but that the problem itself is local.

This is all extremely frustrating as I try to host a few sites on my machine.  When this problem occurs in my absence, I remain unaware until I return to the computer or until someone calls asking why they can't access the sites hosted on my server.

 How all these pieces fit together, I have no idea and was hoping someone could help me out.  Any ideas?

Thanks!

---

### Post by ssam on 2006-02-12
you could install ethereal somewhere on the network and have a look at what the packets are. it might give you some clues

---

### Post by bscbrit on 2006-02-12
ssam's suggestion is a good one.

You could also try disconnecting each of the other machines on your lan in turn to see if it is one of them that is causing the problem (if this is possible), or at least it would confirm the fault as being limited to your ubuntu computer and your router.

ssam - my minutes spent reading your website were not wasted; you may keep them with my grateful thanks for a few moments light relief.  Manchester is my hometown but I am now enjoying the warmer climes here.  Judging by your choice of photographs, you ought to get out more often.... :D )

---

### Post by alphabono on 2006-02-12
I've installed ethereal and am waiting for the problem to occur again.  I can no longer invoke it by visiting the IP address mentioned in my first post.  I have tried disconnecting all other machines on the lan - there was no effect on the upload speed and lack of internet functionality.  

I suppose all I can do is wait for it to occur again, run ethereal when that happens, and report back.

Thanks - I'll keep you updated.

---

### Post by alphabono on 2006-02-14
The problem happened again today.  I ran ethereal when it happened and captured some packets.  Here's the info from ethereal:

```
No.     Time        Source                Destination           Protocol Info
      1 0.000000    192.168.1.17          200.164.145.21        UDP      Source port: 38033  Destination port: 7171

Frame 1 (43 bytes on wire, 43 bytes captured)
    Arrival Time: Feb 14, 2006 18:00:31.684663000
    Time delta from previous packet: 0.000000000 seconds
    Time since reference or first frame: 0.000000000 seconds
    Frame Number: 1
    Packet Length: 43 bytes
    Capture Length: 43 bytes
    Protocols in frame: eth:ip:udp:data
Ethernet II, Src: Dell_74:5d:ea (00:12:3f:74:5d:ea), Dst: Cisco-Li_d4:b0:24 (00:13:10:d4:b0:24)
    Destination: Cisco-Li_d4:b0:24 (00:13:10:d4:b0:24)
    Source: Dell_74:5d:ea (00:12:3f:74:5d:ea)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.1.17 (192.168.1.17), Dst: 200.164.145.21 (200.164.145.21)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 29
    Identification: 0x429d (17053)
    Flags: 0x04 (Don't Fragment)
        0... = Reserved bit: Not set
        .1.. = Don't fragment: Set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0xdcbf [correct]
    Source: 192.168.1.17 (192.168.1.17)
    Destination: 200.164.145.21 (200.164.145.21)
User Datagram Protocol, Src Port: 38033 (38033), Dst Port: 7171 (7171)
    Source port: 38033 (38033)
    Destination port: 7171 (7171)
    Length: 9
    Checksum: 0x03d4 [correct]
Data (1 byte)

0000  30                                                0

```

The offending IP address is 200.164.145.21 which returns 200164145021.user.veloxzone.com.br using nslookup.  Ethereal says the protocol is UDP and the source port is 38033 from my machine and the destination port is 7171.  I went and blocked the offending IP address using firestarter which seems to have solved the problem even though disconnecting the router from the internet had no effect.  This seems to be a temporary fix as the offending IP address has changed from last time (though both are from brasil).

Aside from blocking all brasilian IP addresses (which may not even solve the problem), is there any way to prevent this from happening in the future?

Thanks!

---

