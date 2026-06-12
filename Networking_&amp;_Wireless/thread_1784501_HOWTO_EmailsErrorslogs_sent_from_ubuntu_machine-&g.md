---
title: "HOWTO: Emails/Errors/logs sent from ubuntu machine-&gt;your email address"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by tigerstripedcat on 2011-06-17
**_Problem_**
Ubuntu will generate mail messages for users once you start installing any services (apache, backuppc, mysql) and perhaps even if you don't and these messages will fall on deaf ears if you aren't there to view them since the system isn't mailing you at your email address, it's mailing various users (root, cron, etc) on your machine to local mailboxes.

**_Solution_**
Gmail has an easily accessible SMTP server that can be used to forward (relay) messages to your email address and you don't even have to install an SMTP server.

**_Resources_**
This info has been taken from the following: 
[http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/](http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/)
[http://www.debian-administration.org/articles/604](http://www.debian-administration.org/articles/604)
The first is the major source for this guide and much of it was taken verbatim.


**_Steps_**

**1) Create a Certificate Authority:**
```

cd
/usr/lib/ssl/misc/CA.pl -newca

```

Enter a pass phrase
Verify the pass phrase
Enter *and remember* the following information (you'll need it later): Country Name, State, Locality, Organization, Unity, Common Name, Email Address
Enter extra attributes

**2) Create a Server Certificate**
This is just an example.  You'll need to replace the info above with the example below.
```

openssl req -new -nodes -subj '/CN=domain.com/O=[COLOR="red"]Sanborn_Widgets[/COLOR]/C=[COLOR="red"]US[/COLOR]/ST=[COLOR="Red"]New York[/COLOR]/L=[COLOR="red"]New York[/COLOR]/emailAddress=[COLOR="red"]username@gmail.com[/COLOR]' -keyout FOO-key.pem -out FOO-req.pem -days 3650

```

**3) Sign the Certificate**
```

openssl ca -out FOO-cert.pem -infiles FOO-req.pem

```
Enter the pass you used above
Press y for anything else it asks.

**4) Copy the certificates to the Postfix folder**
```

cp demoCA/cacert.pem FOO-key.pem FOO-cert.pem /etc/postfix
chmod 644 /etc/postfix/FOO-cert.pem /etc/postfix/cacert.pem
chmod 400 /etc/postfix/FOO-key.pem

```

**5) Add the gmail Thawte Premium Server CA to the end of /etc/postfix/cacert.pem**
```

cd
wget https://www.thawte.com/roots/thawte_Premium_Server_CA.pem
sudo cat thawte_Premium_Server_CA.pem >> /etc/postfix/cacert.pem

```

**6) Append the following to the bottom of /etc/postfix/main.cf**
```

## TLS Settings
#
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
#
## SASL Settings
# This is going in to THIS server
smtpd_sasl_auth_enable = no
# We need this
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtpd_sasl_local_domain = $myhostname
smtp_sasl_security_options = noanonymous
#smtp_sasl_security_options =
smtp_sasl_tls_security_options = noanonymous
smtpd_sasl_application_name = smtpd

#to forward all mail through a single user
smtp_generic_maps = hash:/etc/postfix/generic

```

**7) Create the transport file /etc/postfix/transport which contains the following:**
```

gmail.com smtp:[smtp.gmail.com]:587

```

**8 ) Create the SASL password file /etc/postfix/sasl_passwd which contains the following:**
```

[smtp.gmail.com]:587 username@gmail.com:password

```
make sure you replace "password" with your actual gmail password

**9) Lock this file down as it is in plain text:**
```

sudo chown root:root /etc/postfix/sasl_passwd
sudo chmod 600 /etc/postfix/sasl_passwd

```

**10) Create a generic forwarding address:**
```

root@localhost            <email>
root@                     <email>
root@localdomain.local    <email>
<user>@localhost          <email>
<user>@                   <email>
<user>@localdomain.local  <email>

```
The above is just an example. <user> is the user you usually log in as and <email> is the email address you want your logs/errors to be forwarded to. 


**11) Final setup**
```

sudo postmap /etc/postfix/sasl_passwd
sudo postmap /etc/postfix/transport
sudo postmap /etc/postfix/generic
sudo service postfix restart

```

**12) Test**
```

echo "this is a test" | mail -s "test1" <email>
sendmail -bv <email>

```

<email> here is any address that you want to send test messages to.  The first line just shows you that your user can send emails to any address from the command line.  The second line is an auto generated message that mimics what a script/log may use to send email to a local user which should be forwarded to your email address.  

If you have trouble the cause is probably

1) You need your /etc/postfix/generic file to properly forward addresses that were destened for local address only. 
2) The /etc/postfix/generic file my depend on what your hostname is (/etc/hosts).  
3) The log file will be your best friend.  If you're having problems run:
```

tail -f /var/log/mail.log

```
rerun step 11 above and read the logs.

Sorry if a lot of this is obvious or poorly worded, I did this quick but I was sick and tired of not having instructions for Postfix as you would think every user would like emails if their computer is behaving badly.

TSC

---

