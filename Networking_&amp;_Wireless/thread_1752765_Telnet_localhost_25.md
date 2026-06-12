---
title: "Telnet localhost 25"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by ash_n on 2011-05-08
First of all, Hi. Finally got around to registering for the forums. Just never had any problems with this beautiful OS.

So here's my problem (I know this issue has been raised before and I've been through those posts in the forums but either they were left un-resolved or they were slightly different).

Im trying to set up a mail server using postfix on my VPS. I followed the following tutorial pretty much doing exactly what it asked, with the only exception being that I'm not using procmail.
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

After configuring the /etc/postfix/main.cf file, I tried telneting (telnet localhost 25) to find something strange. Sendmail was still listening on port 25. I thought installing postfix was meant to remove sendmail as only one MTA could exist at a time. Anyway, I stopped sendmail and restarted postfix and tried telneting again.

However, now I'm getting the following error:
```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
Connection closed by foreign host.

```I did netstat and smtp is listening on port 25.

Here is the output of my last telnet attempt in /var/log/mail.log:
```

May  8 15:19:45 mail postfix/smtpd[20421]: connect from localhost.localdomain[12
7.0.0.1]
May  8 15:19:45 mail postfix/smtpd[20421]: warning: xsasl_cyrus_server_get_mecha
nism_list: no applicable SASL mechanisms
May  8 15:19:45 mail postfix/smtpd[20421]: fatal: no SASL authentication mechani
sms
May  8 15:19:46 mail postfix/master[17621]: warning: process /usr/lib/postfix/sm
tpd pid 20421 exit status 1
May  8 15:19:46 mail postfix/master[17621]: warning: /usr/lib/postfix/smtpd: bad
 command startup -- throttling

```Thanks in advance

---

