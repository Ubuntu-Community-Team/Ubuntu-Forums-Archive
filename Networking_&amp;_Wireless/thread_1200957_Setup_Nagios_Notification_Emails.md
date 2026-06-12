---
title: "Setup Nagios Notification Emails"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by TheGoat31 on 2009-06-30
Hello All,
     I currently have Ubuntu Desktop 8.04 running Nagios 3.1.0 and have all of my Windows servers, network printers, and firewalls/routers. It is working great bu I followed the directions that Nagios gives to install from their site and installed Mailx and Postfix. I think I setup Postfix correctly to point to my MS Exchange 2003 server. I modified the */usr/local/nagios/etc/objects/commands.cfg* so it points to /usr/bin/mailx. I have restarted and still I do not recieve any notification emails. Does anyone have some good step by step instructions to get nagios to send email notifications through a MS Exchange 2003 server? Thank you.

The Goat

---

### Post by TheGoat31 on 2009-06-30
From the terminal on the Ubuntu Desktop that is running Nagios I sent a test email to my gmail account and to the account I want notifications sent to with the following command:

mailx -s test  [email]example@examplehost.com[/email]
test
<ctrl+d>
<ctrl+d>

I only received the test email on my gmail account not the account that goes through my MS Exchange server.

---

