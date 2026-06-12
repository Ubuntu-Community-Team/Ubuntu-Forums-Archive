---
title: "Postfix Dovecot newbie woes"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by silas2 on 2013-01-11
[FONT=Calibri][SIZE=3]Ubuntu 11.04[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I'm a real mailserver newbie and I'm meddling with things I don't understand…but I installed postfix then dovecot pretty well following [/SIZE][/FONT][[FONT=Calibri][SIZE=3]https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto[/SIZE][/FONT]]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto")
[FONT=Calibri][SIZE=3]to the letter, (in addition I ran [/SIZE][COLOR=#333333][FONT=AnonymousRegular]apt-get install mail-stack-delivery + [/FONT][/COLOR][/FONT][FONT=Courier New]apt-get install sasl2-bin, not mentioned but…)[/FONT]
[SIZE=3][FONT=Calibri]But I get SASL auth failures with mutt -f pop://mail.xyz.com, and when I run telnet xyz.com 25 and EHLO there is no AUTH entries returned but the server says the sasl is running??[/FONT][/SIZE]

---

### Post by silas2 on 2013-01-11
just got a bit further by cleaning up the postfix main.cf, i can now get a AUTH back from the Telnet EHLO, but I'm only getting CRAM-MD5. no PLAIN, I'm afriad i don't event know if this setting is coming from the postfix or the dovecot anyone?

---

