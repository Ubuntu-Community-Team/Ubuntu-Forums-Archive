---
title: "Redirect websites to a local HTML file"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by rowanator on 2011-02-10
Okay, my extensive Googling of this didn't turn up anything relevant, but if this has been posted before please just link me to that and I'll quietly go away. :-)

Basically, I'm running Ubuntu on some really low-end machines (P4s with 1 gig of DDR RAM) off of slow flash drives, so I'm trying to do this with minimal resource usage: I want to redirect certain websites (I'm the admin of an academic-only computer lab, so things like facebook, myspace, kongregate, etc) to a read-only HTML file stored locally.

I know I could just put a simple 0.0.0.0 [url] entry into /etc/hosts, but I have an HTML page with a logger script in it so I can get a feel for how many people are trying to break the rules. I could also put an enrty for 127.0.0.1 [url] and use apache to display the file, but that feels like a bit of a sledgehammer for something so simple and again, I'd rather not use so many resources for this.

Posed simply, what's the simplest and "lightest" way to redirect HTTP requests to a website to a local file?

---

### Post by anglican on 2011-02-11
> **rowanator said:**
> Okay, my extensive Googling of this didn't turn up anything relevant, but if this has been posted before please just link me to that and I'll quietly go away. :-)

Basically, I'm running Ubuntu on some really low-end machines (P4s with 1 gig of DDR RAM) off of slow flash drives, so I'm trying to do this with minimal resource usage: I want to redirect certain websites (I'm the admin of an academic-only computer lab, so things like facebook, myspace, kongregate, etc) to a read-only HTML file stored locally.

I know I could just put a simple 0.0.0.0 [url] entry into /etc/hosts, but I have an HTML page with a logger script in it so I can get a feel for how many people are trying to break the rules. I could also put an enrty for 127.0.0.1 [url] and use apache to display the file, but that feels like a bit of a sledgehammer for something so simple and again, I'd rather not use so many resources for this.

Posed simply, what's the simplest and "lightest" way to redirect HTTP requests to a website to a local file?I would have thought iptables is the way to do this. Take a look at:

http://www.faqs.org/docs/iptables/targets.html#REDIRECTTARGET

H

---

### Post by rowanator on 2011-02-11
> **anglican said:**
> I would have thought iptables is the way to do this. Take a look at:

[http://www.faqs.org/docs/iptables/targets.html#REDIRECTTARGET](http://www.faqs.org/docs/iptables/targets.html#REDIRECTTARGET)

H

Thanks, that looks like exactly what I need. Just to confirm, you can redirect to a specific path rather than a different IP and/or port?

---

### Post by anglican on 2011-02-14
> **rowanator said:**
> Thanks, that looks like exactly what I need. Just to confirm, you can redirect to a specific path rather than a different IP and/or port?Umm, no, it would direct to a port e.g. for a proxy server which could then handle redirection to a specific place.

H

---

### Post by SeijiSensei on 2011-02-14
If you can dedicate a box to it, you're best bet is to run Squid in transparent proxy mode.  Then you can write rules that permit or forbid access to specific URLs based on domain, mimetype, etc., etc.  There are a couple of HOWTOs out there that describe how to set this up.  Even on an old PC like the ones you describe, you shouldn't have a problem handing requests for a computer lab.  I'm running this configuration on a P4 that easily handles requests from over 200 users.

---

