---
title: "About several domains pointing at one server"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by Hioushi on 2011-02-27
Greetings,

I'll post an scenario and hopefully you can help me understand the concept and put me in the right track and do what I intend, if possible. 

Let's say I have a dedicated server with 2 static IPs each with an associated domain, let's call them [www.site1.com](www.site1.com) and [www.site2.com](www.site2.com). Now, apache is running on it, I'd like to redirect anyone coming from site1.com to /home/site1/public_html and anyone coming from site2.com to /home/site2/public_html.

In short, apache serving 2 entire roots depending on the accessed IP/domain. Whether the sites root are in the same parent folder, such as /home/site/site1_public_html and /home/site/site2_public_html or like above doesn't really matter, as long as it works.

Additionally, do something similar with Postfix, so that I can have it running imap/smtp for [email]foobar@site1.com[/email] and [email]foobar@site2.com[/email] on the same server.

At this moment, both apache and postfix are working, and we host only [www.site1.com](www.site1.com) with the respective [email]foobar@site1.com[/email]. But I'm not sure how to proceed or even if it's possible to achieve the above solution.

Thank you for your help.

---

### Post by Hioushi on 2011-02-27
Never mind, I just learned about virtual hosts for apache and postfix, I'll work on that.

---

