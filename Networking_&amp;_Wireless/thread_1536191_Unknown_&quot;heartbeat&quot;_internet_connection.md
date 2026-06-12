---
title: "Unknown &quot;heartbeat&quot; internet connection"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by SoFl W on 2010-07-21
I am seeing an unknown internet connection both send and receive of about 5kbits that seems to happen every 15 seconds or so.  I noticed this the other day and rebooted.  It went away but I noticed it again.  Nothing shows in the System monitor under processes.

I can close all programs and it still seems to happen.  What is the best way to track down what is causing this connection, and how to tell what it is connecting to?

---

### Post by gombadi on 2010-07-21
Open a terminal window and type

```

sudo tcpdump -tnl -c 1000

```

This will show you all packets going to and from your machine including ip addresses and ports. From this you should be able to work out what is generating the traffic.

Post the output here is you want.

---

### Post by SoFl W on 2010-07-22
Thanks, I am looking at the TCPDUMP manual page now.  This seems to come and go.

```

IP 192.168.1.111.43578 > 209.18.47.61.53: 6979+ AAAA? www.findemailbyname.com. (41)
IP 209.18.47.61.53 > 192.168.1.111.40631: 53467 0/1/0 (108)
IP 192.168.1.111.60009 > 209.18.47.61.53: 4605+ A? www.searchpeoplebynumber.com. (46)
IP 209.18.47.61.53 > 192.168.1.111.43578: 6979 0/1/0 (103)
IP 192.168.1.111.34689 > 209.18.47.61.53: 20120+ AAAA? www.findemailbyname.com. (41)
IP 209.18.47.61.53 > 192.168.1.111.60009: 4605 1/0/0 (62)
IP 192.168.1.111.48575 > 209.18.47.61.53: 6491+ AAAA? www.verifyemailaddress.org. (44)
IP 209.18.47.61.53 > 192.168.1.111.41697: 14934 0/1/0 (113)
IP 192.168.1.111.51804 > 209.18.47.61.53: 37247+[|domain]
IP 209.18.47.61.53 > 192.168.1.111.51804: 37247 1/0/0 (67)
IP 192.168.1.111.41969 > 209.18.47.61.53: 17950+ AAAA? www.websitevaluespy.com. (41)
IP 209.18.47.61.53 > 192.168.1.111.34689: 20120 0/1/0 (103)
IP 192.168.1.111.53052 > 209.18.47.61.53: 49517+ A? www.findemailbyname.com. (41)
IP 209.18.47.61.53 > 192.168.1.111.41969: 17950 0/1/0 (103)
IP 192.168.1.111.57755 > 209.18.47.61.53: 40512+ AAAA? www.websitevaluespy.com. (41)
IP 209.18.47.61.53 > 192.168.1.111.48575: 6491 0/1/0 (106)
IP 192.168.1.111.48350 > 209.18.47.61.53: 50517+ AAAA? www.verifyemailaddress.org. (44)
IP 209.18.47.61.53 > 192.168.1.111.53052: 49517 1/0/0 (57)
IP 192.168.1.111.49337 > 209.18.47.61.53: 41657+ AAAA? www.routeripaddress.com. (41)
IP 209.18.47.61.53 > 192.168.1.111.48350: 50517 0/1/0 (106)
IP 192.168.1.111.37657 > 209.18.47.61.53: 42678+ A? www.verifyemailaddress.org. (44)
IP 209.18.47.61.53 > 192.168.1.111.49337: 41657 0/1/0 (103)
IP 192.168.1.111.39637 > 209.18.47.61.53: 7740+ AAAA? www.routeripaddress.com. (41)
IP 209.18.47.61.53 > 192.168.1.111.57755: 40512 0/1/0 (103)
IP 192.168.1.111.48262 > 209.18.47.61.53: 14650+ A? www.websitevaluespy.com. (41)
IP 209.18.47.61.53 > 192.168.1.111.39637: 7740 0/1/0 (103)
IP 192.168.1.111.59731 > 209.18.47.61.53: 65353+ A? www.routeripaddress.com. (41)
IP 192.168.2.150.44848 > 209.18.47.61.53: 50366+ A?** www.how-to-hide-ip.info. **(41)

```Is Port 53 DNS?  That 209.18.47.61 address is an adelphia server.   Not sure what the various site names are.    Think I am going to shut down for tonight, and look more into it in the morning,


