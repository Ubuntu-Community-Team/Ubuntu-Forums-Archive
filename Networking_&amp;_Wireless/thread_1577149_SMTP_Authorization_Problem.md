---
title: "SMTP Authorization Problem"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by cssutto on 2010-09-18
Ubuntu 10.4

Mutt

msmtp

Huawie EC168 air card purchased from Alltel, now serviced by Verizon

Air card in Cradlepoint MBR1000 router

Dynamic DNS

Mutt, msmtp, air card combination two years old.

System worked flawlessly until September 9th.  On that day, I began getting error messages when attempting to send email.

msmtp: recipient address [email]claudesutton@suttonmachine.com[/email] not accepted by the server
msmtp: server message: 554 Service unavailable; Client host [166.166.1.42] blocked using zen.spamhaus.org;
[http://www.spamhaus.org/query/bl?ip=166.166.1.42](http://www.spamhaus.org/query/bl?ip=166.166.1.42)
msmtp: could not send mail (account suttonmachine from /home/claude69694/.msmtprc)

The link advises that the above IP address is on the PBL list, which simply means that you must have smtp authorization.

So this is not a blacklisted address, just one that requires authorization.

My set up is auth on.

My email address is shown above and suttonmachine.com is my domain duly registered with Network Solutions and serviced by my ISP.

I have posted my problem with msmtp but that is apparently a low volume newslist and I have not heard from them.

Any suggestions would be appreciated.

Remember that I get all web sites and can do anything else I would like on the internet including sending emails through gmail.  I understand the difference, so don't waste time on that.

Help will be appreciated.

Verizon support is useless.  

Cradlepoint advised me to open all ports, 1-65535, which I did.

They also suggested that I activate DMZ, which I did.

To double check, I went to Shields Up and the report was that all ports are stealthed.

So I looked to see if firestarter is installed and it is.  I have never used it as I rely on the router firewall.

Anyway, I pulled it up to check it and it is disabled.

So one of my questions is whether 10.4 is shipped with all ports stealthed.

If not, how am I getting the report that I am stealthed when I opened all ports?

CSSJR

---

