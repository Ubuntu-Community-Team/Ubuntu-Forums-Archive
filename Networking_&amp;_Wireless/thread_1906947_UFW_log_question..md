---
title: "UFW log question."
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by collisionystm on 2012-01-10
My UFW Log is flooded with attempts from this guy. From what I can tell, he is trying to use me to resolve DNS?
What do you guys think?

Jan 10 09:51:09 Easton kernel: [1516042.935836] [UFW BLOCK] IN=eth0 OUT= MAC=XXXXXXXXXXX SRC=216.144.228.153 DST=MYEXTERNALADDRESS LEN=66 TOS=0x00 PREC=0x00 TTL=119 ID=17598 PROTO=UDP SPT=53 DPT=53 LEN=46 


Pages and pages of this.

eth0 is my adapter facing the internet.

216.144.228.153 is apparently resolveclothing.com

---

### Post by collisionystm on 2012-01-10
hmm... could be a DDOS attack I guess.

---

### Post by CharlesA on 2012-01-10
Do you have a DNS server on the box in question? That's the only reason someone would be sending traffic on UDP port 53.

---

### Post by collisionystm on 2012-01-10
> **CharlesA said:**
> Block that ip address. Do you have a DNS server on the box in question?


Each server is running bind9 that has a forwarder to the main dns at the main site.

I blocked the address manually with 

```
ufw deny 216.144.228.153
```

However, since running that my ufw.log is not showing any output from blocks on that address?

UFW status output
Anywhere                   DENY        216.144.228.153


I have 6 Servers running as routers at 6 sites. They have a vpn tunnel between each. Each server is running UFW and is configured to only allow INPUT from the other servers. Otherwise all inbound from other servers is blocked. At least, if UFW is doing what it claims....

---

### Post by CharlesA on 2012-01-10
Huh. I've not used ufw, since I just use iptables, but run this to see if logging is still in effect:

```
sudo iptables -L
```

It should be, but can't hurt to check.

---

### Post by collisionystm on 2012-01-10
yes logging is on. Look at this sh*t

Jan 10 10:20:51 Easton kernel: [1517824.808318] **[UFW AUDIT] IN=eth0** OUT= MAC=00:1e:2a:47:87:2b:00:e0:97:6b:7a:25:08:00 SRC=216.144.228.153 **DST=MYIP** LEN=66 TOS=0x00 PREC=0x00 TTL=119 ID=3691 PROTO=UDP SPT=53 DPT=53 LEN=46 

Jan 10 10:20:51 Easton kernel: [1517824.808661] [UFW AUDIT] IN= **OUT=eth0** **SRC=MYIP** DST=216.144.228.153 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=7084 PROTO=UDP SPT=53 DPT=53 LEN=45


seriously, what the f*ck UFW

Listed in my iptables

:INPUT DROP [33:3072]
-A ufw-before-input -m state --state INVALID -j DROP 
-A ufw-not-local -j DROP 
-A ufw-skip-to-policy-input -j DROP 
-A ufw-user-input -s 216.144.228.153/32 -j DROP

---

### Post by collisionystm on 2012-01-10
from one Charles to another...

This is redonkulous. 

With logging like that, How will I ever even know if its being blocked properly.

---

### Post by CharlesA on 2012-01-10
Wth. Are there any logs for BIND that mention anything about zone transfers?

[http://www.zytrax.com/books/dns/ch7/xfer.html](http://www.zytrax.com/books/dns/ch7/xfer.html)

TBH, I would drop UFW and just use iptables itself (even tho ufw is just a frontend to iptables..)

The log did say it was blocked ([UFW BLOCK]), but the entry is a bit of a mess.

---

### Post by collisionystm on 2012-01-10
from what I can tell, the server in question is not transferring zones.

Ill have to fiddle with iptables... its been a while. Hope I dont lock myself out :p

---

### Post by CharlesA on 2012-01-10
Use iptables-apply when testing firewall rules.. I've locked myself out a few times when messing with firewall rules. :p

If you need a refresher, check out the page here:
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by jonobr on 2012-01-10
Hey guys

interesting thread.

Could I ask a silly question for my own education. (BTW I dont work for revolvclothing :-) )

216.144.228.153 / resolveclothing.com looks like a pretty ligit site. 
They seem to have valid security certificates. The registrant in whois appears to also be the owner,

