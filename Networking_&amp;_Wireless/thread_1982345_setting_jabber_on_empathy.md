---
title: "setting jabber on empathy"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by dik angga on 2012-05-18
guy i have some problem here with empathy.
i'm a pidgin user and i use pidgin do chatting on YM, NiMBUZZ, Gtalk..
but i no longer using pidgin and wanna using empathy, empathy could transfer all my account on pidgin except nimbuzz (no XMPP on empathy but Jabber)

my question how to setting jabber to connect nimbuzz like on xmpp.?

this is my jabber setting:

```
login ID : my name@nimbuzz.com
password: *********

advanced:

encryption required (TLS/SSL) -> mark
ignore SSL sertificate error -> unmark
resource: openfire.nimbuzz.com
priority: 0

override server setting:

server: openfire.nimbuzz.com
port: 5222
use old SSL -> unmark 
```

that config is success in pidgin (xmpp) but empathy..??? 

anyone can solve it for me..?

---

### Post by royale1223 on 2013-04-14
Try with port 443

```
$ nmap -A openfire.nimbuzz.com


Starting Nmap 6.00 ( http://nmap.org ) at 2013-04-14 20:03 IST
Nmap scan report for openfire.nimbuzz.com (195.211.49.7)
Host is up (0.29s latency).
Not shown: 996 filtered ports
PORT     STATE SERVICE    VERSION
80/tcp   open  http       nginx
|_http-methods: No Allow or Public header in OPTIONS response (status code 405)
443/tcp  open  ssl/jabber ejabberd (Protocol 1.0)
|_sslv2: server still supports SSLv2
| xmpp-info: 
|   STARTTLS Failed
|   errors
|_    (timeout)
| ssl-cert: Subject: commonName=o.nimbuzz.com
| Not valid before: 2013-04-04 00:00:00
|_Not valid after:  2014-04-04 23:59:59
843/tcp  open  unknown
5222/tcp open  jabber     ejabberd (Protocol 1.0)
| xmpp-info: 
|   STARTTLS Failed
|   XMPP
|     Lang
|       en
|     Server name
|       nimbuzz.com
|     (no version)
|   errors
|     host-unknown
|_    (timeout)
Service Info: Host: nimbuzz.com


Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 49.90 seconds

```

---

