---
title: "[SOLVED] HOWTO Configure an e-mail server with Fetchmail/Postfix/Dovecot"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by cirobr on 2008-12-18
**Objective**

To set up a working e-mail server. This configuration is tested on Hardy Server Edition.

Note: Data/password encryption is not addressed by this article. Any hint on how to do it is very welcome.

Core packages:
[LIST]
[*]Fetchmail: e-mail capture from ISP;
[*]Postfix: MTA (email management) and SMTP Server;
[*]Dovecot: POP/IMAP server.
[/LIST]

Before starting, make sure that all packages are installed:
> sudo apt-get install fetchmail postfix dovecot-common dovecot-pop3d dovecot-imapd

[B]Remark: Some files will store ISP user names and passwords. The user is encouraged to change permissions for data protection purposes with command &#8220;chmod&#8221;. A good reference on how to do it is found [here]("http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-navigating-ownership.html").
[/B]
**Creation of Maildir**

Maildir is the folder where the emails captured from the ISP will be stored at the local server. We will add at the server one user for each existing email account. The Maildir folder must be created within the &#8220;home&#8221; folder of each user.

First, we prepare the server so that for every new user added, the Maildir folder is automatically created:

> sudo maildirmake.dovecot /etc/skel/Maildir
sudo maildirmake.dovecot /etc/skel/Maildir/.Drafts
sudo maildirmake.dovecot /etc/skel/Maildir/.Sent
sudo maildirmake.dovecot /etc/skel/Maildir/.Trash
sudo maildirmake.dovecot /etc/skel/Maildir/.Templates

