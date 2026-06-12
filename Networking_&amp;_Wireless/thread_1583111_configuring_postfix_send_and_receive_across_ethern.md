---
title: "configuring postfix send and receive across ethernet"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by cpage13 on 2010-09-27
Hi

I am would like to configure postfix to send and receive email across Ethernet (just for now). I have two machines with postfix installed both using Ubuntu 10.04 directly connected with an ethernet cable. I have successfully configured a machine to send email to gmail, however i have been unsuccessful in having these machines send email back and forth. I have been interested in setting up a little mail server at home and have just been trying some simple projects with postfix to start with. Have had no luck with this one and have now become obsessed with figuring this out. 

at this moment i am using ip addresses and am not concerned with using a dns server

machine A: has a fixed ip of 10.137.202.1, hostname = mail.me.com, 
machine B: has a fixed ip of 10.137.202.20, hostname = mail.ubuntu.com

in the /etc/hosts file I map each hostname to ip address receptively (not sure if a good idea, but at this point I have been trying everything)

So i will execute from Machine B

echo "Here is a message"  |  mail -s 'Hello' cmd@[10.137.202.1]


I currently get  from mail.log timed out while receiving the initial server greeting

I get from mail.err valid hostname or network address required in server description #[10.137.202.1] 

obviously when I run the mail command from cmd user i do not receive anything. I can receive mail from myself if from machine A, I sent an email using the command above

Any guidance or help would greatly be appreciated. I would just like to send email from machine B and receive it on machine A via direct Ethernet connection. I have been through postfix documentation and have also read the postfix definitive guide and have had no luck. 


_______________________________________________________________________________
Here is a recent main.cf that has been butchered as I have tried getting this to work (this is for machine A however, similar for B) 

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.me.com
mydomain = me.com
#smtp_generic_maps = hash:/etc/postfix/generic
#alias_maps = hash:/etc/aliases
#alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 10.137.201.20 $myhostname localhost.$mydomain localhost $mydomain 
#relayhost = smtp.gmail.com:587
mynetworks = 10.137.202.0/24 127.0.0.0/8 #[::ffff:127.0.0.0]/104 [::1]/128
relayhost =
#relaydomain = 
mailbox_size_limit = 0
recipient_delimiter = +
#inet_interfaces = loopback-only
#inet_interfaces = 10.137.202.1 #10.137.202.1 ,127.0.0.1, 
inet_protocols = all

#smtp_sasl_auth_enable = yes
#smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd
#smtp_sasl_security_options = noanonymous

#smtp_use_tls = yes#
#smtp_enforce_tls = yes#
#smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt#

smtp_generic_maps = hash:/etc/postfix/generic


#home_mailbox = Maildir/

smtpd_sasl_auth_enable = no
smtpd_sasl_type = cyrus
smtpd_sasl_path = smtpd
smtpd_sasl_authenticated_header = no
#smtpd_sasl_security_options = noanonymous#
smtpd_sasl_local_domain = 
broken_sasl_auth_clients = no
smtpd_recipient_restrictions = permit_mynetworks#, reject_unauth_destination
smtpd_sender_restrictions = permit_mynetworks
mailbox_command = 
#smtpd_tls_received_header = no #
#smtpd_tls_mandatory_protocols = SSLv3, TLSv1#
#smtpd_tls_mandatory_ciphers = medium#
#smtpd_tls_auth_only = no#
#tls_random_source = dev:/dev/urandom#

---

### Post by SeijiSensei on 2010-09-27
First things first.  Test to make sure your provider isn't blocking port 25 (SMTP) traffic like this:

telnet gmail-smtp-in.l.google.com 25

You should see it reply with:

Trying 74.125.93.27...
Connected to gmail-smtp-in.l.google.com (74.125.93.27).
Escape character is '^]'.
220 mx.google.com ESMTP o8si11391803qcu.148

(To end this session, hold down Ctrl, hit "]" then type "quit" and enter.)

If you don't see that reply, your provider is probably blocking SMTP connections.  You might be able to use port 587 instead.  Otherwise you're stuck using your ISPs mail server for outbound traffic, and that probably won't support mail from domains other than the ISPs own.

Blame all of this on the spammers.  The biggest scourge to mail providers is the rapid profusion of "spambots" running on infected Windows machines across the globe.  ISPs now routinely block outbound port 25 traffic, especially on consumer-grade lines, to help alleviate the spamming problem.

---

### Post by cpage13 on 2010-09-29
thank you for the reply

i will try the telnet test soon. I have noticed that I have had difficulty in forwarding email to gmail.  Spammers have definitely made setting up email more difficult than it needs to be.

before I get that working maybe i should get something more simple working.

In this case. I have two linux (no port blocking, locally)  computers connected directly with an Ethernet cable with static ip addresses,  will it be possible to send mail using postfix from one user (computer) to the next and check the mail in a users mail box?

---

