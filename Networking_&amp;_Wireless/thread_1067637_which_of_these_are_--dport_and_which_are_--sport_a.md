---
title: "which of these are --dport and which are --sport? about ekiga."
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by q.dinar on 2009-02-12
hello. can you help me by explaining which of these are "--dport" and which are "--sport" : [http://wiki.ekiga.org/index.php/Internet_ports_used_by_Ekiga](http://wiki.ekiga.org/index.php/Internet_ports_used_by_Ekiga)  - there is a table with ports etc.

---

### Post by q.dinar on 2009-02-18
"bump". and: i had asked this also in [#ekiga](irc://irc.freenode.net/ekiga) and [#iptables](irc://irc.freenode.net/iptables) in irc.freenode.net.

---

### Post by superprash2003 on 2009-02-18
are you trying to open these ports or forwarding these ports to another pc?

---

### Post by q.dinar on 2009-02-19
i am going to open them. (for my computer itself, only.)

---

### Post by superprash2003 on 2009-02-19
then you needn't do anything , iptables would allow it !!

---

### Post by q.dinar on 2009-02-19
i have closed output and input packets except several types.

---

### Post by superprash2003 on 2009-02-20
use this command
  
 sudo iptables -I INPUT -p tcp --dport portno -j ACCEPT

where portno is the port no you want to forward

---

### Post by q.dinar on 2009-02-21
let i write them one by one, step by step.
```

Protocols   Ports 	   Types  Descriptions
SIP         5000 to 5100   UDP    SIP signalling, listen port: 5060

```
there is written "listen port: 5060" so it is for INPUT and it is destination port. but i cannot understand is "5000 to 5100" for INPUT or for OUTPUT and whether they are source ports or destination ports.
in the description below the table is written:
"The main port listening for incoming connections in Ekiga for SIP is port 5060 (UDP)"
so i consider now that that "5000 to 5100" are that "non-main" listening ports and i should also open them to listen. >below i think may be i should them as destination ports and for output<
then:
```

STUN        3478 to 3479   UDP    Outgoing traffic to the STUN server

```
so this is for OUTPUT . but i cannot understand is it destination port. i think now it is, because usually ports of the servers are concrete and outgoing ports are some random.
then
```

RTP         Random/Various UDP    Incoming traffic from the other end.
                                  Often 5004, 7070, 16382

```
as it is incoming, i think these "Often 5004, 7070, 16382" are destination ports.
i have read "The main port listening for incoming connections in Ekiga for SIP is port 5060 (UDP), while 1720 (TCP) is used by H.323" so i consider i can one of sip and H.323, not both of them work together. so as next 3 rows in the table are for "H.323" and i am going to try only sip first i can do not open ports for H.323.
then i have opened gconf-editor. there are: listen port = 5060 in sip subfolder and rtp_port_range=5000:5059 so i should open them instead of "Often 5004, 7070, 16382". and there are tcp_port_range and udp_port_range that are equal to ports in H.323 rows in that table. so if will not work without them i will try open them also.
only now i have seen that "Explanation of the port ranges" that in that wiki is about parameters in gconf-editor. it is not understandable by head sizes (h1, h2 tags of html). so there i see and also in description in gconf-editor that udp_port_range is used also for sip. they are 5060-5100 , so i should open only them instead of "5000-5100". they are "for SIP signalling" so i should open them as destination port (and for output)?
then i read about "tcp_port_range" that they are not used for sip. so now i think i need not to open them.

i have never opened port ranges so i need to read man iptables. now i have read that i should use  multiport module so "-m multiport --destination-ports 3478:3479" for example.

---

