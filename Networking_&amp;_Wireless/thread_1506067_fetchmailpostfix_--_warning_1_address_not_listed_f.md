---
title: "fetchmail/postfix -- warning: ::1: address not listed for hostname localhost"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by Buce on 2010-06-09
I've got an Ubuntu Karmic Server machine with postfix and fetchmail installed on it. I'm getting these warnings in /var/log/mail.warn:

```
Jun  9 21:22:05 hal postfix/smtpd[1861]: warning: ::1: address not listed for hostname localhost
```

The whole postfix + fetchmail thing is set up to be a mailing list. Fetchmail grabs emails off a gmail account, and then delivers them to an alias in /etc/aliases, which contains the mailing list.

I've confirmed that it's ONLY when fetchmail does its thing that the warning pops up. Sending mail from a local account to either another local account or to an external email account doesn't trigger the warning.

Additionally, when I change the the following IPv6 line in /etc/hosts:
```
# from this...
::1     localhost ip6-localhost ip6-loopback

# ...to this
::1     ip6-localhost ip6-loopback

```

...the warning messages stop. However, [this bug]("https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/301430") indicates that removing 'localhost' from the line is incorrect.

Is there any other reason I might be getting the error messages? I'd rather not post any of my config files cuz I don't want to get spammed. If I really need to, though, I can filter them through sed or somesuch to remove all the sensitive info.

---

### Post by Buce on 2010-06-09
Some more info:

Doing a 'telnet localhost 25' also generates the warning.

Here's a sanitized version of my main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = $mydomain
mydomain = asdfjkl.com
myhostname = hal.asdfjkl.com
mydestination = $myhostname, $mydomain, localhost.$mydomain, localhost
mynetworks = 127.0.0.0/8
# Gmail relay
relayhost = [smtp.gmail.com]:587

smtpd_banner = $myhostname $mydomain ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# specifies when the postmaster should be emailed
notify_classes = resource, software, bounce
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# TLS parameters
smtpd_use_tls = yes
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtp_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtp_tls_key_file = /etc/postfix/ssl/smtpd.key
smtp_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_use_tls = yes
smtpd_tls_received_header = yes
#smtpd_tls_mandatory_protocols = SSLv3, TLSv1
#smtpd_tls_mandatory_ciphers = medium
tls_random_source = dev:/dev/urandom
#smtp_tls_security_level = may
#smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtp_tls_loglevel = 1
smtpd_tls_session_cache_timeout = 3600s
smtp_tls_per_site = hash:/etc/postfix/tls_per_site
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_sasl_tls_security_options = noanonymous
smtp_sasl_security_options = noanonymous

# SASL SUPPORT FOR CLIENTS
#
# The following options set parameters needed by Postfix to enable
# Cyrus-SASL support for authentication of mail clients.
#
smtpd_sasl_auth_enable = no
smtpd_sasl_type = cyrus
smtpd_sasl_path = smtpd
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
#smtpd_recipient_restrictions = 
smtpd_sender_restrictions = 
inet_protocols = all

# SASL SUPPORT FOR SERVERS
#
# The following options set parameters needed by Postfix to enable
# Cyrus-SASL support for authentication of mail servers.
#
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd

## Good for testing?
#sender_bcc_maps = hash:/etc/postfix/bcc_table

## Disable DNS lookup?
#disable_dns_lookups = yes

## Address mapping
smtp_generic_maps = hash:/etc/postfix/generic
transport_maps = hash:/etc/postfix/transport
```

---

### Post by Peter Pearson on 2011-02-27
I'm having exactly the problem you describe, and googled my way to this thread.  Did you ever solve the problem?  Please, share.

---

### Post by Buce on 2011-02-27
Gosh. If I ever got this working, I didn't use it for very long. I wish I could dig up the config files referenced in my posts and compare them to see if I changed anything, but I'm afraid I nuked the server they were on to make way for a CentOS installation. Sorry, but I'm afraid I can't help.

---

### Post by Buce on 2011-02-27
Hmm. After thinking about it a bit, I've maybe got a hunch. Could you post your /etc/hosts? Or, if you don't want to put the whole thing out on the net, the output of 'grep localhost /etc/hosts'?

---

### Post by Peter Pearson on 2011-02-27
I don't feel at all private about my /etc/hosts file.
Here it is:

peter@pisaster:~$ cat /etc/hosts
127.0.0.1	pisaster	localhost.localdomain	localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Buce on 2011-02-27
Alright, well I'm not too savvy on the differences between IPv4 and IPv6, and I haven't done much with Ubuntu/Debian systems for awhile, so take the following advice with a grain of salt.

I suspect that postfix is detecting a collision between the two 'localhost' entries in your /etc/hosts. You could try changing the '::1' line to read 'localhost6' instead of 'localhost'. That's similar to the convention that my centos box uses:
```

127.0.0.1   localhost  localhost.localdomain
::1         localhost6 localhost6.localdomain

```

'course, there's no reason to suppose that the 'localhost6' convention won't break something else on ubuntu. If the warnings aren't adversely affecting anything on the system, you might take the "If it ain't broke..." attitude and leave it alone.

---

### Post by Peter Pearson on 2011-02-27
Thanks for your attention and for your suggestions.  I think I'll follow the path of calling it "not broke".

---

### Post by russel_sc on 2011-08-14
Just list ur public IP into the /etc/hosts file like below:

x.x.x.x mail.domain.com mail

---

