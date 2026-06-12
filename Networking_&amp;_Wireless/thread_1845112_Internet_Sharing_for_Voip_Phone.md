---
title: "Internet Sharing for Voip Phone"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by oneadvent on 2011-09-16
Hi!

I am trying to share my wireless internet connection with my VOIP phone by using my built in NIC card to share internet. I have that working. The phone has a web browser on it and I can go to google, and to local websites I have setup in my intranet.

HOWEVER, I cannot seem to get it to register with my server. I know that the settings are right because when I plug it directly into my router it works fine. I have the phone network set up dynamically. The phone is showing a good ip address (would have to for it to get internet, but just being clear). 

I turned off my firewall by: ```
oneadvent@oneadvent-desktop:~$ sudo iptables -P INPUT ACCEPT
oneadvent@oneadvent-desktop:~$ sudo iptables -P OUTPUT ACCEPT
oneadvent@oneadvent-desktop:~$ sudo iptables -F

```

And double checked that ufw wasn't running by: ```
oneadvent@oneadvent-desktop:~$ sudo ufw disable
Firewall stopped and disabled on system startup

```

So I feel stuck. I know internet sharing is working but I cannot seem to get it to register the phone.

Any help is appreciated. 

PS I watched my logs on the PBX and it never shows the phone even trying, it's as if the registration never makes it past my local machine here.

---

### Post by oneadvent on 2011-09-17
BUMP!

And I want to amend that I can actually go to the website that the PBX is spitting out on 80 (Freepbx) no problem. So I know I can route to that particular machine.

---

### Post by oneadvent on 2011-10-03
BUMP! same problem. Someone suggested that the 5060-5061 (which is what asterisk uses for phones ) isn't forwarding correctly.

---

### Post by jonobr on 2011-10-05
Hello


Just wondering if you doing any kind of NAT with your device?

If you are then that could be causing your issue.
NAT and regular traffic can be worked around, however it can cuase all sorts of problems with Voip
[Here is an artical on NAT and VoIP]("http://www.voip-info.org/wiki/view/NAT+and+VOIP")

The resolution to these issues usually require either public IPs or STUN or some kind of tunneling.

---

### Post by oneadvent on 2011-10-05
I haven't tried a public IP. Let me try that! I'm sure frustrated. I'm not sure how to setup the NAT for this.

Thanks.

PS I have to do it when I get home, sorry.

---

### Post by jonobr on 2011-10-05
No Probs

Just one thing,
If you dont have a NAT now then its not likely to be your issue,

Any SIP related issues , if you can trace them (wireshark or tcpdump etc), I would be happy to look at them for you

---

### Post by oneadvent on 2011-10-05
I guess I'm not sure what NAT settings you are referring to, sorry. The phone gets internet, it has a web browser so i know that. 

The outside address did not work. I know that is active because I use it with my phone. I watched the PBX and get nothing coming through with asterisk -vrrr so it doesn't even try to register.

Thanks again!

---

### Post by oneadvent on 2011-10-05
wireshark log during an attempted registration:

```


No.     Time        Source                Destination           Protocol Info
     13 19.510327   10.42.43.72           192.168.1.194         SIP      Unknown request: PING sip:192.168.1.194:5060

