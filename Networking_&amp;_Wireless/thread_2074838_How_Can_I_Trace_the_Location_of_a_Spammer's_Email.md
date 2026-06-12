---
title: "How Can I Trace the Location of a Spammer's Email?"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by w201 on 2012-10-22
Quick question- is it possible to trace an email to the original location from where it was sent by looking at the email headers. 

I used some domain tools to trace an email this way but all I get back is the ISP, which in this case is cox communications. Is there a way to trace the actual sender? 

Thanks!

---

### Post by lisati on 2012-10-22
I don't know of any reliable way of tracing a spammer's location based solely on the contents of email headers.

Part of the problem is that not all email headers are trustworthy: any of them could have been modified by the spammer as an effort to cover their tracks. 

Another issue is that some email providers (e.g. gmail) don't always include the originating IP in the emails they send, which results in cybersleuths running into a dead end once they get to the location of the provider's server.

Even if you have the correct IP address (the X-Originating-IP header is a good start, if it's available), tools such as geolocation queries are only approximate, and don't always give you the real location. If, for example, I was to send you an email from my home network, a geolocation query on the originating IP address would show me to be several hundred kilometres from my true location.

One of the "standard" answers I've seen on the [WhatIsMyIpAddress]("http://whatismyipaddress.com") forum is that chances are you won't be able to learn any more than what you already have without a subpoena for the sender's service provider.

---

### Post by w201 on 2012-10-22
Thank you, lisati, I appreciate you taking the time to answer my question.

---

### Post by *^kyfds( on 2012-10-22
according to my IP adress on geolocation, apparently i'm in slough.

That's about 40 miles away from where i live.

these things are generally wildy inaccurate.

---

### Post by Lars Noodén on 2012-10-22
The only way to be sure is to follow the money.  If you order one of the items in the spam and then cancel the payment, you should still end up with the name (and address) of the people hiring spammers.  They are the source.

---

