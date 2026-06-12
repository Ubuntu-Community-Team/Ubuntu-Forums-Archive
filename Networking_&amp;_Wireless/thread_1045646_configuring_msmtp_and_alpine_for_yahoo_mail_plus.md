---
title: "configuring msmtp and alpine for yahoo mail plus"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by doctordruidphd on 2009-01-20
Hello,
I am trying to get alpine to work for receiving and sending mail through my yahoo account. mpop works beautifully, but I cannot get msmtp to work. I suspect problems with both alpine and msmtp configuration.
One problem is that alpine insists on sticking my machine name into the mail address, which won't work. I haven't figured out how to stop this.
Second, I can't get msmtp to send. Well, maybe it does -- if I try sending a file from the command line to my email address, I get a blank message. 
Note also: my yahoo account name is not the same as my ubuntu user name.
Anyone have this working?

Pasted .mpoprc (sanitized where appropriate)(note this part works):
-------------------
defaults
keep on
tls on
tls_starttls off
tls_trust_file /etc/ssl/certs/Equifax_Secure_Certificate_Authority.cer
only_new on
delivery mda "/usr/bin/procmail -f ’%F’ -d $USER"
account mymailaccount
host pop.mail.yahoo.com
user mymailaccount
password imnotthatdumb
account default : mymailaccount
----------------------

Pasted .msmtprc (doesn't appear to work)(sanitized):
---------------------
defaults
tls on
tls_starttls off
tls_trust_file /etc/ssl/certs/Equifax_Secure_Certificate_Authority.cer
logfile /home/myubuntuusername/msmtplog
syslog on
account yahoo
host plus.smtp.mail.yahoo.com
port 465
auto_from off
from [email]mymailaccount@yahoo.com[/email]
user mymailaccount
password imnotthatdumb

account default : yahoo
---------------------------------

---

### Post by andrew.46 on 2009-02-19
Hi doctordruidphd,

> **doctordruidphd said:**
> 
Pasted .msmtprc (doesn't appear to work)(sanitized):
---------------------
```
defaults
[B][COLOR="Red"]tls on
tls_starttls off
tls_trust_file /etc/ssl/certs/Equifax_Secure_Certificate_Authority.cer[/COLOR][/B]
logfile /home/myubuntuusername/msmtplog
syslog on
account yahoo
host plus.smtp.mail.yahoo.com
port 465
auto_from off
from [email]mymailaccount@yahoo.com[/email]
user mymailaccount
password imnotthatdumb
```


I have no experience with yahoo mail but you could try a different approach for the certs. Install the ca-certs:

```
$ sudo apt-get install openssl ca-certificates
```

and alter the lines I have highlighted in your config to:

```
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
```

I have not tested this with yahoo as I don't have a yahoo account but it might be worth a try. 2 other thoughts:

[LIST=1]
[*]I presume the port number is correct?
[*]What does /home/myubuntuusername/msmtplog show?
[/LIST]


Andrew

---

### Post by doctordruidphd on 2009-02-19
Thanks for your reply. I thought I had closed this, but maybe it didn't post.

I did finally get it to work. The problem was simple. I had not set up the .pinerc file right. The sendmail configuration line should read:

sendmail-path="/usr/bin/msmtp --account=yahoo -f [email]doctordruidphd@yahoo.com[/email] -t"

All I did was leave off the -t, and it didn't work. It took quite a bit of research to find that. 

FYI, I installed the certs manually. That part went fine, 

I also solved the problem of apline sticking my account@hostname in my email address using alpine's "role" capability. See the manual or hit <shift> # at the main menu.

---

