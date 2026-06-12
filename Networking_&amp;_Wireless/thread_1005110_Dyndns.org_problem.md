---
title: "Dyndns.org problem?"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2008-12-07
I have a dyndns.org host setup (i'll post my address later if it will be helpful, although I would prefer not.) I installed ddclient onto my server and enabled port forwarding (ports 80 for http and 23 for ssh) on my router.

I am able, from behind my own router, to get to the server. However, I cannot get to it when I borrow my neighbors wifi. I just get a "site not found" error in firefox. Does anybody know why I cannot get to my server from the broader interwho?

---

### Post by jmoorse on 2008-12-07
From the wifi connection:

1. In terminal run nslookup
2. Type in your DynDns domain name

If it doesn't resolve DNS updates may still be propagating.

Do you see the correct IP information in your DynDNS account?

Some ISPs (COX) filter inbound TCP80 so you may want to redirect TCP8080 to internal TCP80 to test.

---

### Post by rhcm123 on 2008-12-07
> **jmoorse said:**
> From the wifi connection:

1. In terminal run nslookup
2. Type in your DynDns domain name

If it doesn't resolve DNS updates may still be propagating.

Do you see the correct IP information in your DynDNS account?

Some ISPs (COX) filter inbound TCP80 so you may want to redirect TCP8080 to internal TCP80 to test.

I'm behind fios, (which i have had very few problems with), and I'm reading they block 80. Can you explain to me how to forward 8080 to 80?

EDIT:
I just got an online scan of my ports. The only ones fully open are: 22 23 25 139 445 (protocols that I use). The rest are closed because there is no program using them. (I.E. the server stated they existed then dropped the connection.) 

Here's the kicker:
My port 80 is "stealthed", meaning that, while the rest of the ports responded that they existed and were either closed or open to connections, this port did not respond to a request at all. There was no evidence of a PC even existing at that entry. (135 responded the same.) However, 8080 is not blocked! Can anybody give me simple forwarding instructions?

---

### Post by jmoorse on 2008-12-08
Can you provide your Router/Firewall make/model?

Basically you need to make external TCP8080 to internal 80 at local ip address.

E.g.: [http://1.1.1.1:8080](http://1.1.1.1:8080) >NAT> 192.168.1.100:80

---

### Post by dmizer on 2008-12-08
Port 80 may be blocked by your ISP. If that's the case, you'll likely find that 8080 is also blocked.

You can use the "WebHop Settings" feature in your dyndns account settings to set up any port you like as well as mask it. That way, you can type [http://yourhost.dyndns.com](http://yourhost.dyndns.com) and get your homepage at [http://yourhost.dyndns.com:8080](http://yourhost.dyndns.com:8080)

---

### Post by rhcm123 on 2008-12-08
> **dmizer said:**
> Port 80 may be blocked by your ISP. If that's the case, you'll likely find that 8080 is also blocked.

You can use the "WebHop Settings" feature in your dyndns account settings to set up any port you like as well as mask it. That way, you can type [http://yourhost.dyndns.com](http://yourhost.dyndns.com) and get your homepage at [http://yourhost.dyndns.com:8080](http://yourhost.dyndns.com:8080)

I've gotten port 8080 forwarded on my router to, well, port 8080 on mah server (i enabled it in /etc/apache2/apache2.conf, ports.conf, and whatever the otherone is.) It appears the only port blocked is 80.

How would i enable webhop? (Just curious.)

---

### Post by dmizer on 2008-12-08
Log into your dyndns account > click on "my hosts" > click on your hostname under "Host Services" > switch to "Web Hop" next to the "Service Type" > configure as needed.

---

### Post by rhcm123 on 2008-12-08
> **dmizer said:**
> Log into your dyndns account > click on "my hosts" > click on your hostname under "Host Services" > switch to "Web Hop" next to the "Service Type" > configure as needed.

How would I configure it? Would i just do xxx.dyndns.org:8080

---

