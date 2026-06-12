---
title: "Monitor my network traffic"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by AmpersUK on 2010-07-24
**PREAMBLE**

I have a Netgear DG834PN
Wired: "Ubuntu 10-04" desktop and "Windows XP" desktop
Wireless: "Ubuntu 10.04 Netbook" Tablet and HTC Hero phone

At present my wife who works from home's employer pays for our broadband but everyone, including my wife, are retiring at the end of the year and the company will close down and we will have to purchase broadband.* (And I can get rid of Microsoft our of my home!)*
[B]
QUESTION[/B]

Is there a program which will measure all **Internet** traffic passing through the router. There is no need to measure each computer's access, just a lump figure between two chosen dates. Although it will be OK if it gives more information. Once can't have everything tailor made.
[B]
PREVIOUS ACTIONS[/B]

I have been searching through the Internet for two hours and found ipac-ng which is no longer on Universe, and Dan something or other* (I forget the full name)* but that is no longer on Universe either.

Ampers

---

### Post by SCIIAM on 2011-11-26
Why does no one answer ?? :confused:

---

### Post by AmpersUK on 2011-11-27
> **SCIIAM said:**
> Why does no one answer ?? :confused:

Probably because nobody has a clue. :-)

I have given up totally on this.

---

### Post by CryptAck on 2011-11-27
Not really an "answer", but maybe a starting point (even though the original posting was from a year an a half ago). 

How is your current router setup? Some routers actually provide this information, and you could use  bash script to pull the data (wget), summarize, and generate a report. 

You could use iptables to perform the same traffic data collection. It would take some time to setup though, as you'd have to write your own rules. 

Best I can come up with at 6am! Sorry!

Best of luck!

---

### Post by SCIIAM on 2011-12-10
Thanks a lot for replying! If AmpersUK has a setup like mine (and most people I know actually do) he probably has a router sharing directly his internet connection with computers on his LAN. This setup does not give you a unique computer where all traffic has to go through.  Having a computer with 2 Ethernet ports on it could be placed on the WAN side of the router (facing the Internet Service Provider) and monitor easily the traffic but I don't have such machine.

CryptAck said the router could monitor traffic, but mine is only counting packets and from what I remember of my IP networking class the packets do not always have the same size so it can't be used to measure a real throughput.

I really don't mind writing scripts or playing with iptables but I feel that the network architecture we have would required some virtual-circuit or similar "black-magic".

The dual port machine would definitely make thing easier...

---

### Post by aeronutt on 2011-12-10
Don't know if this helps or not, but vnstat measures per computer. Pretty easy to install and use, it's in the repositories.

[http://humdi.net/vnstat/](http://humdi.net/vnstat/)

---

### Post by Dangertux on 2011-12-11
If the router supports SNMP you can MRTG audit it or use Nagios (consult the router's documentation but it may not support that).

Otherwise monitoring at the router will be a little bit difficult without a mirrored port ( which it probably also doesn't have)

So ultimately you'd have to run the audit on the machines individually and hand jam the calculation yourself. That being said, you could set up an SNMP trap and MRTG service or Nagios or something similar to audit total network usage in promiscuous mode. 

I think it's not so much that nobody had a clue but the hardware you're doing this with doesn't support the functionality.

Hope this helps.

---

### Post by SCIIAM on 2011-12-11
I think my router doesn't support these options but I'll check when I get back home. I'll probably convert my ubuntu server-firewall into a simple server and get an old pc with 2 ports to install between my ISP and router so I can easily see the net traffic on the bridge...

Thanks everyone.

---

### Post by winh8r on 2011-12-11
Don't know if this is exactly what you need but I have been using it and it is an accurate measure of network traffic.

[http://netramon.sourceforge.net/eng/news.html]("http://netramon.sourceforge.net/eng/news.html")

It comes as a .deb package for Ubuntu so installation only takes seconds.You can set it to various limits if required to stop you exceeding your monthly bandwidth quotas.

Another useful feature is the ability to export data to an external file , just in case you need to argue with your ISP about usage, which seems to be a common problem nowadays.

Hope this is of some help to you.

---

### Post by SCIIAM on 2011-12-11
Thanks

---

