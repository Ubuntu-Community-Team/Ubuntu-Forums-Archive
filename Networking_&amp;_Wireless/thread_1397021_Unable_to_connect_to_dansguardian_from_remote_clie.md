---
title: "Unable to connect to dansguardian from remote clients"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by jclholdings on 2010-02-02
Hello,
 
Any help would be appreciated.
 
I've tried both Jaunty and Karmic both with the same results. Dansguardian is listening on port 8080 with tinyproxy on 3128.
 
Using firefox locally on the box - configuring it to connect to proxy at 127.0.0.1:8080 it works... also configuring it to connect to proxy over the ip address of my wireless adapter:8080 works as well. I even visit blocked sites and get the blocked message... so all is well there.
 
I can ssh to the ubuntu box over port 22 from other windows boxes on my wireless network - all is well there too.
 
When I try to configure IE on a remote windows box to connect to proxy on the ubuntu box's static ip over either 8080 or 3128 I get a timed out connection.
 
No messages appear in the dansguardian or tinyproxy logs indicating an attempted or denied connection. 
 
I do get entries in the syslog like this:
 
Feb 2 17:29:52 ubuntu kernel: [ 604.356730] IN=wlan0 OUT= MAC=ubuntu wireless mac SRC=ip of windows box DST=ip of ubuntu box LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=2754 DF PROTO=TCP SPT=49241 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0
 
So the ubuntu box appears to be getting the packets but the connection is dying somewhere... is there some sort of access list somewhere that's blocking me?
 
The ubuntu box is connecting to a wrt54g router with a wmp54g adapter.
 
Links welcome.
 
Thanks

---

### Post by jclholdings on 2010-02-03
One more tidbit... I don't think it's a dansguardian problem... the same thing happens if I have the browser connect to port 3128... firefox on the local ubuntu machine works, remote clients do not.
 
I will provide any log information that may help.
 
Thanks!

---

### Post by jclholdings on 2010-02-03
Would some sort of sniffer log help troubleshoot this?
 
Thanks

---

### Post by ant2ne on 2010-02-03
troubleshoot firewall on dansguardian box.

Quick googling around....

[http://nixforums.org/about76878.html](http://nixforums.org/about76878.html)

[http://blog.dipinkrishna.info/2009/07/howto-setup-squid-proxy-dansguardian.html](http://blog.dipinkrishna.info/2009/07/howto-setup-squid-proxy-dansguardian.html)

[http://symbolik.wordpress.com/2007/03/06/web-filtering-with-squid-squidguard-and-dansguardian/](http://symbolik.wordpress.com/2007/03/06/web-filtering-with-squid-squidguard-and-dansguardian/)

web filtering is kind of advanced networking. You'll learn a lot and have fun, but expect it to be a challenge. 

I've got a dans+squid VM (virtual box) running on my home network and it is working great. If I could email you the 5gig VM I would.

---

### Post by jclholdings on 2010-02-05
Thanks for the reply... I've read through all three and only a small portion applies to my setup... 

I ran dansguardian successfully in ubuntu 8.something for a long time, then when I upgraded to 9 that's when it broke.

Right now dansguardinan/tinyproxy is working... I can get the local copy of firefox to connect ok... it's just remote clients cannot connect... that's what makes me think this is a more general networking issue.

---

### Post by jclholdings on 2010-02-05
More info:

I also cannot connect to CUPS from a remote computer - [http://ipaddr:631](http://ipaddr:631)

but my local firefox browser will connect ok.

This seems to me to be a general networking configuration problem...

---

### Post by ant2ne on 2010-02-06
can you ping dansguardian box? Can dansguardian box ping the clients?

troubleshoot firewall on dansguardian box. What are you using for a firewall?

---

### Post by jclholdings on 2010-02-06
The windows box can ping the ubuntu box, but ubuntu can't ping the windows box... is that a routing issue?
 
This is a fresh 9.10 install... I'm not running a firewall that I'm aware of (unless one installs by default).
 
Thanks again for the help.

---

### Post by ant2ne on 2010-02-16
> but ubuntu can't ping the windows box turn of windows firewall and try again.

---

