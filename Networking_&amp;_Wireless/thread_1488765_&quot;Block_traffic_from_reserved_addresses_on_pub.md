---
title: "&quot;Block traffic from reserved addresses on public interfaces&quot; + akamaitechnologies.com"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by yottabyte on 2010-05-20
Hey Everyone,

I have been having a strange intermittent problem with my internet connection.  Specifically, every once in a while Firestarter (iptables) would block incoming connections from "deploy.akamaitechnologies.com" and I would be unable to load certain websites in my browser, such as "bbc.co.uk", "newegg.com", and others.  These incoming connections from "deploy.akamaitechnologies.com" would occur sporadically and it quickly became annoying to loose the ability to browse the web proper.  In my efforts to remedy the problem, I came across the option "Block traffic from reserved addresses on public interfaces" in Firestarter, which once disabled (unchecked) solved the problem.  Strangely, I can re-enable this feature at some other time in the day, or just wait it out, and do not receive any incoming connections from "deploy.akamaitechnologies.com" and all websites load just fine.  From what I have read, "akamai" is a company that provides bandwidth for various websites.

More strangely, Firestarter documentation does not provide any explanation for "Block traffic from reserved addresses on public interfaces" and my web search turned out nothing, except for a Ubuntu bug report (#35738) that describes this very problem.  This bug report is dated 2009-04-07 and zero comments have been made on it.  Personally, I have had this option enabled for some time now and did not experience problems until just recently.  As I am writing this, "Block traffic from reserved addresses on public interfaces" is enabled and all websites, including the previously mentioned "bbc.co.uk" and "newegg.com" load perfectly, but I am also not receiving any incoming connections from "deploy.akamaitechnologies.com".  I am confused and a bit bewildered by this situation as these "port scans" by Akamai seem to block access to websites that I want to view, and then they mysteriously stop.

-Can anyone explain what  "Block traffic from reserved addresses on public interfaces" does exactly?

-Why do connections from "deploy.akamaitechnologies.com" prevent the viewing of certain websites when they are blocked by Firestarter (iptables)?

-Why do I need connections to "deploy.akamaitechnologies.com" in the first place?

---

### Post by yottabyte on 2010-05-20
*bump*

---

### Post by yottabyte on 2010-05-23
*bump*

Any takers?  It just might be you with this problem tomorrow...

---

### Post by atanu1 on 2010-07-19
AFAIK reserved IP addresses refer to pvt. or non-route-able addresses on the Internet.   Thus if traffic from these kind of addresses come from a public interface (i.e. an interface with a pub IP) then they are suspect since pvt IPs are not supposed to exist in the pub Internet.  This cud mean some kind of spoofing, etc. and, hence, blocking them is a good idea. This is relevant if your computer (on which the firewall is running) has a public IP (i.e. is visible from the Internet).  So,  If your computer is directly exposed to Internet then block these reserved addresses.  Else if your computer is behind a NAT (or does not have any pub IP associated with any interface) then don't block.  Off-course properly analyze your problem in light of the "reserved addresses" explanation above and then decide on your course of action.  YMMV

---

### Post by atanu1 on 2010-07-19
_Regarding akamai:_

Akamai corp. is a CDN (Content Distribution Distribution) company. They provide mirror/proxy servers which are strategically located across the globe (in terms of connectivity). **Their clients** use these servers to speed up delivery of web page contents to a **users browser**. 

Thus if a given website uses Akamai services then you hv to allow **the website** and **akamai** to get the full web experience!

---

### Post by MIJ-VI on 2010-08-26
I'm currently using these Google DNS settings...

Primary DNS: [8.8.8.8]("http://whois.domaintools.com/8.8.8.8")
Secondary DNS: [8.8.4.4]("http://whois.domaintools.com/8.8.4.4")

...and I was just trying to view...

[http://technology.timesonline.co.uk/tol/news/tech_and_web/article7110657.ece](http://technology.timesonline.co.uk/tol/news/tech_and_web/article7110657.ece)

...and was blocked from doing so when Firestarter was pinged repeatedly with these events every time I clicked the link to said desired web page:

Time: Aug 26 02:56:12 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  Port: 48246 Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 02:57:10 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  Port: 48260 Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 02:58:00 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  Port: 48265 Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:17:05 Source: a184-84-76-20.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  Port: 38677 Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

I have Firestarters Preferences set as follows:

Firewall-->ICMP Filtering set to 'Enable ICPM Filtering' while allowing none of other ICMP packet types.

ToS Filtering is not enabled.

Advanced Options:
**Prefered packet rejection method**: Drop silently

**Broadcast traffic**
- Block broadcasts from external network: check marked.
- Block broadcasts from internal network: check marked.

**Traffic validation**
- Block traffic from reserved addresses on public interfaces: check marked.

The reason why I have Firestarter locked down so tightly is that shortly after entering into an arrangement with my non-tech-savvy, Windows 7-using neighbours to access their Internet connection via Wi-Fi in exchange for paying half of their monthly bill, my 64 bit Ubuntu 10.04.1's Firefox 3.6.8 began experiencing random redirects which [detective work]("http://www.talkbass.com/forum/showthread.php?t=677892") on the 'Net revealed were being caused by my neighbour's router having apparently been DNS-hijacked to a Russian address resulting in Firestarter being regularly pinged with...

Time: Aug 18 17:32:07 Source: [213.109.65.90]("http://whois.domaintools.com/213.109.65.90") Destination: 192.168.0.180 In IF: eth1 Out IF:  Port: 53 Length: 92 ToS: 0x00 Protocol: ICMP Service: DNS

Time: Aug 18 18:10:21 Source: [213.109.73.246]("http://whois.domaintools.com/213.109.73.246") Destination: 192.168.0.180 In IF: eth1 Out IF:  Port: 53 Length: 97 ToS: 0x00 Protocol: ICMP Service: DNS

...therefore I'm leery about granting this alleged 'deploy.akamaitechnologies.com' passage through Firestarter even though the ports it is scanning appear to fall within the boundaries of...

[Registered Ports: 1024 through 49151.]("http://www.speedguide.net/port.php?port=48246&print=friendly")

**So, my question is:**

 Is it safe to allow this 'deploy.akamaitechnologies.com' an open port?

**UPDATE:** I just entered deploy.akamaitechnologies.com into the URL box of a blank Firefox page and then tried to go to said page and the Firefox Add-on WOT threw up a full page "WARNING! This site has a poor reputation."  :shock:

---

### Post by MIJ-VI on 2010-08-26
**An addendum to my previous post:**

I tried repeatedly clicking the...

[http://technology.timesonline.co.uk/tol/news/tech_and_web/article7110657.ece](http://technology.timesonline.co.uk/tol/news/tech_and_web/article7110657.ece)

...link I mentioned earlier and got this from Firestarter's Events window:

Time: Aug 26 04:48:22 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57438** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:49:43 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57459** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:50:30 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57465** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:51:18 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57471** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:52:05 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57481** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:53:05 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57493** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:53:53 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 60048** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:55:09 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 60054** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:55:57 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 60063** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:56:44 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 60069** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:57:31 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 60075** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:58:17 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 39098** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:59:04 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 39103** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 04:59:51 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 39109** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:00:38 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 39118** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:01:25 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 39126** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:02:12 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 39131** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:02:59 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 39137** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:03:46 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 41082** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:04:32 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 41088** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:05:25 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 41098** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:06:13 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 41103** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:06:59 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 41109** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:07:46 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 41115** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:08:33 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 45999** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:09:20 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 46004** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:10:07 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 46010** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:10:54 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 46018** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:11:41 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 46024** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:12:28 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 46033** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:13:14 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 47420** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:14:01 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 47428** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:14:47 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 47436** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:15:34 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 47444** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:16:20 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 47451** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:17:07 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 47459** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:17:54 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 47467** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:18:40 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 33201** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:19:27 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 33209** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:20:13 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 33220** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:21:05 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 33228** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:21:51 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 33236** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:22:37 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 33243** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:23:24 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57807** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:24:11 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57815** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:25:03 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57823** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

Time: Aug 26 05:25:50 Source: a184-84-70-216.deploy.akamaitechnologies.com Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 57829** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

It would seem then that this 'deploy.akamaitechnologies.com' is pinging Firestarter in both of these port ranges:

[URL="http://www.speedguide.net/port.php?port=48246&print=friendly"]Registered Ports: 1024 through 49151. 
Dynamic/Private : 49152 through 65535.[/URL] <-- [-X

I'm hoping that someone waaay smarter than I will come along and enlighten me as to how to proceed.

Thank you.

---

### Post by MIJ-VI on 2010-08-26
So I just went to check out what info on WOT could provide and when I copied...

[http://www.similarsites.com/sites-like/deploy.akamaitechnologies.com](http://www.similarsites.com/sites-like/deploy.akamaitechnologies.com)

...into Firefox's URL box and then tried to go there I got this...

[http://www.similarsites.com/alternativesearchers.aspx](http://www.similarsites.com/alternativesearchers.aspx)

...followed by a stream of Firestarter events which started with...

Time: Aug 26 05:50:23 Source: ec2-184-73-242-75.**compute-1.amazonaws.com** Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 48459** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

...and ended with:

Time: Aug 26 05:52:03 Source: ec2-184-73-242-75.**compute-1.amazonaws.com **Destination: 192.168.0.180 In IF: eth1 Out IF:  **Port: 48480** Length: 44 ToS: 0x00 Protocol: TCP Service: Unknown

I just found these threads:

[**[COLOR=#980101][B][ubuntu]**[/COLOR] What's this: ec2-174-129-227-92.compute-1.amazonaws.com[/B]]("http://ubuntuforums.org/showthread.php?t=1522773")

[**     [COLOR=#980101][B][ubuntu]**[/COLOR] Akamai technologies Yahoo and Microsoft[/B]]("http://ubuntuforums.org/showthread.php?t=1016471")

**CUT TO THE CHASE:**

"...one report reveals that for every static file downloaded from Akamai, an attempt is made to breach the firewall. The **intent** of this, is a **load-balancing measure**;  in an effort to see which server responds fastest, it will send a  packet of data to the user's computer from each of its servers and see  which one bounces back quickest. **The trouble is, with a firewall, the  packet doesn't bounce - it sticks, intercepted by the firewall - and  when nothing comes back, Akamai will continuously make attempt after  attempt instead of simply choosing a server at random** (or by some  other criteria). Norton Personal Firewall views these as "suspicious  activity" and won't let them through, nor will it dignify them with a  response. Presumably **other** firewalls will react similarly. The  end result: any site with Akamai multi-server hosting will either load  REALLY slowly (if only part of the static content eg images, secure  content, etc. is hosted over multiple servers by Akamai) or time out  entirely (if the whole site is hosted this way) as **Akamai makes hundreds if not thousands of attempts to breach the firewall for a single page download**."

Akamai Technologies?
[http://forums.thinkbroadband.com/security/3576350-akamai-technologies.html#Post3576458](http://forums.thinkbroadband.com/security/3576350-akamai-technologies.html#Post3576458)

---

### Post by atari_gods on 2011-03-05
Greetings,

I can relate in an almost frightened way to your problem MIJ-VI, almost port for port from your posts. I too have had problems connecting to websites (newegg.com included) and when I check Firestarter I see the same Sources (*****.deploy.akamaitechnologies.com), variety of Ports (Registered Ports: 1024 through 49151 & Dynamic/Private : 49152 through 65535), and Length (44). Earlier days these issues would crop up right after an ssl update came through, but lately it seems to happen whenever. Now it is constant.

I wrote [a post]("http://ubuntuforums.org/showthread.php?t=1679360") about a month ago describing my issue, but it was less detailed and I didn't have Firestarter at the time or know what I was really looking for. I haven't got any responses there, so I am hoping by finding a similar problem post that people might be able to generate some answers to the problem.

---

