---
title: "Joomla! Mail Settings Problem"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by LeMarque on 2009-03-04
I'm desperate and hope someone is willing to stay with me on this till I can get it resolved.

I am hosting a Joomla! site on my Hybrid VPS for a small community based non-profit wireless ISP. Everything works fine, except ...

We are trying to get their mail server configured to that when, in the backend of J! we have Global Configuration >> Server >> Mail Settings - set to SMTP Server to use their Mail Server (postfix) becasue everything else we've tried results in some sort of HELO problem and I get blacklisted on [http://cbl.abuseat.org](http://cbl.abuseat.org)

When they configure the above to use their mail server and try a test registration after adding my IP to the list of mynetworks in the /etc/postfix/main.cf file, the result is:

Mar  4 08:20:32 smtp postfix/smtpd[11446]: connect from secure.xxxxxxdata.net[67.22x.xx.x]
Mar  4 08:20:32 smtp postfix/smtpd[11446]: lost connection after RSET from secure.xxxxxxdata.net[67.22x.xx.x]
Mar  4 08:20:32 smtp postfix/smtpd[11446]: disconnect from secure.xxxxxxdata.nett[67.22x.xx.x]

Without the entry in main.cf the result is:

Mar  3 09:40:04 smtp postfix/smtpd[6643]: connect from secure.xxxxxxdata.net[67.22x.xx.x]
Mar  3 09:40:04 smtp postfix/smtpd[6643]: NOQUEUE: reject: RCPT from secure.xxxxxxdata.net[67.22x.xx.x]: 554 <mike@xxxxx.com>: Relay access denied; from=<info@xxxx.net> to=<mike@xxxx.com> proto=ESMTP helo=<67.2x.xx.x>
Mar  3 09:40:04 smtp postfix/smtpd[6643]: lost connection after RSET from secure.xxxxxxdata.net[67.22x.xx.x]
Mar  3 09:40:04 smtp postfix/smtpd[6643]: disconnect from secure.xxxxxxdata.net[67.22x.xx.x]

As I said I'm desperate and ANY help is very much appreciated.

---

### Post by lisati on 2010-02-09
This is an old post, I am aware. The error messages mean that someone else is trying to connect to the OPs computer to send mail through it, but the connections are being blocked. Disabling relay access through your own server will help correct this.

---

