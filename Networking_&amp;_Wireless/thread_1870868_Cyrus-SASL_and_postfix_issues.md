---
title: "Cyrus-SASL and postfix issues"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by ZaphoidPA on 2011-10-28
Hi. 

I am trying to setup Auth SMTP with postfix and cyrus-SASL. I have, I believe setup SASL correctly, and testsaslauthd -u user -p password responds with "OK". I am running SASL in rimap mode against a remote IMAP server. 

Attempts to connect through to the SMTP daemon result in authentication failures, and the following log messages:

Oct 27 22:17:32 computer postfix/smtpd[30787]: warning: SASL authentication failure: Password verification failed
Oct 27 22:17:32 computer postfix/smtpd[30787]: warning: unknown[192.168.0.34]: SASL PLAIN authentication failed: generic failure
Oct 27 22:17:34 computer postfix/smtpd[30787]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory

Any thoughts on where I should be looking? I have googled high and low, and have not come up with any answers. 

I am running Ubuntu Server 10.4. 

Thanks,
Richard.

---

