---
title: "sendmail: were do the queued messages go?"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by berankin99 on 2009-02-09
Hello,

It seems that I have sendmail installed on my machine. (8.10 Desktop)

I tried calling it like "cat email.txt | /usr/sbin/sendmail -t -i", and received no error.

However the message is not delivered.  This is not surprising as even if Sendmail was working OK, my ISP blocks outgoing connections on port 25.

So, I presume I must configure it to use a smarthost, but where do i do that, and where has all the mail I already submitted gone?

Thank you,
:)

Calling just "/usr/sbin/sendmail"

Yields:
 
Exim is a Mail Transfer Agent. It is normally called by Mail User Agents,
not directly from a shell command line. Options and/or arguments control
what it does when called. For a list of options, see the Exim documentation.

---