I can find the registrant in Linkedin etc

I would be inclined to contact him and tell him to get his ship in order, and that his site appears to be doing DOS attacks.

Do you guys think its best to just firewall and ignore these?
If this was just light probes or ended up being a dodgy site In some weird country I would ignore, but given you appear to be getting undue attention, thats why I thought I would contact them. Again, just asking this question for my own education and looking for your advice / experience.


> 

.
Registration Service Provided By: 
Active-Domain LLC
Contact:  [http://www.active-domain.com](http://www.active-domain.com)


Domain Name: revolveclothing.com

Expiry Date: 20-Jan-2021


Name servers:
ns1.revolveclothing.com
ns2.revolveclothing.com
ns3.revolveclothing.com


Registrant Name: Michael Karanikolas

Registrant Company: Eminent, Inc.

Registrant Email Address: [email]mkaranikolas@eminentinc.com[/email]

Registrant Address: 7067 Falcon Drive
Registrant City: Buena Park
Registrant State/Region/Province: CA

Registrant Postal Code: 90620
Registrant 
Country: US
Registrant Tel No: 7147973565
Registrant 
Fax No: none

Admin Name: Michael Karanikolas
Admin 
Company: Eminent, Inc.

Admin Email Address: [email]mkaranikolas@eminentinc.com[/email]
Admin Address: 7067 Falcon Drive

Admin City: Buena Park
Admin State/Region/Province: CA

Admin Postal Code: 90620
Admin Country: US

Admin Tel No: 7147973565
Admin Fax No: none

Tech Name: Michael Karanikolas

Tech Company: Eminent, Inc.
Tech Email Address: [email]mkaranikolas@eminentinc.com[/email]

Tech Address: 7067 Falcon Drive

Tech City: Buena Park
Tech 
State/Region/Province: 

Tech Postal Code: 90620

Tech Country: US
Tech 
Tel No: 7147973565




PS- I would offer to drive to LA and punch him in the nose, but Im in work and its a long drive:-)

---

### Post by collisionystm on 2012-01-10
> **jonobr said:**
> Hey guys

interesting thread.

Could I ask a silly question for my own education. (BTW I dont work for revolvclothing :-) )

216.144.228.153 / resolveclothing.com looks like a pretty ligit site. 
They seem to have valid security certificates. The registrant in whois appears to also be the owner,

I can find the registrant in Linkedin etc

I would be inclined to contact him and tell him to get his ship in order, and that his site appears to be doing DOS attacks.

Do you guys think its best to just firewall and ignore these?
If this was just light probes or ended up being a dodgy site In some weird country I would ignore, but given you appear to be getting undue attention, thats why I thought I would contact them. Again, just asking this question for my own education and looking for your advice / experience.




PS- I would offer to drive to LA and punch him in the nose, but Im in work and its a long drive:-)

Not sure what my plan is yet... currently rebuilding my firewall. I have all of my tables in place, now I just need to get logging going... fun fun fun.

Once I get logging up, I will check the logs in the morning and see if this place is still hitting me. Then we will have a problem and a phone call. 
Im in maryland.. they are a bit of a drive for me haha

---

### Post by jonobr on 2012-01-10
Yep, and LA traffic is a b i atch

---

### Post by CharlesA on 2012-01-10
Well, without actually capturing and reading the traffic, it's hard to say if it's actually a DNS request or something else.

UDP 53 is usually the port reserved for dns lookups/traffic, but it is possible to send other types of traffic on that port but why would you want to unless it's for malicious reasons.

---

### Post by collisionystm on 2012-01-10
there are easily over 1000 entries in there from the past 24 hours.

All of them from 216.144.228.153

All from port 53 to port 53



This box just passes VPN traffic. 
The only computer that is accessing the BIND function on it is mine... and I assure you, I have not been to that clothing website lol.

---

### Post by CharlesA on 2012-01-10
> **collisionystm said:**
> there are easily over 1000 entries in there from the past 24 hours.

All of them from 216.144.228.153

All from port 53 to port 53



This box just passes VPN traffic. 
The only computer that is accessing the BIND function on it is mine... and I assure you, I have not been to that clothing website lol.

