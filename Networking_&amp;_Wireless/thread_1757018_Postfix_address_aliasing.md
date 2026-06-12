---
title: "Postfix address aliasing"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by ash_n on 2011-05-13
Hi there,

I've set aliases in /etc/aliases and am able to receive mail fine according to these aliases. However I need to send mail using these aliases too. I have a user <user> with email address <user>@<domain>.com. I need to be able to send email as <firstname>.<lastname>@<domain>.com.

I've updated /etc/postfix/main.cf with the following line:
```

canonical_maps = hash:/etc/postfix/canonical

```I've then created the file /etc/postfix/canonical which contains the following:
```

<firstname>.<lastname> <user>

```FInally, I executed the following:
```

postmap /etc/postfix/canonical

```....which produced the file /etc/postfix/canonical.db

After restarting postfix, I tried sending an email using:
```

echo "Testing" | mailx -s "Test" <some_external_email_address>

```But the 'From' field of the email I receive in <some_external_email_address> reads <user>@<domain>.com. I need it to read <firstname>.<lastname>@<domain>.com

Please help. What am I doing wrong?

Ash

---

### Post by ash_n on 2011-05-13
SOLVED

Changed the entry in /etc/postfix/canonical to:
```

<user> <firstname>.<lastname>@<domain>.com

```

---

