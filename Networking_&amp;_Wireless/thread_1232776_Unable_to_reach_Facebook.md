---
title: "Unable to reach Facebook"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by pvoce on 2009-08-05
I have a weird problem that I've come up against: I cannot reach [www.facebook.com](www.facebook.com) from my laptop. (Ubuntu 9.04, Inspiron 1420n Model).

My wife's Windoze box find the site perfectly well via our wireless router.

I cannot tracert or ping the url, both just hang there in the console.

I have tried other browsers, such as Opera and Epiphany, which of course do not work since it as a lower networking level.

Is there perhaps a whitelist or a way to reset an internal DNS setting?

Thanks for any and all help ahead of time.

PV

---

### Post by Hobgoblin on 2009-08-05
Can you get there by IP address? (ping it from the working Windows system to get the IP).

If so you have a DNS problem, it may be outside your control and the Windows system may have cached the DNS info.

Check your DNS settings, if they match those of the Windows system then sit tight and wait for your ISP to fix them or use an alternative such as Opendns.

---

### Post by pvoce on 2009-08-05
> **Hobgoblin said:**
> Can you get there by IP address? (ping it from the working Windows system to get the IP).

If so you have a DNS problem, it may be outside your control and the Windows system may have cached the DNS info.

Check your DNS settings, if they match those of the Windows system then sit tight and wait for your ISP to fix them or use an alternative such as Opendns.

Thats weird...I can get the IP form the Windoze box, type it into the browser, and get to FB....still DNS problem?  And thanks for the tip!:)

---

### Post by pvoce on 2009-08-05
Update: OpenDNS seems to have done the trick.  Hopefully everything will stay resident.  Thanks for the help!

---

