---
title: "cannot browse by FQDN"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by JohnSka7 on 2010-09-05
Hello all,

brand new install of 10.4 server and I'm having a strange issue. I cannot browse to any website by it's domain name, but I can connect via IP address.

I've been googling around and did the following:
added nameservers to /etc/resolv.conf based on an nslookup from my windows box:
nameserver 71.250.0.12
nameserver 68.237.161.12

I commented out the hosts line in /etc/nsswitch.conf per another site and changed it to:
hosts: files dns

I can see other computers on my local network via IP and I can browse to the server's default apache page by it's hostname, so I'm assuming it's something about the server's dns resolution, but I'm not sure of my next step.

Any ideas?

---

### Post by BkkBonanza on 2010-09-05
What do you get when you try **nslookup google.com** in a terminal?

---

### Post by JohnSka7 on 2010-09-05
A very long pause and then:

;; connection timed out; no servers could be reached

---

### Post by BkkBonanza on 2010-09-05
Either there is a reslov.conf problem or connectivity issue. Try,

**cat /etc/resolv.conf**

**traceroute 71.250.0.12**

And post output. You said you added nameservers to resolv.conf but if you left other lines in the file they could be causing trouble. Adn traceroute will show the path attempted to reach the nameserver (if not blocked by a firewall or routing problem).

---

### Post by JohnSka7 on 2010-09-05
Ok, so here are the results:

```
traceroute to 71.250.0.12 (71.250.0.12), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  0.841 ms  1.388 ms  1.288 ms
 2  98.110.91.1 (98.110.91.1)  7.818 ms  9.761 ms  11.556 ms
 3  130.81.146.42 (130.81.146.42)  11.458 ms  11.495 ms  10.263 ms
 4  130.81.27.249 (130.81.27.249)  108.541 ms  110.701 ms  110.714 ms
 5  130.81.29.36 (130.81.29.36)  17.933 ms  20.068 ms  20.293 ms
 6  130.81.20.161 (130.81.20.161)  20.188 ms  14.574 ms  16.633 ms
 7  * * *
 8  * * *
 9  * * *
10  * * *
[snip]
29  * * *
30  * * *
```

When I do the same on my windows box, I get this:
```

Tracing route to nsnwrk01.verizon.net [71.250.0.12]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  192.168.1.1
  2     6 ms     6 ms     6 ms  L100.CMDNNJ-VFTTP-35.verizon-gni.net [98.110.91.
1]
  3     7 ms     7 ms     6 ms  G3-0-5-435.CMDNNJ-LCR-04.verizon-gni.net [130.81
.146.42]
  4    15 ms    13 ms    14 ms  P10-0-0.CMDNNJ-LCR-03.verizon-gni.net [130.81.27
.249]
  5    15 ms    14 ms    14 ms  so-7-3-0-0.NWRK-BB-RTR1.verizon-gni.net [130.81.
29.36]
  6    14 ms    14 ms    14 ms  so-7-2-0-0.NWRK-CORE-RTR1.verizon-gni.net [130.8
1.20.161]
  7    14 ms    14 ms    14 ms  71.250.0.5
  8    16 ms    14 ms    13 ms  nsnwrk01.verizon.net [71.250.0.12]

Trace complete.

```
So it looks like it almost gets there, but dies out at the second to last stop.

As for the resolv.conf:
```

nameserver 208.67.222.222
nameserver 208.67.220.220

```

---

### Post by BkkBonanza on 2010-09-05
Now your resolve.conf is set for OpenDns?

Try traceroute to that IP then. Did you change it? Or is your router configured to hand out OpenDns (208.67.222.222) during DHCP?

Windows sends ICMP pkts for traceroute but Linux sends UDP pkts. So this indicates that somewhere out there UDP pkts are getting dropped. But why for Linux vs. Windows - I don't know yet.

If your DNS works with OpenDns then that's good. Also Google has DNS at 8.8.8.8 / 8.8.4.4 which I prefer.

(There have been recent changes in DNS due to ISPs starting to do DNSSEC. In a few cases it's possible that UDP requests over 512 bytes may have problems. I don't know if this is causing a difference in behaviour between OSs. But the symptoms seem possibly related. The solution would be for now to not use the verizon DNS if it's causing issues.)

---

### Post by JohnSka7 on 2010-09-10
> **BkkBonaza said:**
> Now your resolve.conf is set for OpenDns?

Try traceroute to that IP then. Did you change it? Or is your router configured to hand out OpenDns (208.67.222.222) during DHCP?

Windows sends ICMP pkts for traceroute but Linux sends UDP pkts. So this indicates that somewhere out there UDP pkts are getting dropped. But why for Linux vs. Windows - I don't know yet.

If your DNS works with OpenDns then that's good. Also Google has DNS at 8.8.8.8 / 8.8.4.4 which I prefer.

(There have been recent changes in DNS due to ISPs starting to do DNSSEC. In a few cases it's possible that UDP requests over 512 bytes may have problems. I don't know if this is causing a difference in behaviour between OSs. But the symptoms seem possibly related. The solution would be for now to not use the verizon DNS if it's causing issues.)

Sorry about the delay in response, work has been crazy.

I bounced back and forth between verizon and opendns...I use opendns on my windows machine but I figured any port in a storm...

I tried using the google dns you supplied but still nothing. I also put my ubuntu box in my router's DMZ just to test, still no dice, so I'm really at a loss.

---

