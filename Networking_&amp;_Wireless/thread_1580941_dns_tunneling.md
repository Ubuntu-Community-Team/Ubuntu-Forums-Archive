---
title: "dns tunneling"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by sulcanto on 2010-09-24
Hello,  
 I tried to make a DNS tunnel with ozymanDNS on ubuntu machines but it hasn't worked. I have one machine with public IP address (14*.**.84.131) - called server and laptop connected with wireless called client. 
  I start the deamon 
```

./nomde.pl -i 0.0.0.0 tune9.*****.com

```on machine called server

and then start a ssh client on client machine
```

ssh -v -o ProxyCommand="./droute.pl tune9.****.com" sulcanto@localhost

```and then I recieved on client's console:
```

OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Executing proxy command: exec ./droute.pl tune*.****.com
debug1: permanently_drop_suid: 1000
debug1: identity file /home/sulcanto/.ssh/identity type -1
debug1: identity file /home/sulcanto/.ssh/id_rsa type -1
debug1: identity file /home/sulcanto/.ssh/id_dsa type -1
debug1: ssh_exchange_identification: \211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251\333\215t\343\236D\223\333Mt\036!k\211'\251
....
....
....
debug1: ssh_exchange_identification: \343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255D\223\333Mt\036!k\211'\251\333\215t\343\255w
ssh_exchange_identification: No banner received

```
and on the server console is following:
```

Maximum reply length as advertosed in EDNS from 147.32.80.9:56908: 4096
Writing response - done
Waiting for connections...
UDP connection from 147.32.80.9:58863 to 0.0.0.0
query 36071: (36-51987.id-3159.down.tune9.mooo.com, IN, TXT) - 
36-51987.id-3159.down.tune*.****.com.   0       IN      TXT     "Hi:  Fri Sep 24 10:39:50 CEST 2010"
NOERROR
;; id = 36071
;; qr = 1    opcode = QUERY    aa = 1    tc = 0    rd = 0
;; ra = 0    ad = 0    cd = 0    rcode  = NOERROR
;; qdcount = 1  ancount = 1  nscount = 0  arcount = 0

Maximum reply length as advertosed in EDNS from 147.32.80.9:58863: 4096
Writing response - done
Waiting for connections...
UDP connection from 147.32.80.9:57566 to 0.0.0.0
query 46635: (54-2270.id-3159.down.tune9.mooo.com, IN, TXT) - 
54-2270.id-3159.down.tune*.****.com.    0       IN      TXT     "Hi:  Fri Sep 24 10:39:50 CEST 2010"
NOERROR
;; id = 46635
;; qr = 1    opcode = QUERY    aa = 1    tc = 0    rd = 0
;; ra = 0    ad = 0    cd = 0    rcode  = NOERROR
;; qdcount = 1  ancount = 1  nscount = 0  arcount = 0
....
....
....
Maximum reply length as advertosed in EDNS from 147.32.80.9:59996: 4096
Writing response - done
Waiting for connections...
UDP connection from 147.32.80.9:62385 to 0.0.0.0
query 26010: (324-55712.id-25592.down.tune9.mooo.com, IN, TXT) - 
324-55712.id-25592.down.tune*.****.com.    0    IN    TXT    "Hi:  Fri Sep 24 10:49:04 CEST 2010"
NOERROR
;; id = 26010
;; qr = 1    opcode = QUERY    aa = 1    tc = 0    rd = 0
;; ra = 0    ad = 0    cd = 0    rcode  = NOERROR
;; qdcount = 1  ancount = 1  nscount = 0  arcount = 0

Maximum reply length as advertosed in EDNS from 147.32.80.9:62385: 4096
Writing response - done

```
do you have any idea how to fix it?

---

### Post by maswan on 2013-04-29
Having just struggled with this, you forgot "sshdns." in the start of the droute.pl argument, as in sshdns.tune*.****.com.

---

