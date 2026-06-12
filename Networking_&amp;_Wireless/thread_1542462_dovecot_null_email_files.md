---
title: "dovecot null email files"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by faun77 on 2010-07-30
I have dovecot and /etc/procmailrc
some users in group aliasses 
deliver empty email
group have 7 user
for exapmle 5 users take mails
2 users take empty mail is empty file in Maildir/cur
in logs
this email is deliver to user command:
relay=local, delay=0.58, delays=0.05/0.06/0/0.48, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
in procmail.log
is deliver to Maildir
but files is null

---