Yikes. I'd definitely get in contact of the person from that site and tell them to take a look at as why their server is sending DNS requests out. Could be that their config is wrong or that it was compromised.

---

### Post by collisionystm on 2012-01-10
oh and did I mention it suddenly vanished? .... strange.

---

### Post by collisionystm on 2012-01-10
well I was thinking that they may have configured something wrong. It was strictly DNS. It wasn't the usual SSH / VNC attempt

---

### Post by CharlesA on 2012-01-10
> **collisionystm said:**
> well I was thinking that they may have configured something wrong. It was strictly DNS. It wasn't the usual SSH / VNC attempt
That's what I am thinking too, especially since it just vanished.

---

### Post by collisionystm on 2012-01-11
nope... nothing today.

Everybody else but resolve clothing lol

---

### Post by collisionystm on 2012-01-27
Everyone really wants to hit up my port 53.


$ cat /var/log/ufw.log | grep -c  DPT=53
**22436**

Refined to make sure its counting the correct logs.

$ cat /var/log/ufw.log | grep BLOCK | grep -c  DPT=53
**22445**

---

### Post by CharlesA on 2012-01-27
Holy crap. Are the requests still coming from the same IP?

---

### Post by collisionystm on 2012-01-27
> **CharlesA said:**
> Holy crap. Are the requests still coming from the same IP?

NO! Its a mixture lol. Wtf!

I port scanned the server from my house and it showed no open ports...sooooo.......... what. the. eff.

---

### Post by CharlesA on 2012-01-27
Well DNS is UDP, so it might not show up on a portscan, but I no idea idea what is going on. In any case, it's firewalled, so the connections are blocked, but they shouldn't be trying to make the connection at all in the first place.

So strange.

---

### Post by collisionystm on 2012-01-27
> **CharlesA said:**
> Well DNS is UDP, so it might not show up on a portscan, but I no idea idea what is going on. In any case, it's firewalled, so the connections are blocked, but they shouldn't be trying to make the connection at all in the first place.

So strange.

Here are the most common in the past few hours


$ cat /var/log/ufw.log | grep -c 74.53.205.194
**64**
$ cat /var/log/ufw.log | grep -c 122.248.243.226
**933**
$ cat /var/log/ufw.log | grep -c 209.197.119.187
**156**
$ sudo cat /var/log/ufw.log | grep -c 79.142.66.252
**1466**

---

### Post by collisionystm on 2012-01-27
The most hilarious part about this...


$ cat /var/log/ufw.log | grep BLOCK | grep -c DPT=22
0

$ cat /var/log/ufw.log | grep BLOCK | grep -c DPT=21
0

$ cat /var/log/ufw.log | grep BLOCK | grep -c DPT=80
4

$ cat /var/log/ufw.log | grep BLOCK | grep -c DPT=443
0

$ cat /var/log/ufw.log | grep BLOCK | grep -c DPT=53
22572

---

### Post by CharlesA on 2012-01-27
Can try a whois on those IPs to see where they are, but I don't know why they are trying to connect in the first place. :(

EDIT: That's hilarious - no hits on 22, 21 or 443 and only a few on 80. WTF indeed.

---

### Post by collisionystm on 2012-01-27
> **CharlesA said:**
> Can try a whois on those IPs to see where they are, but I don't know why they are trying to connect in the first place. :(

EDIT: That's hilarious - no hits on 22, 21 or 443 and only a few on 80. WTF indeed.

The whois didnt take me to far. Not like it matters anyways. There is not much I can do lol.

Oh well... as long as the firewall keeps doing its job I am happy. :KS

---

### Post by CharlesA on 2012-01-27
Indeed. At least you are being diligent and checking logs. ;)

---

### Post by collisionystm on 2012-01-27
I wonder how I can manipulate the GREP command to show me the IP that appears most

---

