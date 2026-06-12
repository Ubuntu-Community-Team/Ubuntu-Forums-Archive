---
title: "Apache and port 80 issues"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by stroiker on 2011-08-27
I am trying to run a webpage outside of my local network using apache on Ubuntu 10.04. My webpage currently loads within my local network, so I know it's working, but it does not work outside of the local network. It is possible that port 80 is being blocked by my ISP or a firewall but I am not sure. Here are a few different errors I get while testing port 80:

80  HTTP  Stealth  There is NO EVIDENCE WHATSOEVER that a port (or even any computer) exists at this IP address!

Error: I could not see your service on XX.XXX.XXX.XXX on port (80)
Reason: Connection timed out

80 (http)	Closed or Filtered

My ISP is Cox Communications. My box running Ubuntu is wired and my laptop is connected to the local network wirelessly on a Linksys WRT54G2 router. Like I said, my laptop will pull up the webpage when apache is running but the webpage will not work outside the local network. 

The issue must be with port 80.
My question is what is going on with port 80, and how can I fix it (workarounds, firewalls, contact ISP etc..) so that I can get my webpage up and running?

[IMG]http://i.imgur.com/4XBMc.png[/IMG]

---

### Post by rickyjones on 2011-08-27
> **stroiker said:**
> I am trying to run a webpage outside of my local network using apache on Ubuntu 10.04. My webpage currently loads within my local network, so I know it's working, but it does not work outside of the local network. It is possible that port 80 is being blocked by my ISP or a firewall but I am not sure. Here are a few different errors I get while testing port 80:

80  HTTP  Stealth  There is NO EVIDENCE WHATSOEVER that a port (or even any computer) exists at this IP address!

Error: I could not see your service on XX.XXX.XXX.XXX on port (80)
Reason: Connection timed out

80 (http)	Closed or Filtered

My ISP is Cox Communications. My box running Ubuntu is wired and my laptop is connected to the local network wirelessly on a Linksys WRT54G2 router. Like I said, my laptop will pull up the webpage when apache is running but the webpage will not work outside the local network. 

The issue must be with port 80.
My question is what is going on with port 80, and how can I fix it (workarounds, firewalls, contact ISP etc..) so that I can get my webpage up and running?

Did you remember to forward port 80 from the router to your server?

Thanks,
Richard

---

### Post by stroiker on 2011-08-27
> **rickyjones said:**
> Did you remember to forward port 80 from the router to your server?

Thanks,
Richard
Yes sir I did.

---

### Post by rickyjones on 2011-08-29
> **stroiker said:**
> Yes sir I did.

As a test try changing the Apache port to 8080 and forward that port to the server. If that works then it means forwarding is fine, but that Cox may be blocking port 80 on residential customers.

Thanks,
Richard

---

