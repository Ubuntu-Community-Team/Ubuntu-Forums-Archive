---
title: "IP through DHCP but use different DNS Server"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by crazy4nix on 2011-09-21
Hey guys
My ethernet connection (eth0) gets its ip address through dhcp. But I need to use a different dns server than the one provided by router. Everytime the computer starts, and once I get connected, I have to manually modify /etc/resolv.conf
Is there a more permanent way? Thanks a lot in advance :)

---

### Post by sanderj on 2011-09-21
Edit the /etc/dhcp/dhclient.conf and add the line:

prepend domain-name-servers 8.8.8.8;

(if you want 8.8.8.8 to be that nameserver).

---

### Post by crazy4nix on 2011-09-21
alright... but I want this to be applicable only to my eth0 and not my wlan0 when I'm at home or at a coffee shop. Any way I can tell it to apply this custom dns server only for my eth0 connection?

---

### Post by jvance492 on 2011-09-21
> **crazy4nix said:**
> alright... but I want this to be applicable only to my eth0 and not my wlan0 when I'm at home or at a coffee shop. Any way I can tell it to apply this custom dns server only for my eth0 connection?

I would log into whatever device is passing IP addresses, and assign the DNS servers there. IF its a home router, like a linksys by Default they assign you 192.168.1.1 if the DNS translation table gets screwed up it tends to fail. Assigning 8.8.8.8 or 8.8.4.4 or even your ISP's DNS server directly to the DHCP router it should take care of the problem.

---

### Post by sanderj on 2011-09-21
> **crazy4nix said:**
> alright... but I want this to be applicable only to my eth0 and not my wlan0 when I'm at home or at a coffee shop. Any way I can tell it to apply this custom dns server only for my eth0 connection?

Check out EXAMPLES on [http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=dhclient.conf](http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=dhclient.conf) ... you can specify options per interface  ...

---

### Post by crazy4nix on 2011-09-21
> **jvance492 said:**
> I would log into whatever device is passing IP addresses, and assign the DNS servers there.
Unfortunately, I don't have access to that router... it's a work router.

---

### Post by crazy4nix on 2011-09-21
> **sanderj said:**
> Check out EXAMPLES on [http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=dhclient.conf](http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=dhclient.conf) ... you can specify options per interface  ...
Thanks for the valuable link. Will check it out.
Edit: Checked it out... I think supersede is the option that I need to use rather than prepend in the interface specific stanza. Thanks again.
The link you gave is a manpage... lol.. It reminds me how important manpages are... most of us simply don't use them even though they are a command away.

---

