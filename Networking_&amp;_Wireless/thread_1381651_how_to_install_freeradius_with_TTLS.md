---
title: "how to install freeradius with TTLS?"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by liaommx on 2010-01-15
my ubuntu is ubuntu 8.10,
because i need to maintain some program under 8.10,

my teacher asked me for setting freeradius with TTLS (or eap_TLS)
but i don't know how to install the other step.

i already make freeradius well with username / password
(which edit in /etc/freeradius/user )
but i want to combine it with eap_tls or TTLS.
i always defeat by it,

is there any one can help me to set it up?

--

the step i install freeradius , only 1 step.
```
sudo apt-get install freeradius
```
done...

and edit some config file,

like /etc/radiusd.conf
the default setting is for mysql manage name and pass.
i want to config it in file,
so i # all mysql text,

and edit the user name and pass in clients.conf and users
after it i start testing mode (or debug mode?)
with

```
freeradius -X
``` 

testing mode, now
but i still want to combine it with eap-tls and ttls,
who can give me the details of creating certification.
and what should i change in eap.conf?

thx

---

