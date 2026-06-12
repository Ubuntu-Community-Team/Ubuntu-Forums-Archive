---
title: "dig &amp; ping returning different results.  suggestions please"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by okpgreg on 2009-03-10
We have a nameserver running on an amazon instance.  We moved it over from an old ip a couple of weeks ago and updated all our dns records.  

Currently, our dns provider shows the proper records for our server, and if we dig the server at our dns provider we get the results.  However, if we ping the server, or dig it and don't specify our server we get the old ip address.  

An opendns cache check also sporadically returns the proper results but generally returns the old ip address.  Does anyone have *any suggestions* because this bewildering me.  

Thanks in advance.

Edit, I should add that we cannot access the nameserver by it's domain, only by ip.

---

### Post by jonobr on 2009-03-11
This is an interesting one,

Just curious if you mananged to resolve it?

Was wondering what you would see on a wireshark/tcpdump trace when you do the dig or ping.

If the query goes to the same destination and returns different results then Im thinking you need to talk with your providor dude, but am interested to see if you have had any luck getting to the bottom of this

---

### Post by okpgreg on 2009-03-12
> **jonobr said:**
> This is an interesting one,

Just curious if you mananged to resolve it?

Was wondering what you would see on a wireshark/tcpdump trace when you do the dig or ping.

If the query goes to the same destination and returns different results then Im thinking you need to talk with your providor dude, but am interested to see if you have had any luck getting to the bottom of this

I'm actually not very fluent in using either of those.  if you'd like to point me in the right direction w/ tcpdump i'd be glad to show you the results.  Still haven't gotten it resolved. :-/ I opened a support ticket at opendns as well but haven't heard anything from them.

edit:  would a command like tcpdump -nnvvXSs 0 -i eth0 udp  be effective?

---

### Post by jonobr on 2009-03-12
Hey

If you have tcpdump installed, you could do

```
tcpdump -w trace.pcap -s 1600 -i eth0 port 53
```

where 

tcpdump gets the thing running

-w creates the file trace.pcap which a program like wireshark can read
-s 1600 increases the default packet capture size from 64  to 1600 bytes
-i = interface to trace on in the example here its eth0
port 53 - this is the dns port. If you want to capture everything then you just remove this line.

WOuld recommend you download wireshark in synaptic for fiewving the captured file.
With wireshark you can also do the same as above, its more a graphical interface

---

### Post by jonobr on 2009-03-12
I would run two traces,

first one trace1
would be the first correct dns lookup
the second would be the incorrect.

It should show and error on their part and should be something you can send to them to say 

> GET YOUR ACT TOGETHER

---

### Post by okpgreg on 2009-03-12
Well, this is on Ubuntu server, with no desktop environment, so wireshark wouldn't work very well :):(:/
These are the results of dig ns1.medialantern.com @ns1.everydns.net:

```

root@domU-12-31-39-03-BD-D6 { ~ }$ tcpdump -s 1600 -i eth0 port 53
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 1600 bytes
13:50:13.712570 IP domU-12-31-39-03-BD-D6.compute-1.internal.32775 > ip-172-16-0-23.ec2.internal.domain: 1259+ A? ns1.everydns.net. (34)
13:50:13.712824 IP ip-172-16-0-23.ec2.internal.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32775: 1259 1/0/0 A ns1.tahoe.everydns.net (50)
13:50:13.713013 IP domU-12-31-39-03-BD-D6.compute-1.internal.32776 > ip-172-16-0-23.ec2.internal.domain: 54036+ PTR? 23.0.16.172.in-addr.arpa. (42)
13:50:13.713155 IP ip-172-16-0-23.ec2.internal.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32776: 54036 1/0/0 PTR ip-172-16-0-23.ec2.internal. (83)
13:50:13.713265 IP domU-12-31-39-03-BD-D6.compute-1.internal.32776 > ip-172-16-0-23.ec2.internal.domain: 63947+ PTR? 36.190.249.10.in-addr.arpa. (44)
13:50:13.713590 IP ip-172-16-0-23.ec2.internal.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32776: 63947 1/0/0 PTR domU-12-31-39-03-BD-D6.compute-1.internal. (99)
13:50:13.713716 IP domU-12-31-39-03-BD-D6.compute-1.internal.32776 > ip-172-16-0-23.ec2.internal.domain: 57986+ PTR? 56.56.76.208.in-addr.arpa. (43)
13:50:13.713941 IP ip-172-16-0-23.ec2.internal.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32776: 57986 1/0/0 PTR ns1.tahoe.everydns.net. (79)
13:50:13.714202 IP domU-12-31-39-03-BD-D6.compute-1.internal.32776 > ns1.tahoe.everydns.net.domain: 20695+ A? ns1.medialantern.com. (38)
13:50:13.794386 IP ns1.tahoe.everydns.net.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32776: 20695*- 1/4/4 A ec2-75-101-152-152.compute-1.amazonaws.com (202)
13:50:13.794559 IP domU-12-31-39-03-BD-D6.compute-1.internal.32777 > ip-172-16-0-23.ec2.internal.domain: 33229+ PTR? 152.152.101.75.in-addr.arpa. (45)
13:50:13.794681 IP ip-172-16-0-23.ec2.internal.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32777: 33229 1/0/0 PTR ec2-75-101-152-152.compute-1.amazonaws.com. (101)

12 packets captured
12 packets received by filter
0 packets dropped by kernel

```

and these are the results of dig ns1.medialantern.com:

```

root@domU-12-31-39-03-BD-D6 { ~ }$ tcpdump -s 1600 -i eth0 port 53
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 1600 bytes
13:50:28.047142 IP domU-12-31-39-03-BD-D6.compute-1.internal.32777 > ip-172-16-0-23.ec2.internal.domain: 64775+ A? ns1.medialantern.com. (38)
13:50:28.047479 IP ip-172-16-0-23.ec2.internal.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32777: 64775 1/0/0 A admin.medialantern.com (54)
13:50:28.047701 IP domU-12-31-39-03-BD-D6.compute-1.internal.32778 > ip-172-16-0-23.ec2.internal.domain: 8511+ PTR? 23.0.16.172.in-addr.arpa. (42)
13:50:28.047936 IP ip-172-16-0-23.ec2.internal.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32778: 8511 1/0/0 PTR ip-172-16-0-23.ec2.internal. (83)
13:50:28.048052 IP domU-12-31-39-03-BD-D6.compute-1.internal.32778 > ip-172-16-0-23.ec2.internal.domain: 51742+ PTR? 36.190.249.10.in-addr.arpa. (44)
13:50:28.048263 IP ip-172-16-0-23.ec2.internal.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32778: 51742 1/0/0 PTR domU-12-31-39-03-BD-D6.compute-1.internal. (99)
13:50:28.048399 IP domU-12-31-39-03-BD-D6.compute-1.internal.32778 > ip-172-16-0-23.ec2.internal.domain: 52983+ PTR? 15.186.111.65.in-addr.arpa. (44)
13:50:28.048592 IP ip-172-16-0-23.ec2.internal.domain > domU-12-31-39-03-BD-D6.compute-1.internal.32778: 52983 1/0/0 PTR admin.medialantern.com. (80)

8 packets captured
8 packets received by filter
0 packets dropped by kernel

```

admin.medialantern.com is where our ns1 used to be.

---

