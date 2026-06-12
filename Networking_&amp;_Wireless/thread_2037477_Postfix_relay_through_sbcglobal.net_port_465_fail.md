---
title: "Postfix relay through sbcglobal.net port 465 fail"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by JimLS on 2012-08-04
I am trying to get postfix on ubuntu 11.10 to relay sent mail through an sbcglobal.net account on port 465.  (started with sendmail but postfix was recommended).  This is for email from asterisk and perl.  Eventually want to be able to get mail with perl as well but don't think I need any extra software for that - don't want postfix to mess with any incoming mail, at least at this time.

I have tried to get through several guides but they are all slightly different and it is hard to tell what is up to date.  ATT, sbc, yahoo... has changed this over the years.  I was trying to follow this:
[http://fonality.com/trixbox/wiki/howto-voicemail-email-postfix-and-sbc-att-your-isp](http://fonality.com/trixbox/wiki/howto-voicemail-email-postfix-and-sbc-att-your-isp)

I think I have some of the aliases messed up but not sure how...not sure why the above puts aliases in generic file instead of aliases file.

I have looked at the log file but it doesn't make much sense to me.  I tried:
sendmail -bv [EMAIL="secondemail@sbcglobal.net"]secondemail@sbcglobal.net[/EMAIL] and it reports an email sent to my local account but apparently my local account is being sent to sbcglobal (through firstemail but fails) so my system mail doesn't have anything.
My account on ubuntu is jim.  I do not have an email [EMAIL="jim@sbcglobal.net"]jim@sbcglobal.net[/EMAIL] but do have several accounts on sbcglobal.net.  I am trying to use [EMAIL="firstemail@sbcglobal.net"]firstemail@sbcglobal.net[/EMAIL] to send the emails out and only using [EMAIL="secondemail@sbcglobal.net"]secondemail@sbcglobal.net[/EMAIL] as a destination to try sending emails to.  The second one could be any email and, no, 'firstemail' and 'secondemail' aren't the actual addresses - just changed them in this post...
Version of postfix is 2.8.5

I have set up my password file.  I get the following error in the log (among others):
```

Aug  4 07:59:00 Netvista postfix/smtp[4117]: CLIENT wrappermode (port smtps/465) is unimplemented
Aug  4 07:59:00 Netvista postfix/smtp[4117]: instead, send to (port submission/587) with STARTTLS

```/etc/host:
```
127.0.0.1    localhost
127.0.1.1    Netvista Netvista.

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```main.cf
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = Netvista.sbcglobal.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = sbcglobal.net
mydestination = 
relayhost = [smtp.att.yahoo.com]:465
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
#added 
smtp_sasl_password_maps = hash:/etc/postfix/saslpasswd
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = no
smtp_always_send_ehlo = yes
smtp_sasl_auth_enable = yes
smtp_sasl_security_options =
mydomain = sbcglobal.net
masquerade_domains = sbcglobal.net
smtp_generic_maps = hash:/etc/postfix/generic
```/etc/aliasses:
```

#
# Mail aliases for sendmail
#
# You must run newaliases(1) after making changes to this file.
#

# Required aliases
postmaster:    root
MAILER-DAEMON:    postmaster

# Common aliases
abuse:        postmaster
spam:        postmaster

# Other aliases
```

/etc/postfix/generic
```

jim@sbcglobal.net firstemail@sbcglobal.net
jim@Netvista.localhost firstemail@sbcglobal.net

```Host name, domain...
```
jim@Netvista:~$ hostname
Netvista
jim@Netvista:~$ dnsdomainname
jim@Netvista:~$ domainname
(none)
jim@Netvista:~$
```

---

### Post by JimLS on 2012-08-05
Looks like I have two main issues - address substitution and encryption.  Postfix apparently cannot do the connection to att/sbc/yahoo on port 465.  The postfix site shows how to use stunnel to complete the connection. 

[http://www.postfix.org/TLS_README.html#client_smtps](http://www.postfix.org/TLS_README.html#client_smtps)

I will try this.

---

### Post by wooddealer on 2012-08-30
Did you ever solve this problem?  I too am trying to use postfix to relay mail via my ISP (U-verse) and the outbound.att.net:465 server.

Thanks in advance.

---

