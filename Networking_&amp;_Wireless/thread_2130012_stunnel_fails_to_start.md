---
title: "stunnel fails to start"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by blwegrzyn on 2013-03-28
I installed stunnel on ubuntu server 12.10
and in config i have:

cert = /etc/stunnel/mail.pem

[attsmtp]
client = yes
verify = 0
accept = 127.0.0.1:2525
connect = smtp.att.yahoo.com:465
delay = yes

 ls /etc/stunnel/
mail.pem  README  stunnel.conf

ubuntu@ip-10-253-53-184:/etc/stunnel$ sudo /etc/init.d/stunnel4 start
Starting SSL tunnels: Clients allowed=500
stunnel 4.53 on x86_64-pc-linux-gnu platform
Compiled with OpenSSL 1.0.1 14 Mar 2012
Running  with OpenSSL 1.0.1c 10 May 2012
Update OpenSSL shared libraries or rebuild stunnel
Threading:PTHREAD SSL:+ENGINE+OCSP Auth:LIBWRAP Sockets:POLL+IPv6
Reading configuration from file /etc/stunnel/stunnel.conf
Compression not enabled
Snagged 64 random bytes from /home/ubuntu/.rnd
Wrote 1024 new random bytes to /home/ubuntu/.rnd
PRNG seeded successfully
Line 11: "~               ": No '=' found
str_stats: 7 block(s), 1191 data byte(s), 406 control byte(s)
[Failed: /etc/stunnel/stunnel.conf]
You should check that you have specified the pid= in you configuration file
ubuntu@ip-10-253-53-184:/etc/stunnel$

---

### Post by blwegrzyn on 2013-03-28
> **blwegrzyn said:**
> I installed stunnel on ubuntu server 12.10
and in config i have:

cert = /etc/stunnel/mail.pem

[attsmtp]
client = yes
verify = 0
accept = 127.0.0.1:2525
connect = smtp.att.yahoo.com:465
delay = yes

 ls /etc/stunnel/
mail.pem  README  stunnel.conf

ubuntu@ip-10-253-53-184:/etc/stunnel$ sudo /etc/init.d/stunnel4 start
Starting SSL tunnels: Clients allowed=500
stunnel 4.53 on x86_64-pc-linux-gnu platform
Compiled with OpenSSL 1.0.1 14 Mar 2012
Running  with OpenSSL 1.0.1c 10 May 2012
Update OpenSSL shared libraries or rebuild stunnel
Threading:PTHREAD SSL:+ENGINE+OCSP Auth:LIBWRAP Sockets:POLL+IPv6
Reading configuration from file /etc/stunnel/stunnel.conf
Compression not enabled
Snagged 64 random bytes from /home/ubuntu/.rnd
Wrote 1024 new random bytes to /home/ubuntu/.rnd
PRNG seeded successfully
Line 11: "~               ": No '=' found
str_stats: 7 block(s), 1191 data byte(s), 406 control byte(s)
[Failed: /etc/stunnel/stunnel.conf]
You should check that you have specified the pid= in you configuration file
ubuntu@ip-10-253-53-184:/etc/stunnel$



i figured it out.
Enabled debug and turns out sendmail was listening on 2525 although it should not. (it should sent to 2525, not listen on)
Rebooting fixed the issue.

---