Frame 13: 509 bytes on wire (4072 bits), 509 bytes captured (4072 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Internet Protocol, Src: 10.42.43.72 (10.42.43.72), Dst: 192.168.1.194 (192.168.1.194)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     14 19.518434   192.168.1.194         10.42.43.72           SIP      Status: 501 Method Not Implemented

Frame 14: 510 bytes on wire (4080 bits), 510 bytes captured (4080 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Internet Protocol, Src: 192.168.1.194 (192.168.1.194), Dst: 10.42.43.72 (10.42.43.72)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     15 20.019786   10.42.43.72           192.168.1.194         SIP      Unknown request: PING sip:192.168.1.194:5060

Frame 15: 509 bytes on wire (4072 bits), 509 bytes captured (4072 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Internet Protocol, Src: 10.42.43.72 (10.42.43.72), Dst: 192.168.1.194 (192.168.1.194)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     16 20.025416   192.168.1.194         10.42.43.72           SIP      Status: 501 Method Not Implemented

Frame 16: 510 bytes on wire (4080 bits), 510 bytes captured (4080 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Internet Protocol, Src: 192.168.1.194 (192.168.1.194), Dst: 10.42.43.72 (10.42.43.72)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     17 21.030397   10.42.43.72           192.168.1.194         SIP      Unknown request: PING sip:192.168.1.194:5060

Frame 17: 509 bytes on wire (4072 bits), 509 bytes captured (4072 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Internet Protocol, Src: 10.42.43.72 (10.42.43.72), Dst: 192.168.1.194 (192.168.1.194)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     18 21.032732   192.168.1.194         10.42.43.72           SIP      Status: 501 Method Not Implemented

Frame 18: 510 bytes on wire (4080 bits), 510 bytes captured (4080 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Internet Protocol, Src: 192.168.1.194 (192.168.1.194), Dst: 10.42.43.72 (10.42.43.72)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     19 23.040027   10.42.43.72           192.168.1.194         SIP      Unknown request: PING sip:192.168.1.194:5060

Frame 19: 509 bytes on wire (4072 bits), 509 bytes captured (4072 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Internet Protocol, Src: 10.42.43.72 (10.42.43.72), Dst: 192.168.1.194 (192.168.1.194)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     20 23.042193   192.168.1.194         10.42.43.72           SIP      Status: 501 Method Not Implemented

Frame 20: 510 bytes on wire (4080 bits), 510 bytes captured (4080 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Internet Protocol, Src: 192.168.1.194 (192.168.1.194), Dst: 10.42.43.72 (10.42.43.72)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     21 25.384842   Dfi_fc:39:5a          LnSritha_a5:6d:fe     ARP      Who has 10.42.43.72?  Tell 10.42.43.1

Frame 21: 42 bytes on wire (336 bits), 42 bytes captured (336 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     22 25.385132   LnSritha_a5:6d:fe     Dfi_fc:39:5a          ARP      10.42.43.72 is at 00:1a:7e:a5:6d:fe

Frame 22: 60 bytes on wire (480 bits), 60 bytes captured (480 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     23 36.275208   10.42.43.72           192.168.1.194         SIP      Unknown request: PING sip:192.168.1.194:5060

Frame 23: 516 bytes on wire (4128 bits), 516 bytes captured (4128 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Internet Protocol, Src: 10.42.43.72 (10.42.43.72), Dst: 192.168.1.194 (192.168.1.194)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     24 36.278087   192.168.1.194         10.42.43.72           SIP      Status: 501 Method Not Implemented

Frame 24: 517 bytes on wire (4136 bits), 517 bytes captured (4136 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Internet Protocol, Src: 192.168.1.194 (192.168.1.194), Dst: 10.42.43.72 (10.42.43.72)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     25 36.782580   10.42.43.72           192.168.1.194         SIP      Unknown request: PING sip:192.168.1.194:5060

Frame 25: 516 bytes on wire (4128 bits), 516 bytes captured (4128 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Internet Protocol, Src: 10.42.43.72 (10.42.43.72), Dst: 192.168.1.194 (192.168.1.194)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     26 36.784799   192.168.1.194         10.42.43.72           SIP      Status: 501 Method Not Implemented

Frame 26: 517 bytes on wire (4136 bits), 517 bytes captured (4136 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Internet Protocol, Src: 192.168.1.194 (192.168.1.194), Dst: 10.42.43.72 (10.42.43.72)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     27 37.792124   10.42.43.72           192.168.1.194         SIP      Unknown request: PING sip:192.168.1.194:5060

Frame 27: 516 bytes on wire (4128 bits), 516 bytes captured (4128 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Internet Protocol, Src: 10.42.43.72 (10.42.43.72), Dst: 192.168.1.194 (192.168.1.194)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     28 37.793685   192.168.1.194         10.42.43.72           SIP      Status: 501 Method Not Implemented

Frame 28: 517 bytes on wire (4136 bits), 517 bytes captured (4136 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Internet Protocol, Src: 192.168.1.194 (192.168.1.194), Dst: 10.42.43.72 (10.42.43.72)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     29 39.802412   10.42.43.72           192.168.1.194         SIP      Unknown request: PING sip:192.168.1.194:5060

Frame 29: 516 bytes on wire (4128 bits), 516 bytes captured (4128 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Internet Protocol, Src: 10.42.43.72 (10.42.43.72), Dst: 192.168.1.194 (192.168.1.194)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     30 39.805072   192.168.1.194         10.42.43.72           SIP      Status: 501 Method Not Implemented

Frame 30: 517 bytes on wire (4136 bits), 517 bytes captured (4136 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Internet Protocol, Src: 192.168.1.194 (192.168.1.194), Dst: 10.42.43.72 (10.42.43.72)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     31 41.271689   LnSritha_a5:6d:fe     Dfi_fc:39:5a          ARP      Who has 10.42.43.1?  Tell 10.42.43.72

Frame 31: 60 bytes on wire (480 bits), 60 bytes captured (480 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     32 41.271715   Dfi_fc:39:5a          LnSritha_a5:6d:fe     ARP      10.42.43.1 is at 00:01:29:fc:39:5a

Frame 32: 42 bytes on wire (336 bits), 42 bytes captured (336 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     33 45.631326   10.42.43.1            224.0.0.251           MDNS     Standard query PTR _presence._tcp.local, "QM" question

Frame 33: 80 bytes on wire (640 bits), 80 bytes captured (640 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
Internet Protocol, Src: 10.42.43.1 (10.42.43.1), Dst: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
Domain Name System (query)

No.     Time        Source                Destination           Protocol Info
     34 45.742779   10.42.43.1            224.0.0.251           MDNS     Standard query response PTR oneadvent@oneadvent-desktop._presence._tcp.local TXT, cache flush SRV, cache flush 0 0 5298 oneadvent-desktop.local AAAA, cache flush fe80::201:29ff:fefc:395a A, cache flush 10.42.43.1

Frame 34: 384 bytes on wire (3072 bits), 384 bytes captured (3072 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: IPv4mcast_00:00:fb (01:00:5e:00:00:fb)
Internet Protocol, Src: 10.42.43.1 (10.42.43.1), Dst: 224.0.0.251 (224.0.0.251)
User Datagram Protocol, Src Port: mdns (5353), Dst Port: mdns (5353)
Domain Name System (response)

No.     Time        Source                Destination           Protocol Info
     35 53.087423   10.42.43.72           192.168.1.194         SIP      Unknown request: PING sip:192.168.1.194:5060

Frame 35: 515 bytes on wire (4120 bits), 515 bytes captured (4120 bits)
Ethernet II, Src: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe), Dst: Dfi_fc:39:5a (00:01:29:fc:39:5a)
Internet Protocol, Src: 10.42.43.72 (10.42.43.72), Dst: 192.168.1.194 (192.168.1.194)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

No.     Time        Source                Destination           Protocol Info
     36 53.089738   192.168.1.194         10.42.43.72           SIP      Status: 501 Method Not Implemented

Frame 36: 516 bytes on wire (4128 bits), 516 bytes captured (4128 bits)
Ethernet II, Src: Dfi_fc:39:5a (00:01:29:fc:39:5a), Dst: LnSritha_a5:6d:fe (00:1a:7e:a5:6d:fe)
Internet Protocol, Src: 192.168.1.194 (192.168.1.194), Dst: 10.42.43.72 (10.42.43.72)
User Datagram Protocol, Src Port: sip (5060), Dst Port: sip (5060)
Session Initiation Protocol

```

---

### Post by jonobr on 2011-10-05
Do you own the pBx can you run tcpdump on it?

```
sudo tcpdump -w trace.pcap -s 1600 -i any port 5060
```
and post the results

Msy also be worthwhile sending to me personally as opposed to posting private info here

---

### Post by oneadvent on 2011-10-05
Yes, it's in my house. I ran as root:
```
root@joshsphone:~ $ sudo tcpdump -w trace.pcap -s 1600 -i any port 5060                                           
tcpdump: WARNING: Promiscuous mode not supported on the "any" device                                              
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 1600 bytes                            
36 packets captured                                                                                               
38 packets received by filter                                                                                     
0 packets dropped by kernel                                                                                       
root@joshsphone:~ $      
```

Thanks for the help, hope this is getting closer!

---

### Post by oneadvent on 2011-10-05
Oh, and I've been trying to be careful not to give out the public IP...mighta missed one, but I'm trying.

---

### Post by jonobr on 2011-10-05
Sorry 

I should have been a bit clearer

The command you ran created a file called trace.pcap

I can see from the result it caught 36 packets on port 5060,

could you send the trace.pcap to me again, if your OK with posting it, post here,
if not post to me in a private message

---

### Post by oneadvent on 2011-10-05
I'm sending it to you privately. I do not know how to open it, so I do not know what is in it.

---

### Post by jonobr on 2011-10-05
Got it, but it appears empty,

This can be opened with wireshark for ubuntu or windows.

---

### Post by jonobr on 2011-10-06
Any luck with that file ?

if no, 

maybe you could try 
```
tcpdump -vvv -i any port 5060
```

or even better, install ngrep
and do

```
ngrep -n port 5060 
```

---

### Post by oneadvent on 2011-10-07
```
root@joshsphone:~ $ tcpdump -vvv -i any port 5060
tcpdump: WARNING: Promiscuous mode not supported on the "any" device
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
14:06:20.397505 IP (tos 0xb8, ttl  61, id 56901, offset 0, flags [none], proto: UDP (17), length: 539) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 511
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:716@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\032\373\011p\030\373\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\030\373\011\310m\377\011files\000\000\000\000\000\000\000\021\000\000\000\350\034\373\011\270\034\373\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030n\377\011\360m\377\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3640
14:06:20.397709 IP (tos 0x60, ttl  64, id 27135, offset 0, flags [none], proto: UDP (17), length: 537) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 509
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\032\373\011p\030\373\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\030\373\011\310m\377\011files\000\000\000\000\000\000\000\021\000\000\000\350\034\373\011\270\034\373\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030n\377\011\360m\377\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450

```

Does that help??

---

### Post by oneadvent on 2011-10-07
or maybe this:

```
14:08:37.151734 IP (tos 0x68, ttl 250, id 6633, offset 0, flags [none], proto: UDP (17), length: 350) 192.168.1.193.sip > joshsphone.com.sip: SIP, length: 322
        SIP/2.0 200 OK
        To: <sip:701@192.168.1.193:5060>;tag\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\032\373\011p\030\373\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\030\373\011\310m\377\011files\000\000\000\000\000\000\000\021\000\000\000\350\034\373\011\270\034\373\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030n\377\011\360m\377\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  546f 3a20 3c73 6970 3a37 3031 4031 3932
        0x0020:  2e31 3638 2e31 2e31 3933 3a35 3036 303e
        0x0030:  3b74 6167
14:08:39.754583 IP (tos 0xb8, ttl  63, id 35454, offset 0, flags [none], proto: UDP (17), length: 504) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 476
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\032\373\011p\030\373\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\030\373\011\310m\377\011files\000\000\000\000\000\000\000\021\000\000\000\350\034\373\011\270\034\373\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030n\377\011\360m\377\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
14:08:39.754797 IP (tos 0x60, ttl  64, id 33880, offset 0, flags [none], proto: UDP (17), length: 507) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 479
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\032\373\011p\030\373\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\030\373\011\310m\377\011files\000\000\000\000\000\000\000\021\000\000\000\350\034\373\011\270\034\373\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030n\377\011\360m\377\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450

```

192.168.1.191 is the host machine.

Btw sorry it took so long to get back, the forum didn't notify me of new replies.

---

### Post by jonobr on 2011-10-07
mmmmmm   (sits back in office chair and and rubs chin in a professorial way)

Your getting a 501
As per the RFC 

> 

21.5.2 501 Not Implemented

   The server does not support the functionality required to fulfill the
   request.  This is the appropriate response when a UAS does not
   recognize the request method and is not capable of supporting it for
   any user.  (Proxies forward all requests regardless of method.)

   Note that a 405 (Method Not Allowed) is sent when the server
   recognizes the request method, but that method is not allowed or
   supported.


A method is one of the following (in yours its the invite)
INVITE = Establishes a session
ACK = Confirms an INVITE request
BYE = Ends a session
CANCEL = Cancels establishing of a session
REGISTER = Communicates user location (host name, IP)
OPTIONS


Are you sure the sip server is setup ok to recognise the number your calling? (715)

---

### Post by collisionystm on 2011-10-07
It sounds like a routing problem to me. The phone is not being blocked.
Sorry Its been a while Since I have done this. I used to work on Mitel's.
SIP opens random ports to initiate its phone call. 5060 and 5061 are just the udp ports for voice traffic. A send port and Receive port. Although, you really need more ports than that.
The phone connects through your computer, and then to? An air card? Wireless to your router?

Your computer is not routing the traffic back to the phone properly. That doesnt mean its blocking, it just does not know what to do. What instructions did you use to setup your connection sharing?

I did this a long time ago with firestarter and ubuntu 9.10, Verizon Air Card, and a Mitel Phone. Neat stuff.

---

### Post by oneadvent on 2011-10-07
@jonobr
Yes I am sure, plugged into the switch or the router and it works fine, and the internet works on the phone. So I'm sure that the phone itself is setup right AND that it's authentication is okay. I also allow remote extensions, for instance my cell phone. That means that I am not blocking IP addresses.

@collisionystm
I just used Kubuntu's built in sharing connection. The connection from the phone is wired to the computer, then the computer has one of those cheap Belkin wireless usb things to connect wirelessly with the router. That router also has a switch plugged into it that has the PBX on it. This setup worked with Windows when I was doing a similar things so I know physically it is fine. I do think that is correct. I think it does not know how to route the service. Just not sure how to tell it.

---

### Post by jonobr on 2011-10-07
> 5060 and 5061 are just the udp ports for voice traffic.

Just to clarify, Port 5060 is used for call signalling between the UAS and the UAC.
Thats what is showing the call setup/teardown messages and in this case the 501 method not allowed message.

The signalling sets up the voice ports using RTP which can be any udp port north of some number I cant remember,
While its possible that the voice ports are blocked, that could be the case, however, this would result in the called phone ringing and having no audio in one or both directions

The original messages seem to indicate registrations issues,

whjat needs to happen now is, the phone needs to be switched off , run the trace, and then power on the phone.

It would be good to see a registration attempt from your phone and how the SIP server responds.
If you register you chould be ok to make the call.
If you dont register you will never make the call.


either way, you need a trace from initial startup of the phone.

---

### Post by oneadvent on 2011-10-07
@jonobr
Can you tell me how to do it? I would be more than happy to try anything!

---

### Post by jonobr on 2011-10-07
power off the phone, wait for a minute or so,  run your trace on either the server or wherever you ran the previous tcpdump trace before, power on the phone, 
ensure you see at least two packets.
There should be a messsage in that called register.

Do you have a model number of the phone BTW?

---

### Post by collisionystm on 2011-10-07
5060... call control. Thats right lol. Like I said. Its been a while. That's pretty neat Kubuntu has a built in feature for sharing a connection. I never knew that.

Wireshark your network and see if you see requests on port 5060 or 5061. That might help?

---

### Post by jonobr on 2011-10-07
without control... we are nothing.... its just chaos.....

---

### Post by oneadvent on 2011-10-07
OK, I'm doing this remotely right now. Earlier when I sent those two things I got back that was done with registering the phone at that point.

Otherwise I'll have to do it when I get home, fills up putty too quick...maybe I can do a grep for register on that command?

---

### Post by collisionystm on 2011-10-07
> **oneadvent said:**
> OK, I'm doing this remotely right now. Earlier when I sent those two things I got back that was done with registering the phone at that point.

Otherwise I'll have to do it when I get home, fills up putty too quick...maybe I can do a grep for register on that command?

You can change putty to an infinite amount of scroll back lines

---

### Post by oneadvent on 2011-10-07
```
root@joshsphone:~ $ tcpdump -vvv -i any port 5060
tcpdump: WARNING: Promiscuous mode not supported on the "any" device
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
16:00:22.489243 IP (tos 0xb8, ttl  61, id 57358, offset 0, flags [none], proto: UDP (17), length: 539) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 511
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:716@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3640
16:00:22.489819 IP (tos 0x60, ttl  64, id 27592, offset 0, flags [none], proto: UDP (17), length: 537) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 509
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:00:28.296419 IP (tos 0x60, ttl  64, id 44466, offset 0, flags [none], proto: UDP (17), length: 551) joshsphone.com.sip > 192.168.1.193.sip: SIP, length: 523
        OPTIONS sip:718@192.168.1.193:5060 SIP/2.0
        Via: SIP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027\351\000\000\007
        0x0000:  4f50 5449 4f4e 5320 7369 703a 3731 3840
        0x0010:  3139 322e 3136 382e 312e 3139 333a 3530
        0x0020:  3630 2053 4950 2f32 2e30 0d0a 5669 613a
        0x0030:  2053 4950
16:00:28.307004 IP (tos 0x68, ttl 250, id 6867, offset 0, flags [none], proto: UDP (17), length: 445) 192.168.1.193.sip > joshsphone.com.sip: SIP, length: 417
        SIP/2.0 200 OK
        To: <sip:718@192.168.1.193:5060>;tag\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  546f 3a20 3c73 6970 3a37 3138 4031 3932
        0x0020:  2e31 3638 2e31 2e31 3933 3a35 3036 303e
        0x0030:  3b74 6167
16:00:34.089569 IP (tos 0x60, ttl  64, id 27593, offset 0, flags [none], proto: UDP (17), length: 547) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 519
        OPTIONS sip:716@192.168.1.100:5060 SIP/2.0
        Via: SIP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027
        0x0000:  4f50 5449 4f4e 5320 7369 703a 3731 3640
        0x0010:  3139 322e 3136 382e 312e 3130 303a 3530
        0x0020:  3630 2053 4950 2f32 2e30 0d0a 5669 613a
        0x0030:  2053 4950
16:00:34.120275 IP (tos 0xb8, ttl  61, id 57359, offset 0, flags [none], proto: UDP (17), length: 1161) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 1133
        SIP/2.0 200 OK
        From: "Unknown"<sip:Unknown@192.168.\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027\351\000\000\007\352\360\342\366\352\000\342\346\353\360\304\326\354\000\304\306\355p\341\277\356\200\340\257\357p\303\237\360\200\302\217\361p\245\177\362\200\244o\363p\207_\364\200\206O\365pi?\366\200h/\367\360\205(\370\200J\017\371\360g\010\372\000g\370\372\360I\350\373\000I\330\374\360+\310\375\000+\270\376\360\015\250\377\000\015\230\000\360\357\207\001\000\357w\002p\014q\003\200\013a\004p\356P\005\200\355@\006p\3200\007\200'\215\007p\262\020\011\000\243\255\011p\224\360\012\200\223\340\013\360\260\331\014\200u\300\015\360\222\271\016\000\222\251\017\360t\231\020\000t\211\021\360Vy\022\000Vi\023\3608Y\024\0008I\025\360\0329\026\000\032)\027p7"\030\000\374\010\031p\031\002\032\200\030\362\032p\373\341\033\200\372\321\034p\335\301\035\200\334\261\036p\277\241\037\000\017v p\241\201!\000\361U"\360\275j#\000\3235$\360\237J%\000\265\025&\360\201*'\200\321\376'\360c\012)\200\263\336)\360E\352*\200\225\276+pb\323,\200w\236-pD\263.\200Y~/p&\2230\000vg1p\010s2\000XG3p\352R4\000:'5p\31426\000\034\0077\360\350\0338\000\376\3468\360\312\3739\000\340\306:\360\254\333;\200\374\257<\360\216\273=\200\336\217>\360p\233?\200\300o@p\215\204A\200\242OBpodC\200\204/DpQDE\000\267\363E\360m-G\000\231\323G\360O\015I\000{\263I\3601\355J\200\227\234KpN\326L\200y|Mp0\266N\200[\Op\022\226P\200=<Qp\364uR\200\037\034Sp\326UT\200\001\374Tp\2705V\000\036\345V\360\324\036X\000\000\305X\360\266\376Y\000\342\244Z\360\230\336[\000\304\204\\360z\276]\000\246d^\360\\236_\200\302M`py\207a\200\244-bp[gc\200\206\015dp=Ge\200h\355ep\037'g\200J\315gp\001\007i\200,\255ip\343\346j\000I\226k\360\377\317l\000+vm\360\341\257n\000\015Vo\360\303\217p\000\3575q\360\245or\000\321\025s\360\207Ot\200\355\376tp\2448v\200\317\336vp\206\030x\200\261\276xp
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  4672 6f6d 3a20 2255 6e6b 6e6f 776e 223c
        0x0020:  7369 703a 556e 6b6e 6f77 6e40 3139 322e
        0x0030:  3136 382e
16:00:35.521734 IP (tos 0xb8, ttl  63, id 37035, offset 0, flags [none], proto: UDP (17), length: 518) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 490
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:00:35.521972 IP (tos 0x60, ttl  64, id 34676, offset 0, flags [none], proto: UDP (17), length: 521) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 493
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:00:43.701432 IP (tos 0xb8, ttl  61, id 57360, offset 0, flags [none], proto: UDP (17), length: 538) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 510
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:716@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\036
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3640
16:00:43.701607 IP (tos 0x60, ttl  64, id 27594, offset 0, flags [none], proto: UDP (17), length: 536) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 508
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:00:52.216535 IP (tos 0xb8, ttl  63, id 37038, offset 0, flags [none], proto: UDP (17), length: 516) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 488
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:00:52.218024 IP (tos 0x60, ttl  64, id 34677, offset 0, flags [none], proto: UDP (17), length: 519) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 491
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:00:59.606742 IP (tos 0x60, ttl  64, id 44467, offset 0, flags [none], proto: UDP (17), length: 551) joshsphone.com.sip > 192.168.1.193.sip: SIP, length: 523
        OPTIONS sip:701@192.168.1.193:5060 SIP/2.0
        Via: SIP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027\351\000\000\007
        0x0000:  4f50 5449 4f4e 5320 7369 703a 3730 3140
        0x0010:  3139 322e 3136 382e 312e 3139 333a 3530
        0x0020:  3630 2053 4950 2f32 2e30 0d0a 5669 613a
        0x0030:  2053 4950
16:00:59.616549 IP (tos 0x68, ttl 250, id 6868, offset 0, flags [none], proto: UDP (17), length: 445) 192.168.1.193.sip > joshsphone.com.sip: SIP, length: 417
        SIP/2.0 200 OK
        To: <sip:701@192.168.1.193:5060>;tag\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  546f 3a20 3c73 6970 3a37 3031 4031 3932
        0x0020:  2e31 3638 2e31 2e31 3933 3a35 3036 303e
        0x0030:  3b74 6167
16:01:04.491800 IP (tos 0xb8, ttl  61, id 57361, offset 0, flags [none], proto: UDP (17), length: 539) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 511
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:716@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3640
16:01:04.492056 IP (tos 0x60, ttl  64, id 27595, offset 0, flags [none], proto: UDP (17), length: 537) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 509
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:01:09.524292 IP (tos 0xb8, ttl  63, id 37043, offset 0, flags [none], proto: UDP (17), length: 518) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 490
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:01:09.524486 IP (tos 0x60, ttl  64, id 34678, offset 0, flags [none], proto: UDP (17), length: 521) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 493
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:01:12.544068 IP (tos 0xb8, ttl  63, id 37045, offset 0, flags [none], proto: UDP (17), length: 518) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 490
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:01:12.544296 IP (tos 0x60, ttl  64, id 34679, offset 0, flags [none], proto: UDP (17), length: 521) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 493
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:01:20.928716 IP (tos 0x60, ttl  64, id 30948, offset 0, flags [none], proto: UDP (17), length: 622) joshsphone.com.sip > sipgate.com.sip: SIP, length: 594
        REGISTER sip:sipgate.com SIP/2.0
        Via: SIP/2.0/UDP 6\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027\351\000\000\007\352\360\342\366\352\000\342\346\353\360\304\326\354\000\304\306\355p\341\277\356\200\340\257\357p\303\237\360\200\302\217\361p\245\177\362\200\244o\363p\207_\364\200\206O\365pi?\366\200h/\367\360\205(\370\200J\017\371\360g\010\372\000g
        0x0000:  5245 4749 5354 4552 2073 6970 3a73 6970
        0x0010:  6761 7465 2e63 6f6d 2053 4950 2f32 2e30
        0x0020:  0d0a 5669 613a 2053 4950 2f32 2e30 2f55
        0x0030:  4450 2036
16:01:21.004161 IP (tos 0x0, ttl  51, id 9168, offset 0, flags [none], proto: UDP (17), length: 393) sipgate.com.sip > joshsphone.com.sip: SIP, length: 365
        SIP/2.0 200 OK
        Via: SIP/2.0/UDP 192.168.1.194:5060;\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  5669 613a 2053 4950 2f32 2e30 2f55 4450
        0x0020:  2031 3932 2e31 3638 2e31 2e31 3934 3a35
        0x0030:  3036 303b
16:01:23.106235 IP (tos 0xb8, ttl  63, id 37046, offset 0, flags [none], proto: UDP (17), length: 497) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 469
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:01:23.106448 IP (tos 0x60, ttl  64, id 34680, offset 0, flags [none], proto: UDP (17), length: 500) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 472
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:01:25.691938 IP (tos 0xb8, ttl  61, id 57362, offset 0, flags [none], proto: UDP (17), length: 539) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 511
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:716@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3640
16:01:25.692192 IP (tos 0x60, ttl  64, id 27596, offset 0, flags [none], proto: UDP (17), length: 537) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 509
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:01:26.635960 IP (tos 0xb8, ttl  63, id 37049, offset 0, flags [none], proto: UDP (17), length: 497) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 469
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:01:26.636165 IP (tos 0x60, ttl  64, id 34681, offset 0, flags [none], proto: UDP (17), length: 500) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 472
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:01:28.306896 IP (tos 0x60, ttl  64, id 44468, offset 0, flags [none], proto: UDP (17), length: 551) joshsphone.com.sip > 192.168.1.193.sip: SIP, length: 523
        OPTIONS sip:718@192.168.1.193:5060 SIP/2.0
        Via: SIP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027\351\000\000\007
        0x0000:  4f50 5449 4f4e 5320 7369 703a 3731 3840
        0x0010:  3139 322e 3136 382e 312e 3139 333a 3530
        0x0020:  3630 2053 4950 2f32 2e30 0d0a 5669 613a
        0x0030:  2053 4950
16:01:28.316599 IP (tos 0x68, ttl 250, id 6869, offset 0, flags [none], proto: UDP (17), length: 445) 192.168.1.193.sip > joshsphone.com.sip: SIP, length: 417
        SIP/2.0 200 OK
        To: <sip:718@192.168.1.193:5060>;tag\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  546f 3a20 3c73 6970 3a37 3138 4031 3932
        0x0020:  2e31 3638 2e31 2e31 3933 3a35 3036 303e
        0x0030:  3b74 6167
16:01:34.120383 IP (tos 0x60, ttl  64, id 27597, offset 0, flags [none], proto: UDP (17), length: 547) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 519
        OPTIONS sip:716@192.168.1.100:5060 SIP/2.0
        Via: SIP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027
        0x0000:  4f50 5449 4f4e 5320 7369 703a 3731 3640
        0x0010:  3139 322e 3136 382e 312e 3130 303a 3530
        0x0020:  3630 2053 4950 2f32 2e30 0d0a 5669 613a
        0x0030:  2053 4950
16:01:34.148815 IP (tos 0xb8, ttl  61, id 57363, offset 0, flags [none], proto: UDP (17), length: 1161) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 1133
        SIP/2.0 200 OK
        From: "Unknown"<sip:Unknown@192.168.\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027\351\000\000\007\352\360\342\366\352\000\342\346\353\360\304\326\354\000\304\306\355p\341\277\356\200\340\257\357p\303\237\360\200\302\217\361p\245\177\362\200\244o\363p\207_\364\200\206O\365pi?\366\200h/\367\360\205(\370\200J\017\371\360g\010\372\000g\370\372\360I\350\373\000I\330\374\360+\310\375\000+\270\376\360\015\250\377\000\015\230\000\360\357\207\001\000\357w\002p\014q\003\200\013a\004p\356P\005\200\355@\006p\3200\007\200'\215\007p\262\020\011\000\243\255\011p\224\360\012\200\223\340\013\360\260\331\014\200u\300\015\360\222\271\016\000\222\251\017\360t\231\020\000t\211\021\360Vy\022\000Vi\023\3608Y\024\0008I\025\360\0329\026\000\032)\027p7"\030\000\374\010\031p\031\002\032\200\030\362\032p\373\341\033\200\372\321\034p\335\301\035\200\334\261\036p\277\241\037\000\017v p\241\201!\000\361U"\360\275j#\000\3235$\360\237J%\000\265\025&\360\201*'\200\321\376'\360c\012)\200\263\336)\360E\352*\200\225\276+pb\323,\200w\236-pD\263.\200Y~/p&\2230\000vg1p\010s2\000XG3p\352R4\000:'5p\31426\000\034\0077\360\350\0338\000\376\3468\360\312\3739\000\340\306:\360\254\333;\200\374\257<\360\216\273=\200\336\217>\360p\233?\200\300o@p\215\204A\200\242OBpodC\200\204/DpQDE\000\267\363E\360m-G\000\231\323G\360O\015I\000{\263I\3601\355J\200\227\234KpN\326L\200y|Mp0\266N\200[\Op\022\226P\200=<Qp\364uR\200\037\034Sp\326UT\200\001\374Tp\2705V\000\036\345V\360\324\036X\000\000\305X\360\266\376Y\000\342\244Z\360\230\336[\000\304\204\\360z\276]\000\246d^\360\\236_\200\302M`py\207a\200\244-bp[gc\200\206\015dp=Ge\200h\355ep\037'g\200J\315gp\001\007i\200,\255ip\343\346j\000I\226k\360\377\317l\000+vm\360\341\257n\000\015Vo\360\303\217p\000\3575q\360\245or\000\321\025s\360\207Ot\200\355\376tp\2448v\200\317\336vp\206\030x\200\261\276xp
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  4672 6f6d 3a20 2255 6e6b 6e6f 776e 223c
        0x0020:  7369 703a 556e 6b6e 6f77 6e40 3139 322e
        0x0030:  3136 382e
16:01:40.269932 IP (tos 0xb8, ttl  63, id 37050, offset 0, flags [none], proto: UDP (17), length: 504) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 476
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:01:40.270151 IP (tos 0x60, ttl  64, id 34682, offset 0, flags [none], proto: UDP (17), length: 507) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 479
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:01:46.496247 IP (tos 0xb8, ttl  61, id 57364, offset 0, flags [none], proto: UDP (17), length: 538) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 510
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:716@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\036
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3640
16:01:46.496531 IP (tos 0x60, ttl  64, id 27598, offset 0, flags [none], proto: UDP (17), length: 536) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 508
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:01:59.616711 IP (tos 0x60, ttl  64, id 44469, offset 0, flags [none], proto: UDP (17), length: 551) joshsphone.com.sip > 192.168.1.193.sip: SIP, length: 523
        OPTIONS sip:701@192.168.1.193:5060 SIP/2.0
        Via: SIP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027\351\000\000\007
        0x0000:  4f50 5449 4f4e 5320 7369 703a 3730 3140
        0x0010:  3139 322e 3136 382e 312e 3139 333a 3530
        0x0020:  3630 2053 4950 2f32 2e30 0d0a 5669 613a
        0x0030:  2053 4950
16:01:59.626545 IP (tos 0x68, ttl 250, id 6870, offset 0, flags [none], proto: UDP (17), length: 445) 192.168.1.193.sip > joshsphone.com.sip: SIP, length: 417
        SIP/2.0 200 OK
        To: <sip:701@192.168.1.193:5060>;tag\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  546f 3a20 3c73 6970 3a37 3031 4031 3932
        0x0020:  2e31 3638 2e31 2e31 3933 3a35 3036 303e
        0x0030:  3b74 6167
16:02:00.608458 IP (tos 0xb8, ttl  63, id 37057, offset 0, flags [none], proto: UDP (17), length: 504) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 476
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:02:00.608850 IP (tos 0x60, ttl  64, id 34683, offset 0, flags [none], proto: UDP (17), length: 507) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 479
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:02:07.697847 IP (tos 0xb8, ttl  61, id 57365, offset 0, flags [none], proto: UDP (17), length: 539) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 511
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:716@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3640
16:02:07.698079 IP (tos 0x60, ttl  64, id 27599, offset 0, flags [none], proto: UDP (17), length: 537) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 509
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:02:14.271450 IP (tos 0xb8, ttl  63, id 37058, offset 0, flags [none], proto: UDP (17), length: 504) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 476
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:02:14.271831 IP (tos 0x60, ttl  64, id 34684, offset 0, flags [none], proto: UDP (17), length: 507) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 479
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:02:15.789283 IP (tos 0xb8, ttl  63, id 37060, offset 0, flags [none], proto: UDP (17), length: 504) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 476
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:02:15.789808 IP (tos 0x60, ttl  64, id 34685, offset 0, flags [none], proto: UDP (17), length: 507) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 479
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:02:17.799154 IP (tos 0xb8, ttl  63, id 37061, offset 0, flags [none], proto: UDP (17), length: 504) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 476
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:02:17.799730 IP (tos 0x60, ttl  64, id 34686, offset 0, flags [none], proto: UDP (17), length: 507) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 479
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:02:28.316816 IP (tos 0x60, ttl  64, id 44470, offset 0, flags [none], proto: UDP (17), length: 551) joshsphone.com.sip > 192.168.1.193.sip: SIP, length: 523
        OPTIONS sip:718@192.168.1.193:5060 SIP/2.0
        Via: SIP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027\351\000\000\007
        0x0000:  4f50 5449 4f4e 5320 7369 703a 3731 3840
        0x0010:  3139 322e 3136 382e 312e 3139 333a 3530
        0x0020:  3630 2053 4950 2f32 2e30 0d0a 5669 613a
        0x0030:  2053 4950
16:02:28.327078 IP (tos 0x68, ttl 250, id 6871, offset 0, flags [none], proto: UDP (17), length: 445) 192.168.1.193.sip > joshsphone.com.sip: SIP, length: 417
        SIP/2.0 200 OK
        To: <sip:718@192.168.1.193:5060>;tag\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  546f 3a20 3c73 6970 3a37 3138 4031 3932
        0x0020:  2e31 3638 2e31 2e31 3933 3a35 3036 303e
        0x0030:  3b74 6167
16:02:28.499214 IP (tos 0xb8, ttl  61, id 57366, offset 0, flags [none], proto: UDP (17), length: 539) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 511
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:716@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3640
16:02:28.499762 IP (tos 0x60, ttl  64, id 27600, offset 0, flags [none], proto: UDP (17), length: 537) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 509
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:02:31.073188 IP (tos 0xb8, ttl  63, id 37062, offset 0, flags [none], proto: UDP (17), length: 504) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 476
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:02:31.073716 IP (tos 0x60, ttl  64, id 34687, offset 0, flags [none], proto: UDP (17), length: 507) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 479
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:02:31.580139 IP (tos 0xb8, ttl  63, id 37063, offset 0, flags [none], proto: UDP (17), length: 504) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 476
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:02:31.580649 IP (tos 0x60, ttl  64, id 34688, offset 0, flags [none], proto: UDP (17), length: 507) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 479
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:02:32.590434 IP (tos 0xb8, ttl  63, id 37064, offset 0, flags [none], proto: UDP (17), length: 504) 192.168.1.191.sip > joshsphone.com.sip: SIP, length: 476
        PING sip:192.168.1.194:5060 SIP/2.0
        From: <sip:715@\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336
        0x0000:  5049 4e47 2073 6970 3a31 3932 2e31 3638
        0x0010:  2e31 2e31 3934 3a35 3036 3020 5349 502f
        0x0020:  322e 300d 0a46 726f 6d3a 203c 7369 703a
        0x0030:  3731 3540
16:02:32.590627 IP (tos 0x60, ttl  64, id 34689, offset 0, flags [none], proto: UDP (17), length: 507) joshsphone.com.sip > 192.168.1.191.sip: SIP, length: 479
        SIP/2.0 501 Method Not Implemented
        Via: SIP/2.0/UDP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211
        0x0000:  5349 502f 322e 3020 3530 3120 4d65 7468
        0x0010:  6f64 204e 6f74 2049 6d70 6c65 6d65 6e74
        0x0020:  6564 0d0a 5669 613a 2053 4950 2f32 2e30
        0x0030:  2f55 4450
16:02:34.148615 IP (tos 0x60, ttl  64, id 27601, offset 0, flags [none], proto: UDP (17), length: 547) joshsphone.com.sip > ip68-225-64-193.pn.at.cox.net.sip: SIP, length: 519
        OPTIONS sip:716@192.168.1.100:5060 SIP/2.0
        Via: SIP\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027
        0x0000:  4f50 5449 4f4e 5320 7369 703a 3731 3640
        0x0010:  3139 322e 3136 382e 312e 3130 303a 3530
        0x0020:  3630 2053 4950 2f32 2e30 0d0a 5669 613a
        0x0030:  2053 4950
16:02:34.205129 IP (tos 0xb8, ttl  61, id 57367, offset 0, flags [none], proto: UDP (17), length: 1161) ip68-225-64-193.pn.at.cox.net.sip > joshsphone.com.sip: SIP, length: 1133
        SIP/2.0 200 OK
        From: "Unknown"<sip:Unknown@192.168.\000\000\000\000\021\000\000\000port 5060\000\000\000\021\000\000\0000\272\036\011p\270\036\0110\000\000\0001\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000p\270\036\011\310\015#\011files\000\000\000\000\000\000\000\021\000\000\000\350\274\036\011\270\274\036\011rpc\000\031\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000)\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\001\000\000\000\001\000\000\000\030\016#\011\360\015#\011dns\000\331\004\000\000\200,\246\236p\371\272\237\200\016\206\240p\333\232\241\000t\313\242\360\367\203\243\200\322E\244\360\331c\245\000\331S\246p\227\025\247\000\2733\250\360\263\376\250\000\235\023\252\360\225\336\252\000\177\363\253\360w\276\254\000a\323\255\360Y\236\256\000C\263\257\360;~\260\200_\234\261pXg\262\200A|\263p:G\264\200#\\265p\034'\266\200\005<\267p\376\006\270\200\347\033\271p\340\346\271\000\004\005\273p\302\306\273\000\346\344\274\360\336\257\275\000\310\304\276\360\300\217\277\000\326Z\300p<\260\301\000\214\204\302\360\204O\303\000nd\304\360f/\305\200\212M\306\360H\017\307\200l-\310pe\370\310\200N\015\312pG\330\312\200\376\210\313p\364#\322\360\011a\322\000\363u\323\360\353@\324\000\325U\325\360\315 \326\000\2675\327\360\257\000\330\000\231\025\331\360\221\340\331\200\265\376\332\360s\300\333\200\227\336\334p\220\251\335\200y\276\336pr\211\337\200[\236\340pTi\341\200=~\342p6I\343\200\037^\344\360<W\345\000<G\346\360\0367\347\000\036'\350\360\000\027\351\000\000\007\352\360\342\366\352\000\342\346\353\360\304\326\354\000\304\306\355p\341\277\356\200\340\257\357p\303\237\360\200\302\217\361p\245\177\362\200\244o\363p\207_\364\200\206O\365pi?\366\200h/\367\360\205(\370\200J\017\371\360g\010\372\000g\370\372\360I\350\373\000I\330\374\360+\310\375\000+\270\376\360\015\250\377\000\015\230\000\360\357\207\001\000\357w\002p\014q\003\200\013a\004p\356P\005\200\355@\006p\3200\007\200'\215\007p\262\020\011\000\243\255\011p\224\360\012\200\223\340\013\360\260\331\014\200u\300\015\360\222\271\016\000\222\251\017\360t\231\020\000t\211\021\360Vy\022\000Vi\023\3608Y\024\0008I\025\360\0329\026\000\032)\027p7"\030\000\374\010\031p\031\002\032\200\030\362\032p\373\341\033\200\372\321\034p\335\301\035\200\334\261\036p\277\241\037\000\017v p\241\201!\000\361U"\360\275j#\000\3235$\360\237J%\000\265\025&\360\201*'\200\321\376'\360c\012)\200\263\336)\360E\352*\200\225\276+pb\323,\200w\236-pD\263.\200Y~/p&\2230\000vg1p\010s2\000XG3p\352R4\000:'5p\31426\000\034\0077\360\350\0338\000\376\3468\360\312\3739\000\340\306:\360\254\333;\200\374\257<\360\216\273=\200\336\217>\360p\233?\200\300o@p\215\204A\200\242OBpodC\200\204/DpQDE\000\267\363E\360m-G\000\231\323G\360O\015I\000{\263I\3601\355J\200\227\234KpN\326L\200y|Mp0\266N\200[\Op\022\226P\200=<Qp\364uR\200\037\034Sp\326UT\200\001\374Tp\2705V\000\036\345V\360\324\036X\000\000\305X\360\266\376Y\000\342\244Z\360\230\336[\000\304\204\\360z\276]\000\246d^\360\\236_\200\302M`py\207a\200\244-bp[gc\200\206\015dp=Ge\200h\355ep\037'g\200J\315gp\001\007i\200,\255ip\343\346j\000I\226k\360\377\317l\000+vm\360\341\257n\000\015Vo\360\303\217p\000\3575q\360\245or\000\321\025s\360\207Ot\200\355\376tp\2448v\200\317\336vp\206\030x\200\261\276xp
        0x0000:  5349 502f 322e 3020 3230 3020 4f4b 0d0a
        0x0010:  4672 6f6d 3a20 2255 6e6b 6e6f 776e 223c
        0x0020:  7369 703a 556e 6b6e 6f77 6e40 3139 322e
        0x0030:  3136 382e

60 packets captured
67 packets received by filter
0 packets dropped by kernel

```

WHEW! Thats a lot. I figured out how to change it to 9999 lines.

Hope that has what you need.

---

### Post by oneadvent on 2011-10-07
Oh and to clear up the confusion, the wireless Ubuntu computer is 192.168.1.191 and the ip address assigned to the phone is 10.x.x.x (nothing else uses that ip range.) 192.168.1.194 is the PBX

There are other phones on my system, hence the others.

---

### Post by jonobr on 2011-10-07
doing a tcp dump with port 5060 should not take up that much unless theres a lot going on on that port.
It would be nice to see the original registration and 200ok...

You could reduce the verbosity with one -v switch instead of 3. (-vvv)

Or you could try dumping to a file again. (-w trace.pcap)

Im scared of the latter as the wqebsite you posted on installed a program called ilivid and a search toolbar called searchqu which was a pest to get rid of
Mind you, that was my own fault as it said something like this


trace.pcap

[CENTER]**[SIZE="4"]DOWNLOAD HERE!!!![/SIZE]**
[SIZE="1"]to download ilivid[/SIZE]


















click here to download trace.pcap[/CENTER]


Just fyi if you use that site often

---

### Post by oneadvent on 2011-10-07
@jonobr
I'm sorry but I have no idea what you are talking about at this point. The whole thing is what I posted, from when I clicked (or had someone else click) the register button to when it said failed. I only said changing it to 9999 to say I didn't run out of room this time, so it's the whole trace.

Thanks!

---

### Post by jonobr on 2011-10-07
The last trace you gave was good but I only see one successful registration from sipgate .com wshich gets a 200ok, there rest are all method not support messages,
The hex is also truncated beyond a certain point where I cant see the codec your using,

Can you try and get the same kind of trace, but go for the -w switch gain and send the resulting file

tcpdump -w trace.pcap -i any -s 1600 

Leave it run for a short while, maybe restart the phone if you can

---

### Post by oneadvent on 2011-10-07
ready for incoming?

```
134040 packets captured
135521 packets received by filter
49 packets dropped by kernel

```

left it on for a while....

---

### Post by jonobr on 2011-10-07
sweet, if you gzip it , it should compress nicely


or if you can send as is that would be ok to.
Ill have a look and see whats what

Could you tell me the phone model

---

### Post by oneadvent on 2011-10-07
Okay, tell me when you get it, so I can kill the link off:
[http://www.2shared.com/file/_srhiT7r/trace.html](http://www.2shared.com/file/_srhiT7r/trace.html)

I have the Nortel 1535 (it is a cheap video phone.)

The file isn't zipped....sorry, 85megs

---

### Post by jonobr on 2011-10-07
That really shows a lot , Thanks for sending.

this is doing something very weird,
Heres what I see

.194 seems to be your sip proxy (freepbx).

It sends an occasional message out to clients asking what the endpoints are capable of this is the 'options' messages - arrowed in the trace....

Your clients give a 200ok with capabilities 
There seems to be a Linksys in there as well as a outside address of 68.225.x.x (a Nortel 1535)

There is also a registration from sipgate.com which works fine, im guessing this is your external voip carrier. This is all good


The one thing that seems kind of odd is this constant message from IP address 191 ( is this the ip address of the device causing issues?)

This is also a nortel 1535 , im guessing your freepbx software doesnt support this message, see attached graphic circles

The method sent is ping ....
Ive worked with sip a lot and never seen this method before , it may be specifc to nortel and their specifc pbx setup.

I figure freepbx doesnt know this method and doesnt know what to do, see the returned message each time.
it shows the same.


Im going to research this method and phone a bit more...



Lastly, you may look at the pbx and see if there is an option to allow anonymous call in , may be good to toggle that to see if that helps anything as I say a few anonymous@ip come in on the trace

---

### Post by oneadvent on 2011-10-07
> **jonobr said:**
> That really shows a lot , Thanks for sending.

this is doing something very weird,
Heres what I see

.194 seems to be your sip proxy (freepbx).

This is correct. I am using freepbx on asterisk. Nerd Vittles Incredible PBX, actually it is 1.4. Had it for a while.
> **jonobr said:**
> 
It sends an occasional message out to clients asking what the endpoints are capable of this is the 'options' messages - arrowed in the trace....

Your clients give a 200ok with capabilities 
There seems to be a Linksys in there as well as a outside address of 68.225.x.x (a Nortel 1535)

This is a correct thing. That is one of my friends, who has a phone that pulls off my system. I had forgotten about that.
> **jonobr said:**
> 
There is also a registration from sipgate.com which works fine, im guessing this is your external voip carrier. This is all good


The one thing that seems kind of odd is this constant message from IP address 191 ( is this the ip address of the device causing issues?)

This is the machine that should be giving the nortel internet (which it is) and allowing it to be a phone.
> **jonobr said:**
> 
This is also a nortel 1535 , im guessing your freepbx software doesnt support this message, see attached graphic circles

The method sent is ping ....
Ive worked with sip a lot and never seen this method before , it may be specifc to nortel and their specifc pbx setup.

I figure freepbx doesnt know this method and doesnt know what to do, see the returned message each time.
it shows the same.

Remember this phone DID work before, and does plugged straight in, without changes. 

It appears that the machine does not allow pings response. I am going to figure out why that is and make it work. Maybe I should turn off the firewall and see what happens: 

```
root@DD-WRT:~# ping 192.168.1.194
PING 192.168.1.194 (192.168.1.194): 56 data bytes
^C
--- 192.168.1.194 ping statistics ---
49 packets transmitted, 0 packets received, 100% packet loss

```

> **jonobr said:**
> 
Im going to research this method and phone a bit more...



Lastly, you may look at the pbx and see if there is an option to allow anonymous call in , may be good to toggle that to see if that helps anything as I say a few anonymous@ip come in on the trace

I can turn on anonymous calls. I remember that being a horrible thing to have on for long, but I can try it if you think it might help.

Thanks for looking so hard!

---

### Post by jonobr on 2011-10-07
Hey

Just did a bit of light reading [Here]("http://www.packetizer.com/in/q122.html")

Its a boring day when you dont learn something knew.

To me register method seems to be the best way to know if something is alive or not.

This is new to me using ping.

Remember though this is not regular ping , but a ping built within a SIP message, I figure its pinging the sip server not only ensuring the server is alive but also the sip application.
I.e. you can ping the box but pbx is not running not running on the box.

Given, as you mention, this worked and nothing changed on the pbx, I can only guess something happened on the phone that defaulted or changed in some way.
Can you look at the phone options and disable this, as I am thinking the phone figure the asterisk box is dead

---

### Post by oneadvent on 2011-10-07
Well it will respond to pings with iptables off so I'm going to see if it registers then.

---

### Post by oneadvent on 2011-10-07
It is still not registering, even with the ability to accept pings on. And it still gives that 501 error.

---

### Post by jonobr on 2011-10-07
hello

Just again to clarify , that it appears that the options ping, within the sip message is to check that the Piaf box is alive.

If you just do a regular ping Im sure it will work,
thats just using regular ICMP and sending a packet to ensure the host is alive and on the network.
The pin option within sip seems to be specifc that checks that the SIP application is alive,

The method not supported seems to cause an issue for that phone.

Is there a way that this option can be disabled on the 1535? To not use the SIP options PING method.
Again, this is all guessing as I have never come up against this method before.

---

### Post by oneadvent on 2011-10-09
I cannot find an option to turn that off, however, how would that work if it works plugged in? Wouldn't the same protocol have to be accepted then??

---

### Post by jonobr on 2011-10-10
Can you get a similar trace when its plugged directly into the router?

May the method not allowed message is a red herring and it still accpets registration with that method unsupported.

If all this works fine when your in the router,

Im again leaning back towards this being a nat issue
where your sharing is doing a nat.

If I recall we, discounted this as it was working belfore?
Is that correct?

Is there any chance the setting of the user has changed on the PBX
If memory serves, PIAF has a setting to set the user to a natted device...
I have not had to play with that before, but if you have a look at it maybe toggling nat may show something

---

### Post by oneadvent on 2011-10-10
I'll plug it straight in again tonight and re run that test. 

The only person that has access to the pbx is me, so no changes that I know of. 

The way this worked before was with Windows 7, same way to be plugged in.

---

### Post by oneadvent on 2011-10-16
Hi!

I haven't plugged straight in yet, I figured since Kubuntu 11.10 was coming soon, I should be able to try it then.

So I reformated, got internet to the phone again and still the same problem, but here is something interesting:

I plugged in my laptop, I needed to copy some files over from it. When I did that I tried to ssh to it and when I did it would say I was, but instead it would ssh to the main machine. It's like it loops.

---

