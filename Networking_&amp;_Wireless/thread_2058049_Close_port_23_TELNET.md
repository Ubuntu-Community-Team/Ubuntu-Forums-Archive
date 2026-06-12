---
title: "Close port 23 TELNET"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by ub45 on 2012-09-14
Can anybody help me wth this annoying it's the hell out of me. I ran a port
scan and it showed that port 23 is open, so I decided to close it using GUFW
but when I ported scanned again it showed up as open. I've checked the router and there dose'nt seem to be anything related to Telnet is there 
anything else can be done.

---

### Post by dniMretsaM on 2012-09-14
Try this:
```
sudo apt-get remove telnetd
```

That will remove the Telnet server from your machine (you will still have the client, though).

---

### Post by jerome1232 on 2012-09-14
With what did you run a scan with, are there multiple computers connected to this router?

---

### Post by ub45 on 2012-09-14
I tested with [www.yougotsignal.com](www.yougotsignal.com)

---

### Post by SeijiSensei on 2012-09-14
From the command prompt, type the command "telnet localhost 23".  Does something answer or do you get refused?  If the latter, there isn't any telnet server running.  Nor should there be as it is not installed by default or started by Ubuntu.

If you want to scan ports, I recommend installing nmap with "sudo apt-get install nmap".  Visit nmap.org for more details.

---

### Post by ub45 on 2012-09-14
I've justed with Nmap and it shows ports 53 and 631 and no telnet is this correct.

---

### Post by lisati on 2012-09-14
> **ub45 said:**
> I tested with [www.yougotsignal.com](www.yougotsignal.com)

I don't think so: it looks like a domain parking page filled with advertisements from this end.

---

### Post by ub45 on 2012-09-14
Last reply was wrong telnet is open, just out of curiosity I typed localhost in nmap and
it said telnet closed. than I typed in my ip address and telnet open whats the difference.

---

### Post by iponeverything on 2012-09-14
localhost is your loopback

and if your "ip address" is from from what's my ip or one of those other web services -- you are looking at the ip of your Internet connected gateway device.

odds are you are a on private ip that being masqueraded behind another device -- so it wouldn't really matter what ports you have open..

---

### Post by ub45 on 2012-09-14
Does this mean that gufw was set up wrong????

---

### Post by jerome1232 on 2012-09-15
That means the port scanner you are using is scanning your router not your computer.

you could unblock every port in ufw, then install 50 services all lisenting for connections and that scanner you run wouldn't see a single one of them, your router is "between" you and the rest of the internet.

---

