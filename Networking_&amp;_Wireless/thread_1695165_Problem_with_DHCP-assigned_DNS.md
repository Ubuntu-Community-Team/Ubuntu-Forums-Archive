---
title: "Problem with DHCP-assigned DNS"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by ratcheer on 2011-02-25
This is weird and its making me feel stupid. One Ubuntu Maverick installation is working properly and the other is not and they are both set the same way.

I have my OpenDNS servers set statically in my router. Both Ubuntu installations are set to "Automatic (DHCP)". If I look at /etc/resolv.conf, both systems say they are using the router (192.168.1.1) as the nameserver. However, one system is getting the features of OpenDNS and the other is not.

For example, on the one that does not seem to be using OpenDNS, if I go to [http://welcome.opendns.com](http://welcome.opendns.com), I get the Oops! page that says "You do not appear to be using OpenDNS". If I use my OpenDNS shortcuts, they fail to work. And if I go to the OpenDNS Phishing test page, the Phishing test page is shown (which would not happen if OpenDNS was being used.

On the other system, all the above functions work correctly. And the two systems seem to be configured the same way. What the heck is going on?

I know I could set the nameservers manually, but I want to control this stuff from one location, the router.

Tim

---

### Post by ratcheer on 2011-02-25
Ok, I can verify by using the dig command that both hosts are indeed using my router for their DNS queries.

tim@tim-mav-prod:~$ dig welcome.opendns.com

; <<>> DiG 9.7.1-P2 <<>> welcome.opendns.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17142
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;welcome.opendns.com.        IN    A

;; ANSWER SECTION:
welcome.opendns.com.    300    IN    CNAME    [www.opendns.com](www.opendns.com).
[www.opendns.com](www.opendns.com).    30    IN    A    208.69.38.150

;; Query time: 73 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Fri Feb 25 11:52:31 2011
;; MSG SIZE  rcvd: 71

The only DNS servers assigned on the router are 208.67.222.222 and 208.67.220.220, that is, OpenDNS.

Again, what is going on?

Tim

---

### Post by ratcheer on 2011-02-25
I suppose this is a bug in my router firmware. I edited resolv.conf to specify the OpenDNS servers, and marked the file read-only. Now, the OpenDNS features work correctly.

Tim

---

### Post by ratcheer on 2011-02-25
Yes, it was the router. I found a workaround in the OpenDNS knowledge base, which said to add option "strict-order" to the DNSMasq configuration. I then reverted /etc/resolv.conf to go to the router and everything still works.

Tim

---

