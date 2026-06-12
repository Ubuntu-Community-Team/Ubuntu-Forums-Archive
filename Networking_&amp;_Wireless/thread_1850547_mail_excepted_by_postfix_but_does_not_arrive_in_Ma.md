---
title: "mail excepted by postfix but does not arrive in Maildir mailbox"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by laurieturpin on 2011-09-26
Hello, 

I have two pcs that I'm using as a server and a desktop network. The following site shows a diagram of the setup.
[https://sites.google.com/site/laurieswebpages/home?pli=1](https://sites.google.com/site/laurieswebpages/home?pli=1)
There is a dlink router that creates my domain which is dlink.com 192.168.1.1
A server running Ubuntu server 11.04 
server1 192.168.1.2
A desktop running Ubuntu desktop 11.04 duel booted with Windows 7
client1 192.168.1.3
My problem is I am trying to get email server running according to the instructions at the following website:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

I have got to the point where I'm trying to do the following:

netcat server1.dlink.com 25
ehlo dlink.com
mail from: [email]root@server1.dlink.com[/email]
rcpt to: [email]fmaster@server1.dlink.com[/email]
data
Subject: My first mail to my domain

Hi,
Are you there?
regards,
Admin
.
quit

This seems to go ok, but when I do the next bit which is:

su - fmaster
cd Maildir/new
ls

There is nothing in the new folder?  //This is the problem

The mail has not arrived.

Also I cannot set the enviroment variable MAIL
By default it is set to:
MAIL=/var/mail/fmaster

If I try to set it to set it to
/home/fmaster/Maildir

It sets itself back to the default even if I do the following
MAIL=/home/fmaster/Maildir; export MAIL

Below is my main.cf file 

Thanking you in anticipation



# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = dlink.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mydomain = dlink.com
myhostname = server1
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = server1.dlink.com, localhost.dlink.com, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 192.168.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
home_mail = Maildir/
home_mailbox = Maildir/
mailbox_command = 
inet_protocols = all

---

### Post by laurieturpin on 2011-09-27
Hello again,
I have gone back and re-installed the whole server and set up the network again. I have reinstalled the email server again following the instructions from the following web page:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

This time I got a little big further because although it is still not receiving the mail in the following folder:

/home/fmaster/Maildir/new

I have received something in:

/home/fmaster/Maildir/tmp

so that ls:

 ls /home/fmaster/Maildir/tmp
 1317135860.Vfb0011402b4M398027.server1.dlink.com:2,s

Does that mean anthing to anyone?
Can anyone make any suggestions would more info help?
I'm really stuck

Thanking you in anticipation

---

### Post by gombadi on 2011-09-27
In Linux most servers produce logs that are stored in /var/log. Have a look in the files in that directory and postfix may be telling you what the problem is.

Some files to look at are syslog and any of the mail.* files

---

### Post by laurieturpin on 2011-09-28
Thank you for your reply gombadi. It now seems to be working I think the original problem was a combination of things.
I had some ssl packages and had not got ssl setup correctly. I have now left those uninstalled.

Also because the home router sets the domain to dlink.com I have to make sure the mail does try and go over the internet to the company called dlink. If that happens the mail gets rejected and distroyed. I got over this by never using just dlink.com so that [email]root@dlink.com[/email] won't work it has to be [email]root@server1.dlink.com[/email].

I suppose there must be some way of stopping mail trying to go dlink.com(the company) So in that sense I still have problem. Does anyone have any suggestions about that?

regards:D

---