EDIT:  I poked around a little more and I guess those are DNS servers?   I can't figure out why the computer is randomly connecting to them.  All user programs are closed, and the screen saver is active.  I unlock the screen and see these pulses.  I should note that I am running apache for the local network.  I did enter a port 80 pass through on my router but it is closed at this time, unlike most ISP it is not blocked.

---

### Post by SoFl W on 2010-07-22
Text removed, formatting was off and everything was a smiley.

---

### Post by SoFl W on 2010-07-22
Still, regular/steady connections:

```
IP 192.168.1.111.38236 > 74.53.59.134.80: Flags [.], ack 24724, win 495, options [nop,nop,TS val 2703242 ecr 2640472552], length 0
IP 192.168.1.111.48227 > 209.18.47.61.53: 40907+ AAAA? apps.dnsstuff.com. (35)
IP 192.168.1.111.34058 > 209.18.47.61.53: 4220+ AAAA? support.dnsstuff.com. (38)
IP 209.18.47.61.53 > 192.168.1.111.34058: 4220 0/1/0 (88)
IP 192.168.1.111.46678 > 209.18.47.61.53: 2841+ AAAA? support.dnsstuff.com. (38)
IP 209.18.47.61.53 > 192.168.1.111.48227: 40907 1/1/0 CNAME[|domain]
IP 192.168.1.111.38047 > 209.18.47.61.53: 5138+ A? apps.dnsstuff.com. (35)
IP 209.18.47.61.53 > 192.168.1.111.46678: 2841 0/1/0 (88)
IP 192.168.1.111.44009 > 209.18.47.61.53: 42342+ A? support.dnsstuff.com. (38)
IP 209.18.47.61.53 > 192.168.1.111.38047: 5138 2/0/0 CNAME[|domain]
IP 209.18.47.61.53 > 192.168.1.111.44009: 42342 1/0/0 (54)
```


Can't figure out why.

IP address: 209.18.47.61
Reverse DNS: dns-cac-lb-01.rr.com.
Reverse DNS authenticity: [Verified]
ASN: 7843
ASN Name: ADELPHIA-AS
IP range connectivity: 2
Registrar (per ASN): ARIN
Country (per IP registrar): US [United States]
Country Currency: USD [United States Dollars]
Country IP Range: 209.18.0.0 to 209.19.255.255
Country fraud profile: Normal
City (per outside source): Unknown
Country (per outside source): -- []
Private (internal) IP? No
IP address registrar: whois.arin.net
Known Proxy? No
Link for WHOIS: 209.18.47.61

---

### Post by SoFl W on 2010-07-23
Still have this regular connection and can't figure out what it is.

---

### Post by SoFl W on 2010-07-26
One last bump... anybody have any ideas?

---

### Post by SoFl W on 2010-08-21
I will try a weekend day time bump

---

### Post by gradinaruvasile on 2010-08-21
Try something such as 

lsof -i

to see what and where

[http://linuxers.org/howto/how-find-out-active-connections-or-which-ports-are-openlistening-linux](http://linuxers.org/howto/how-find-out-active-connections-or-which-ports-are-openlistening-linux)

---

### Post by SoFl W on 2010-08-21
Thank you, that might have answered my question.  I believe it might be Opera but I will have to do some more testing.  I was thinking it was another program, but I believe I was using Opera at the same time as the other program.  Opera makes more sense.

Thank you again.

---

