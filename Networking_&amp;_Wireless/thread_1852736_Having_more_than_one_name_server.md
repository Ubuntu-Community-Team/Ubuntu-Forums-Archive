---
title: "Having more than one name server?"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by k_0z on 2011-09-30
I'd like to know if it's possible to have more than one name server from different hosts.

Example:

URL: mywebsite.com

Name servers:

[COLOR="red"]ns1[/COLOR].domain.com
[COLOR="Red"]ns2[/COLOR].domain.com

[COLOR="red"]ns1[/COLOR].somedomain.com
[COLOR="red"]ns2[/COLOR].somedomain.com

[COLOR="red"]ns1[/COLOR].thisdomain.com
[COLOR="red"]ns2[/COLOR].thisdomain.com

Is this possible?

---

### Post by papibe on 2011-09-30
You can have up to 3 different name servers set on one machine.

I that what you are looking for?
Regards.

---

### Post by k_0z on 2011-09-30
Basically I want to take a load off my name servers and take full advantage of different free hosts. Wha I'm concerned about is the amount I can have for each domain name. Also I'm not sure if I'm allowed to have more than 1 ns1, ns2, etc...

---

### Post by papibe on 2011-09-30
The actual domains (like domain.com) of domain name servers (DNS) don't really matter. You usually set them using IP addresses, so you don't waste time translate them too.

So in total 3, regardless of their domains.

May I ask more details of what you are trying to do? Do you want to use public DNS like Google or OpenDNS?

Regards.

---

### Post by k_0z on 2011-10-01
For instance,

I'm running my website off a free host. It's a shared host and my website starts gaining popularity. Then the servers start to slow down and I am at risk of being banned from the free host. To reduce load, I need to upgrade to VPS or have more name servers.

Is it possible to add different name servers from other hosts or do I have to get a VPS?

---

### Post by papibe on 2011-10-01
> **k_0z said:**
> To reduce load, I need to upgrade to VPS or have more name servers.
Is that your assessment, or you were told that?
 
I think I may have misunderstood your concern. My guess now is that the DNS you referring to aren't the ones that use the server, but the ones the serve it (the one that hold the records of mywebsite.com).

Are you concern of overloading their DNS?

Regards.

---

### Post by k_0z on 2011-10-01
Would a user be able to add shared servers to his domain?

When people log onto the site they use bandwidth. A website hosted on a shared server can only take so much bandwidth before it starts slowing other websites.

The question is: When the traffic increases, is it possible to add different DNS servers from other hosts to my one domain name.

I don't want to add VPS yet...

---

### Post by k_0z on 2011-10-02
Anyone please help?

---

### Post by calanor on 2011-10-02
You are asking the wrong question. A DNS only resolves a query to a name for ex. when you ask for google.com, your nameserver tells you what ip is google.com So what you want is not offloading your DNS server but you want to increase the no of servers that serve your website. I don't know how to do that, but asking your question in the right way will help others answer you. Don't be afraid of asking questions, no one knows it all. Good luck :)

---