For the already existing users (&#8220;john&#8221;, in the example), creation of Maildir is manual:

> sudo cp -r /etc/skel/Maildir /home/john/
sudo chown -R john:john /home/john/Maildir
sudo chmod -R 700 /home/john/Maildir

When creating new users (&#8220;jane&#8221;, in the example), creation of Maildir is automatic. The username and password created here will be used at a later stage by the e-mail client to access the server.

> sudo useradd -d /home/jane -m jane
sudo passwd jane

**Fetchmail**

Edit file /etc/default/fetchmail:

```
# Start daemon operation
START_DAEMON=yes
```

Edit file /etc/fetchmailrc. Note that, on the below code, the names &#8220;john&#8221; and &#8220;jane&#8221; match with the users created on the server.

```
# Read the ISP accounts every 180 seconds
set syslog 
set daemon 180 

# Configure the ISP accounts (POP server, users and respective passwords)
poll pop.sao.terra.com.br with protocol POP3: 
user "johndoe", password "pass1", is john here;
user "janedoe", password "pass2", is jane here
```

Then, protect the passwords by typing on terminal:

> sudo chmod 600 /etc/fetchmailrc

**Postfix**

Edit file /etc/postfix/main.cf. Find out the heading of the below code and make the adjustments as needed. Most likely, these are the changes needed to the original file:

[LIST]
[*]No changes on the file,  above the first two comment lines.
[*]Adapt myhostname (note1-server, on the example) to your needs. Extension &#8220;.local.domain&#8221; shall be preserved.
[*]On &#8220;mynetworks&#8221;, add the network for the localhost (127.0.0.0/8). The local network (192.168.0.0/24, on the example) must reflect the actual private network.
[*]Add all code lines starting from &#8220;smtp_generic_maps&#8221;.
[/LIST]

```
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for

# information on enabling SSL in the smtp client.



#General server configuration

mydomain = local.domain

myhostname = note1-server.$mydomain

alias_maps = hash:/etc/aliases

alias_database = hash:/etc/aliases

myorigin = $mydomain

mydestination = localhost, $myhostname, $mydomain, localhost.$mydomain

#mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

mynetworks = 127.0.0.0/8, 192.168.0.0/24

mailbox_command = 

mailbox_size_limit = 0

recipient_delimiter = +

inet_interfaces = all



smtp_generic_maps = hash:/etc/postfix/generic

home_mailbox = Maildir/



# Postfix configuration to relay e-mail through ISP

relayhost = [smtp.sao.terra.com.br]

smtp_sasl_auth_enable = yes

smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

smtp_sasl_security_options =



# Postfix configuration as SMTP server

smtpd_sasl_type = dovecot

smtpd_sasl_path = private/auth-client

smtpd_sasl_local_domain =

smtpd_sasl_security_options = noanonymous

broken_sasl_auth_clients = yes

smtpd_sasl_auth_enable = yes

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination



```


Edit file /etc/aliases to:

```
# Indicate who is the root user (probably configured, already)

root:	john
# Indicate who is the postmaster
postmaster:    root 

```
After that, type on terminal:

> sudo newaliases
sudo /etc/init.d/postfix restart

Edit /etc/postfix/generic to:

```
# Correlate the local email addresses of the users with the emails set at the ISP
john@local.domain	johndoe@terra.com.br
jane@local.domain	janedoe@terra.com.br

```
After that, type on terminal:

> postmap /etc/postfix/generic
sudo /etc/init.d/postfix restart


Edit /etc/postfix/sasl_passwd to include ISP's SMTP server address and password.

```
# /etc/postfix/sasl_passwd

[smtp.sao.terra.com.br] yourloginid:yourpassword

```
Then, protect the passwords by typing on terminal:

> sudo chown root:root /etc/postfix/sasl_passwd
sudo chmod 600 /etc/postfix/sasl_passwd
sudo postmap /etc/postfix/sasl_passwd


**Dovecot**

Edit /etc/dovecot/dovecot.conf and make sure the following lines are either uncommented or added:

```
protocols = imap imaps pop3 pop3s
listen = *
mail_location = /home/%u/Maildir
```

Find the below text heading (around line 1001) and change it to reflect exactly as below. Most likely, it is just needed to uncomment the &#8220;client&#8221; portion.

```
  # It's possible to export the authentication interface to other programs:

  socket listen {

    #master {

      # Master socket provides access to userdb information. It's typically

      # used to give Dovecot's local delivery agent access to userdb so it

      # can find mailbox locations.

      #path = /var/run/dovecot/auth-master

      #mode = 0600

      # Default user/group is the one who started dovecot-auth (root)

      #user = 

      #group = 

    #}

    client {

      # The client socket is generally safe to export to everyone. Typical use

      # is to export it to your SMTP server so it can do SMTP AUTH lookups

      # using it.

      #path = /var/run/dovecot/auth-client

      path = /var/spool/postfix/private/auth-client

      mode = 0660

      user = postfix

      group = postfix

    }

   }
```

After that, save and close file, and type on terminal:

> sudo /etc/init.d/dovecot restart

The e-mail server is now ready. E-mail clients can now be reconfigured:
POP/SMTP servers: IP address of the server;
User name and password: same as in Maildir.

**References**

**a)Articles**

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
[https://help.ubuntu.com/community/GmailPostfixFetchmail](https://help.ubuntu.com/community/GmailPostfixFetchmail)
[https://help.ubuntu.com/8.04/serverguide/C/postfix.html](https://help.ubuntu.com/8.04/serverguide/C/postfix.html)
[http://linuxguruz.wordpress.com/2008/09/14/if-you-just-need-an-outgoing-email-from-web-server-use-sendmail-but-what-is-masquerading/](http://linuxguruz.wordpress.com/2008/09/14/if-you-just-need-an-outgoing-email-from-web-server-use-sendmail-but-what-is-masquerading/)
[http://edafe.org/tag/postfix/](http://edafe.org/tag/postfix/)
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)


**b)Manuals**

[http://fetchmail.berlios.de/fetchmail-man.html](http://fetchmail.berlios.de/fetchmail-man.html)
[http://www.postfix.org/BASIC_CONFIGURATION_README.html](http://www.postfix.org/BASIC_CONFIGURATION_README.html)
[http://www.postfix.org/STANDARD_CONFIGURATION_README.html](http://www.postfix.org/STANDARD_CONFIGURATION_README.html)

---

