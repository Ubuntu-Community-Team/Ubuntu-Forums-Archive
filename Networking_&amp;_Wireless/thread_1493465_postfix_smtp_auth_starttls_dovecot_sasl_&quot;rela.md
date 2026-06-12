---
title: "postfix smtp auth starttls dovecot sasl &quot;relay access denied&quot;"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by greybeard95a on 2010-05-25
I'm not finding anything helpful on this.  First, my Postfix configuration on my Linode running Debian Lenny:


atlanta# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
home_mailbox = Maildir/
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 10485760
mydestination = parts-unknown.org, greybeard95a.com, sftaxi.org, cybernude.org, disunitedstates.org, li67-79.members.linode.com, localhost.members.linode.com, localhost
mydomain = parts-unknown.org
myhostname = mail.parts-unknown.org
mynetworks = 127.0.0.0/8
myorigin = parts-unknown.org
owner_request_special = no
recipient_delimiter = +
relay_recipient_maps = hash:/etc/postfix/relay_recipients
relayhost = 
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_client_connection_count_limit = 10
smtpd_client_connection_rate_limit = 10
smtpd_client_new_tls_session_rate_limit = 5
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_error_sleep_time = 0
smtpd_helo_required = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,        permit_mynetworks,        reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = $smtpd_sasl_security_options
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = check_sender_access hash:/etc/postfix/sender_access, reject_non_fqdn_sender, reject_unknown_sender_domain
smtpd_tls_CAfile = /etc/ssl/certs/cacert.org.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/parts-unknown.org.pem
smtpd_tls_key_file = /etc/postfix/ssl/private.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_alias_maps = hash:/etc/postfix/virtual

Second, my postfix configuration on my laptop running Ubuntu Lucid:


graton root /home/benfell # postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = 127.0.0.1, [::1]
inet_protocols = all
mailbox_command = 
mailbox_size_limit = 0
mydestination = graton.parts-unknown.org, graton, localhost.localdomain, localhost
myhostname = graton.parts-unknown.org
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = mail.parts-unknown.org
smtp_bind_address = 0.0.0.0
smtp_bind_address6 = ::
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = encrypt
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

Third, since switching to a configuration which is intended to require TLS, because I really don't want to send a password in clear text, it seems no longer possible in an openssl session to authorize.  The command I'm trying is:

