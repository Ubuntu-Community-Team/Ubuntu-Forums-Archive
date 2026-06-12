---
title: "Networking newbie needs firewall advice"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by cknight on 2010-02-26
OK, so for several years now I've had issues with certain web sites, many related to google such as maps.google.com or images.google.com or flickr where a bit of the map or a few of many images might load and then it stalls and I get nothing more.  This drove me nuts as it often rendered these sites useless and I've been looking for solutions ever since.  

Then finally, I stumbled across the right google search combination.  The issue is with my router's (a 3Com OfficeConnect ASDL wireless 11g router) firewall.  Apparently it has this feature called SPI which has issues with certain types of network traffic.  Changing my router's firewall "level" setting from High to Medium suddenly opened the flood gates and now all maps and imagery load at super wonderful speeds and I have no further issues.

So my question is what vulnerabilities have I opened myself up to?  Should I be concerned or be looking for an alternative solution for this SPI thing?  I'm just an average home user.

From the firewall help text on the different settings of firewall protection:
> Low Level: IP spoofing check only.
Medium Level: Adding DoS pattern match, RIP defect (for P2P application).
High Level: Adding SPI feature.

Enabling the 'High' setting gives me these additional (editable) super-techy settings (with no associated help text):
> Connection Policy
 Fragmentation half-open wait : 	 10 secs
 TCP SYN wait : 	 30 secs
 TCP FIN wait : 	 5 secs
 TCP connection idle timeout : 	3600 secs
 UDP session idle timeout : 	30 secs
 H.323 data channel idle timeout : 	180 secs
 
DoS Detect Criteria
 Total incomplete TCP/UDP sessions HIGH : 	300 session
 Total incomplete TCP/UDP sessions LOW : 	250 session
 Incomplete TCP/UDP sessions (per min) HIGH : 	250 session
 Incomplete TCP/UDP sessions (per min) LOW : 	200 session
 Maximum incomplete TCP/UDP sessions number from same host : 	 10 session
 Incomplete TCP/UDP sessions detect sensitive time period : 	 300 msecs
 Maximum half-open fragmentation packet number from same host : 	 30 packet
 Half-open fragmentation detect sensitive time period : 	 10000 msecs
 Flooding cracker block time : 	 300 secs
Any help or advice most appreciated.  Thanks!

---

### Post by cknight on 2010-02-27
Still looking for advice.  I should add that I don't use any VNC/remote desktop features.  Thanks.

---

### Post by 2hot6ft2 on 2010-02-27
> **cknight said:**
> Still looking for advice.  I should add that I don't use any VNC/remote desktop features.  Thanks.
Then you're fine. Ubuntu has iptables and incoming connections are closed by default. You don't need to do anything unless you start opening ports for things like VNC, SSH, and the like. For normal everyday use there's no problem.

---

### Post by cknight on 2010-02-27
Well, I'm a bit confused then.  After your post I've been looking up info on iptables and SPI.  If I understand correctly, SPI is a good thing to have and iptables can be configured to enable this aspect.  However, you state that incoming connections are closed by default.  But my (untouched) iptables configuration shows the following:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      
```
Doesn't this mean that I am accepting all incoming packets and therefore have no SPI protection?  Or by "incoming connections are closed by default" do you mean some other networking, er, thing?  Thanks!

---

### Post by 2hot6ft2 on 2010-02-27
> **cknight said:**
> Well, I'm a bit confused then.  After your post I've been looking up info on iptables and SPI.  If I understand correctly, SPI is a good thing to have and iptables can be configured to enable this aspect.  However, you state that incoming connections are closed by default.  But my (untouched) iptables configuration shows the following:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      
```
Doesn't this mean that I am accepting all incoming packets and therefore have no SPI protection?  Or by "incoming connections are closed by default" do you mean some other networking, er, thing?  Thanks!
I may be wrong but doesn't that make the target is the source. Perhaps the loopback interface or meaning that if you connect to a web site it's allowed to answer you?

I'm not that familiar with iptables it confuses me still since I haven't made the time to learn it.
Have you tried testing your ports with any of the many port scanners that are out there like grc.com

Or find out which ports you have open with nmap
```
nmap -PS localhost
```
Here's mine
> Interesting ports on localhost (127.0.0.1):
Not shown: 998 closed ports
PORT    STATE SERVICE
53/tcp  open  domain
631/tcp open  ipp


---

