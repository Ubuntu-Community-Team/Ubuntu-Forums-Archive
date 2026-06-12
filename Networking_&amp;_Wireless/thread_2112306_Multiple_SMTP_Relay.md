---
title: "Multiple SMTP Relay"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by contertulio on 2013-02-04
Dear friends, I have a VPS with multiple domains hosted. Over time I was a problem with shipping to accounts 'hotmail.com'. The solution I found was to hire an SMTP service to relay e. I had to configure Postfix to have some authentication data for each domain. Here attached configuration for which you can serve:

/etc/postfix/main.cf
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwords
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = may
start_tls = yes
header_size_limit = 4096000
smtp_sender_dependent_authentication = yes
sender_dependent_relayhost_maps = hash:/etc/postfix/sender_relay
relayhost = 

/etc/postfix/sender_relay
@dominio.com [smtp.servidorsmtp.com]:25

/etc/postfix/sasl_passwords
#[smtp.servidorsmtp.com]:25 usuario:clave
@dominio.com usuario:clave

postmap /etc/postfix/sender_relay
postmap hash:/etc/postfix/sasl_passwords
/etc/init.d/postfix restart

This configuration works well for the relay of all emails in each domain. My question now is whether there is a Postfix configuration allowing the relay emails sent only to 'hotmail.com' for each domain. That would solve my problem, because the only emails I am having reception problems are with 'hotmail.com', others are working properly and I can send to my VPS server.

Thank you very much in advance.

---

