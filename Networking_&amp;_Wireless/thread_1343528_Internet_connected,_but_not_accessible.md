---
title: "Internet connected, but not accessible?"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by Tidbit on 2009-12-01
Hi, so I've been having some problems with my internet connection. This has been happening with clean installations of both Intrepid and Karmic.

I have a wired connection and my network status says it's connected and active, yet FireFox, Package Manager, and Update Manager are all telling me they can't access the internet?

This computer is hooked up to a router, and the Windows machines sharing this router have no problems connecting to the internet immediately.

The real mystery is that if I leave the computer running, eventually I will be able to access the internet.

I suspect it also helps speed things up if I just keep plugging and unplugging the ethernet cable.

Although every once in awhile things will go smoothly and I'll be able to access the internet immediately after turning the machine on...

I've had this problem on 4 separate machines running Ubuntu...

So to summarize:
Affected OS: Ubuntu Intrepid and Karmic
Symptoms: Firefox, etc act as if I am not online
Network wired connection status: Connected and active
Notes: Only happens when turning the computer on, or after being disconnected (ie. wire pulled out while online). Even then it does not happen 100% of the time. When it does happen it may take anywhere from 10 seconds to an hour to resolve itself on its own. Once established internet access is steady and reliable. It's just very inconvenient to never know if you'll be able to get online immediately, or even how long I'll have to wait. It doesn't even give an indication that anything has changed when I do finally get access so I just have to keep refreshing my browser until the page loads successfully. ONLY Ubuntu running machines are being affected.

Thank you for your help, and your time.

(PS. Sorry my summary was almost as long as the whole post >_<)

---

### Post by teward on 2009-12-02
Your router is trying to use DHCP to assign your Linux computer an IP address, but your computer is choosing not to recognize it.  Perhaps your router's giving you IPv6 addresses, where it should be giving you IPv4 addresses?


I've seen this problem and similar with the wired and wireless networks on-campus at the University I'm attending when Linux is trying to access... my guess is the IP assigning system doesn't like linux much...

---

### Post by Tidbit on 2009-12-02
Any suggestions on confirming this, or even solving it? It's a home computer and I can get administrative/root access, and can also do what I want with the router as long as it keeps working for everyone else...

I guess I'm sort of the underqualified network admin for this building ;)

---

### Post by teward on 2009-12-02
Well, one way is to post the output from the command ```
ifconfig
```This command will list all relevant data pertaining to networking interfaces, including the IP addresses you are being assigned.  As a tech, I can recognize the types of IPs.  For example, a IPv4 address is in the format *.*.*.* where stars are some value.  An IPv6 address follows a completely different format.

So, would you mind posting your ifconfig output for when your computer has internet access?

As for determining if Linux is rejecting the IP address, I'm not too sure.  I do know, however, that if it IS rejecting the IP address, then the DHCP on the router would try to assign another IP address, over and over until its accepted by the computer's OpSys.


***EDIT:  I don't recommend going into your router and messing with its settings unless you have to.  I know many people who messed with their router settings, and now have no working routers (thank god for Best Buy... I get them a new router, then I charge them for setup, hardware, and service fees :P).  Oh, and my friend completely killed his Verizon FiOS router, and had to have Verizon come out and replace it just because he hit the wrong button :P ***

---

### Post by Iowan on 2009-12-02
**ifconfig -a** should show all interfaces (even inactive). If you get a valid IP address (169.254.X.X is **avahi** - probably won't work with the rest of your network), you might check **route -n** to verify your gateway. Finally, see if valid nameservers are in */etc/resolv.conf*.

---

### Post by Tidbit on 2009-12-02
May I ask what parts of the file you're interested in specifically and what information you're looking for? 

I like to post as little information about my system or internet connection as possible, I'm sure you understand ;)

---

### Post by linuxonbute on 2009-12-02
If you are able to check your router you could try something else.

Find out what range of ip addresses it dishes out under DHCP.

You can set your own PC up to have a static ip address in the same subnet 

but outside the range being served up by your router.

As long as it isn't an address used by anything else on your network it 

should be fine. You will also need to give it the right gateway and also 

which DNS addresses it needs.

---

### Post by Iowan on 2009-12-02
From **ifconfig**: what are IP addresses for interfaces. 192.168.X.X are private addresses and are unreachable from Internet. The last line from the **route -n** command should show your router as default gateway. That's where all traffic that's not routed elsewhere will go.

---