### Post by collisionystm on 2012-01-27
Think I got it


 1 SRC=114.60.5.193
    972 SRC=122.248.243.226
   2329 SRC=128.241.50.90
      1 SRC=174.136.79.35
    341 SRC=174.143.228.218
    283 SRC=184.172.132.162
      3 SRC=184.22.133.55
   2199 SRC=184.82.245.61
      1 SRC=188.212.152.7
     15 SRC=188.94.240.72
    812 SRC=193.219.8.157
     64 SRC=194.28.157.8
    185 SRC=194.68.106.197
   1380 SRC=195.26.235.136
     10 SRC=208.111.182.222
    117 SRC=208.69.230.58
    183 SRC=208.69.230.59
    168 SRC=208.83.140.146
    195 SRC=209.197.119.187
      5 SRC=212.224.126.200
      1 SRC=212.96.161.252
      1 SRC=212.96.161.253
    223 SRC=213.175.216.3
    217 SRC=216.139.226.228
    167 SRC=216.139.226.46
      1 SRC=218.27.148.82
      1 SRC=218.28.125.173
      2 SRC=219.143.8.143
      2 SRC=219.148.202.197
    423 SRC=41.86.112.46
    846 SRC=46.236.11.4
    182 SRC=46.38.170.96
    327 SRC=50.23.38.43
      1 SRC=50.56.125.162
    793 SRC=50.56.218.82
      1 SRC=59.125.148.85
      1 SRC=60.190.222.143
      1 SRC=61.235.241.70
    971 SRC=64.27.63.142
   2004 SRC=66.208.86.34
    153 SRC=66.219.23.59
    231 SRC=66.219.23.60
      4 SRC=67.220.93.37
      1 SRC=67.23.23.56
    132 SRC=69.172.200.88
   1737 SRC=69.175.116.110
     34 SRC=72.52.232.116
      6 SRC=72.52.232.125
   1198 SRC=72.52.232.96
     78 SRC=74.53.205.194
    394 SRC=78.136.56.74
   1466 SRC=79.142.66.252
      1 SRC=86.105.68.177
    726 SRC=86.54.178.36
    847 SRC=90.155.4.69
    248 SRC=91.229.248.177
      1 SRC=93.184.211.30

---

### Post by CharlesA on 2012-01-27
Nice. What was the command you used to get that info?

---

### Post by collisionystm on 2012-01-27
sed 's/ /\n/g' /var/log/ufw.log | sort | uniq -c | grep SRC=


Just stuff I found online... Not sure where to include DPT=53 because of the way the output is. Running it without grep SRC= is a mess.

The output is pretty accurate for me though because I know 99% of my current logs are DNS related

---

### Post by CharlesA on 2012-01-27
Thanks. That's pretty handy.

---

### Post by Doug S on 2012-01-30
collisionystm, that command you posted is just the thing I have been wanting, Thanks.
I am posting back here two changes I made to it: I reversed the grep and the sort, to reduce the work the sort has to do; I did another sort and then only list the worst offenders:```
cat /var/log/messages.1 /var/log/messages | sed 's/ /\n/g' | grep "SRC=" | sort | uniq -c | sort -g | tail -25
```Example output (I don't use ufw, so am looking at another log file):```
     ... deleted some...
      18 SRC=74.125.225.127
     20 SRC=200.63.21.138
     20 SRC=65.52.103.78
     27 SRC=74.125.127.106
     28 SRC=173.194.33.58
     56 SRC=192.168.111.103
     58 SRC=192.168.111.109
     61 SRC=192.168.111.100
     91 SRC=8.25.128.188
   1264 SRC=174.103.192.101
   2724 SRC=192.168.111.106
   4579 SRC=222.92.89.14

```

---

### Post by collisionystm on 2012-01-30
> **Doug S said:**
> collisionystm, that command you posted is just the thing I have been wanting, Thanks.
I am posting back here two changes I made to it: I reversed the grep and the sort, to reduce the work the sort has to do; I did another sort and then only list the worst offenders:```
cat /var/log/messages.1 /var/log/messages | sed 's/ /\n/g' | grep "SRC=" | sort | uniq -c | sort -g | tail -25
```Example output (I don't use ufw, so am looking at another log file):```
     ... deleted some...
      18 SRC=74.125.225.127
     20 SRC=200.63.21.138
     20 SRC=65.52.103.78
     27 SRC=74.125.127.106
     28 SRC=173.194.33.58
     56 SRC=192.168.111.103
     58 SRC=192.168.111.109
     61 SRC=192.168.111.100
     91 SRC=8.25.128.188
   1264 SRC=174.103.192.101
   2724 SRC=192.168.111.106
   4579 SRC=222.92.89.14

```


Your Welcome :D

Glad my Google skills came in handy

---

