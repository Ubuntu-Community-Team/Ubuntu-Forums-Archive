---
title: "Can not resolve host name for sending emails"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by James4 on 2011-04-23
hey there,
I recently bought a VPS with DirecAdmin installed on it. everything works fine but the only problem is I can't send emails from my server.
in DirectAdmin's messaging system I got this message:
> 
Cannot find your hostname using the command '/bin/hostname --fqdn'. Please check this command to ensure it works properly.
If you get the error:
hostname: Name or service not known

Check your /etc/resolv.conf and try setting it to use 127.0.0.1Unable to resolve your hostname, . This will cause major issues when sending email.

Solution:

Create an A record for your hostname (.) in your DNS control panel. Point the hostname to your server's main IP address. Also check /etc/hosts to ensure that the server ip is correctly set. 

and when i use the command 'hostname --fqdn' I get the following error:
> 
hostname: Name or service not known

I posted this question in DirectAdmin's forum but so far no one could help me.
I'm so desperate on this.
any help would be appreciated.

---

