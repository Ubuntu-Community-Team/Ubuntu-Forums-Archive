---
title: "Help with traceroute diagnosis"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by CompBio on 2009-11-14
I've been experiencing some sftp weirdness from my school, so I'm using the opportunity to learn a bit about diagnosing networking problems.

My sftp transfers from school start at ~500Kbps, not bad for my Comcast 1Mbps connection.  But within ~30 seconds the transfer gradually slows from 500Kbps to ~120Kbps and stays there for the remainder of the transfer.

I ran traceroute to see what's going on, and got the following output (names and numbers altered to protect the guilty):

traceroute to frodo.shire.edu (177.61.46.157), 30 hops max, 40 byte packets
 1  192.168.1.254 (192.168.1.254)  1.882 ms  1.890 ms  2.116 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  te-0-8-0-5-ar02.sincity.na.sincity.comcast.net (72.58.103.154)  11.301 ms  12.842 ms  11.953 ms
 7  * * *
 8  72.58.128.18 (72.58.128.18)  11.924 ms  20.581 ms  11.564 ms
 9  k1-dp-5-vl631.frgp.net (192.29.12.170)  12.047 ms  11.269 ms  11.974 ms
10  fhc-shire.frgp.net (192.29.12.227)  13.946 ms  13.107 ms  14.320 ms
11  177.61.2.10 (177.61.2.10)  14.944 ms  14.513 ms  14.049 ms
12  frodo.shire.edu (177.61.46.157)  62.484 ms  14.534 ms  18.948 ms

1 is my wireless router; 2 through 5 would be, what, my connection to Comcast?  The link between my router and the cable modem?

Any ideas about this or my sftp slowness would be much appreciated!

---

