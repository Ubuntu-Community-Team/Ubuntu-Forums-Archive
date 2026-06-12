---
title: "dsniff not catching IMAP passwords"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by fmmarzoa on 2012-05-29
Hi there,

I have forgot a password for one of my IMAP accounts. Fortunatly, I have that password stored on Thunderbird, but I need to access to the account from other email client.

I used to use SSL/TSL as connection security, so I disabled it and set to None on Thunderbird account so the login/password are sent in play text. In fact, changing this parameter makes also "Authentication method" change into "Password, transmitted insecurely".

Now, I have put dsniff on a terminal so it can sniff the password, but it does not do it.

$ sudo dsniff -i wlan0

No output it showed at all. To do a test, I have try with another POP3 account that I have, and it did it right. So I think the problem is with the IMAP protocol

Any hints?

Thanks a lot in advance,

---

### Post by fmmarzoa on 2012-05-29
Doing some checking with Wireshark, I have found that while imap communication starts in plain text, Thunderbird is changing to imaps cause a request of the IMAP host. 

Is there anyway to force Thunderbird not to do that?

TIA

---

### Post by fmmarzoa on 2012-05-29
I managed to found another manner of recovering password for thunderbird:

[http://www.ghacks.net/2010/09/26/recover-or-change-thunderbird-passwords/](http://www.ghacks.net/2010/09/26/recover-or-change-thunderbird-passwords/)

It is a bit outdated, since now you should go to Edit/Preferences in the first step, but appart from this it is right.

Anyway could be useful to know why Thunderbird uses secure imap connection even when instructed to do not so.

---