graton benfell /home/benfell % openssl s_client -connect mail.parts-unknown.org:587 -starttls smtp
CONNECTED(00000003)
depth=1 /O=Root CA/OU=http://www.cacert.org/CN=CA Cert Signing Authority/emailAddress=support@cacert.org
verify error:num=19:self signed certificate in certificate chain
verify return:0
---
Certificate chain
 0 s:/CN=www.parts-unknown.org
   i:/O=Root CA/OU=http://www.cacert.org/CN=CA Cert Signing Authority/emailAddress=support@cacert.org
 1 s:/O=Root CA/OU=http://www.cacert.org/CN=CA Cert Signing Authority/emailAddress=support@cacert.org
   i:/O=Root CA/OU=http://www.cacert.org/CN=CA Cert Signing Authority/emailAddress=support@cacert.org
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFoDCCA4igAwIBAgIDCJ7UMA0GCSqGSIb3DQEBBQUAMHkxEDAOBgNVBAoTB1Jv
b3QgQ0ExHjAcBgNVBAsTFWh0dHA6Ly93d3cuY2FjZXJ0Lm9yZzEiMCAGA1UEAxMZ
Q0EgQ2VydCBTaWduaW5nIEF1dGhvcml0eTEhMB8GCSqGSIb3DQEJARYSc3VwcG9y
dEBjYWNlcnQub3JnMB4XDTEwMDUxMDAxNTIzMloXDTEwMTEwNjAxNTIzMlowIDEe
MBwGA1UEAxMVd3d3LnBhcnRzLXVua25vd24ub3JnMIIBIjANBgkqhkiG9w0BAQEF
AAOCAQ8AMIIBCgKCAQEAxIcyXqDNvVtyUgDVpKak7WuT52wlRQELEKw6jjhDqAur
f2NXGxmaPjPx/0IXE04hNeU0qZr2by1oXy01eO8wtb5BvzKecLppuHuqusMCWVOg
FKikYJsmyrJNAGkr+zAZq2HTC0T4kc4LALjCBoZhMEiZcECGCH5PS9UU8DOVxt8x
vDvnDHnCOSLWTvNuJpvgigFeDFjMliXXBn8eS6x7EsoIfgiJYTRJrg/W7m6tTtnL
yVxhbnqEc/mIa1/Z3XklWcVLX0xioremfCR9xntY0/fUPIyWwvVMo+q4Cdqav/Nk
4i9BY1Jo6Kf5envhVOWv2eApWtSEcLZgrb2iMow3sQIDAQABo4IBiDCCAYQwDAYD
VR0TAQH/BAIwADA0BgNVHSUELTArBggrBgEFBQcDAgYIKwYBBQUHAwEGCWCGSAGG
+EIEAQYKKwYBBAGCNwoDAzALBgNVHQ8EBAMCBaAwMwYIKwYBBQUHAQEEJzAlMCMG
CCsGAQUFBzABhhdodHRwOi8vb2NzcC5jYWNlcnQub3JnLzCB+wYDVR0RBIHzMIHw
ghV3d3cucGFydHMtdW5rbm93bi5vcmegIwYIKwYBBQUHCAWgFwwVd3d3LnBhcnRz
LXVua25vd24ub3JnghFwYXJ0cy11bmtub3duLm9yZ6AfBggrBgEFBQcIBaATDBFw
YXJ0cy11bmtub3duLm9yZ4IYb3BlbmlkLnBhcnRzLXVua25vd24ub3JnoCYGCCsG
AQUFBwgFoBoMGG9wZW5pZC5wYXJ0cy11bmtub3duLm9yZ4IWd3d3Mi5wYXJ0cy11
bmtub3duLm9yZ6AkBggrBgEFBQcIBaAYDBZ3d3cyLnBhcnRzLXVua25vd24ub3Jn
MA0GCSqGSIb3DQEBBQUAA4ICAQCwZoSvbN2Hpa2dznF6twPIUeM1HPD6N+yDKnJl
XTgg/u5yFrO6v6hBwJV5KkgwblSO3V5cE4fbG4nCPmju3ATq6+G06JY5+GIiCFeG
dYdykCMXvZc0fudS2aAuxk/K+Q8cdP6mhFMI4fZBmstgzi5fiKxDgYkXdKUSXF4h
azgVMgZvDNgpQ43t32kmDcdcr2Am1DJ2sLc/OeHgmCUBrtGlaY4z31V9jd1v4C0j
6cWnkmyV1jSHBE5J/IjsYYbVRoZ8a620xsJDXd4ea9PAu7bo98Szt4hgWEm8jXcR
JQmSlSU5f0O+mW/MRQpttlPoceip4iKraRF7peMsVBz216bsn/kJdwGir5v6NtQk
re0u+MJnoDKXr2DeILYd08TUNVQ8Xf4gxWR2tbU0B3thUQDZFRS8N4Q+0b39/WBW
ceOskv63ff29fcXKMEnmlU3x24A12AsC+VYF4+tIukknL4aIAEA1B5wcekRMipl7
BhhWZbG8pyKbcBFh7HbLkoEtjuTXKnS1irx/IRS3Jm5J8V+HRV773yLau4XMbWD/
/GPG13jWwYmSU64+MWodXLJb69wGF2jgkNhlvwe/8i/Jd/UbGLUAMNAG46FhC7w8
GaM+/AtHuR8nGoJSlXbv2M9xDbkRSAd3YURrblgwARkBYSYEf8ARwKCrM9vjZmLu
ec6UYg==
-----END CERTIFICATE-----
subject=/CN=www.parts-unknown.org
issuer=/O=Root CA/OU=http://www.cacert.org/CN=CA Cert Signing Authority/emailAddress=support@cacert.org
---
No client certificate CA names sent
---
SSL handshake has read 4226 bytes and written 351 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 2048 bit
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: 5966ABEAABC342DEEF572FEA94815CDAA60285A1BED21AECB8CF87928AC6E30D
    Session-ID-ctx: 
    Master-Key: 693E562244847147C6F660FFF62ECEF6ACB726393F64E5205F1335126D38EFA64FDE38C57974262E85DE908F93AB521D
    Key-Arg   : None
    Start Time: 1274839332
    Timeout   : 300 (sec)
    Verify return code: 19 (self signed certificate in certificate chain)
---
250 DSN
ehlo graton.parts-unknown.org
250-mail.parts-unknown.org
250-PIPELINING
250-SIZE 10485760
250-VRFY
250-ETRN
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
auth plain ***
535 5.7.8 Error: authentication failed: 
auth plain ***
535 5.7.8 Error: authentication failed: 
quit
221 2.0.0 Bye
read:errno=0

This is with two different versions of the mime-encoding based on two different sets of instructions.  It wasn't that way before, though I still had the same "relay access denied" problem when trying to actually send mail:

graton benfell /home/benfell % telnet mail.parts-unknown.org 25 
Trying 74.207.225.79... 
Connected to mail.parts-unknown.org. 
Escape character is '^]'. 
220 mail.parts-unknown.org ESMTP Postfix (Debian/GNU) 
ehlo graton.parts-unknown.org 
250-mail.parts-unknown.org 
250-PIPELINING 
250-SIZE 10485760 
250-VRFY 
250-ETRN 
250-STARTTLS 
250-AUTH PLAIN LOGIN 
250-AUTH=PLAIN LOGIN 
250-ENHANCEDSTATUSCODES 
250-8BITMIME 
250 DSN 
mail from: benfell 
250 2.1.0 Ok 
rcpt to: [email]dbenfell@gmail.com[/email] 
554 5.7.1 <dbenfell@gmail.com>: Relay access denied 
auth plain *** 
235 2.7.0 Authentication successful 
rcpt to: [email]dbenfell@gmail.com[/email] 
250 2.1.5 Ok 
quit 
221 2.0.0 Bye 
Connection closed by foreign host. 

But I have consistently gotten the same error in my logs when ever I have attempted to actually send mail: "relay access denied."  A Google search has led me so many places I suspect I no longer know which way is up.  And all without success.

It's supposed to just work.  And of course it doesn't just work.  I don't know what to do.  My local security expert says to set up a VPN instead which would be nice but of course that doesn't work as documented either.

I'd really like to be able to send mail.  Any ideas?

---

