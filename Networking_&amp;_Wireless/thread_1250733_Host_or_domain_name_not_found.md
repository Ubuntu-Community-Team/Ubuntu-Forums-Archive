---
title: "Host or domain name not found"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by peaky69 on 2009-08-26
Hi all,
I'm relatively new to Ubuntu.  I have installed and set it up to run a mail relay server for our web environment.  I am having some problem with this where email is iniitally deferred before being sent.  The following is from the mail.log:
Aug 27 11:45:59 relay2 postfix/cleanup[3277]: 414E328E37F: message-id=<[EMAIL="APP7fEFzotSkrpEwwSm00003906@APP7.website.wishlist.com.au"]APP7fEFzotSkrpEwwSm00003906@APP7.website.wishlist.com.au[/EMAIL]>
Aug 27 11:45:59 relay2 postfix/qmgr[2606]: 414E328E37F: from=<[EMAIL="service@wishlist.com.au"]service@wishlist.com.au[/EMAIL]>, size=958, nrcpt=1 (queue active)
Aug 27 11:45:59 relay2 postfix/smtpd[3273]: disconnect from unknown[192.168.1.132]
Aug 27 11:46:02 relay2 postfix/smtpd[3275]: connect from unknown[192.168.1.132]
Aug 27 11:46:02 relay2 postfix/smtpd[3275]: 2B66C28E39D: client=unknown[192.168.1.132]
Aug 27 11:46:02 relay2 postfix/cleanup[3277]: 2B66C28E39D: message-id=<[EMAIL="APP73olwRhD54wG8nls00003907@APP7.website.wishlist.com.au"]APP73olwRhD54wG8nls00003907@APP7.website.wishlist.com.au[/EMAIL]>
Aug 27 11:46:02 relay2 postfix/qmgr[2606]: 2B66C28E39D: from=<[EMAIL="service@wishlist.com.au"]service@wishlist.com.au[/EMAIL]>, size=5281, nrcpt=1 (queue active)
Aug 27 11:46:02 relay2 postfix/smtpd[3275]: disconnect from unknown[192.168.1.132]
Aug 27 11:46:19 relay2 postfix/smtp[3278]: 414E328E37F: to=<[EMAIL="alex.cimbal@wishlist.com.au"]alex.cimbal@wishlist.com.au[/EMAIL]>, relay=none, delay=20, delays=0.03/0.01/20/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=wishlist.com.au type=MX: Host not found, try again)
Aug 27 11:46:22 relay2 postfix/smtp[3279]: 2B66C28E39D: to=<[EMAIL="ahendy@hendyhr.com.au"]ahendy@hendyhr.com.au[/EMAIL]>, relay=none, delay=20, delays=0.03/0.01/20/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=hendyhr.com.au type=MX: Host not found, try again)
Aug 27 11:52:09 relay2 postfix/qmgr[2606]: 2B66C28E39D: from=<[EMAIL="service@wishlist.com.au"]service@wishlist.com.au[/EMAIL]>, size=5281, nrcpt=1 (queue active)
Aug 27 11:52:09 relay2 postfix/qmgr[2606]: 414E328E37F: from=<[EMAIL="service@wishlist.com.au"]service@wishlist.com.au[/EMAIL]>, size=958, nrcpt=1 (queue active)
Aug 27 11:52:09 relay2 postfix/smtp[3384]: 2B66C28E39D: to=<[EMAIL="ahendy@hendyhr.com.au"]ahendy@hendyhr.com.au[/EMAIL]>, relay=mail.day3hosting.com[202.0.155.143]:25, delay=367, delays=367/0.01/0.05/0.39, dsn=2.0.0, status=sent (250 ok 1251337800 qp 23356)
Aug 27 11:52:09 relay2 postfix/qmgr[2606]: 2B66C28E39D: removed
Aug 27 11:52:10 relay2 postfix/smtp[3385]: 414E328E37F: to=<[EMAIL="alex.cimbal@wishlist.com.au"]alex.cimbal@wishlist.com.au[/EMAIL]>, relay=mail.wishlist.com.au[203.89.210.75]:25, delay=371, delays=370/0.01/0.27/0.6, dsn=2.0.0, status=sent (250 Requested mail action okay, completed)
Aug 27 11:52:10 relay2 postfix/qmgr[2606]: 414E328E37F: removed

 
There were no changes made in any way between the delay and the successful send.
In addtion when the initial delay occurred I ran an nslookup on both receipient domains, the first time they both timed out but the second time they responded immediately.
 
We are using Postfix for email and our Ubuntu version is 9.04.
 
Anyone with any ideas.

---

