---
title: "LDAP Authentication"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by Sanguinor on 2009-10-08
Hi there,

Having trawled the net for the past few hours looking for a solution to my problems I have given up and resorted to asking.

Here's the situation, I have a LAMP (Ubuntu server 9.04) sitting here with Moodle installed and working on it, I wish to authenticate Moodle of our Active Directory server here so that I can allow the users to logon without having a different username and password.

Seems simple enough, unfortunately there is a big but here.

It needs to run VIA secure LDAP and it needs to use a certificate to authenticate itself.


Now, I know that it all works because not only have I had the server running VIA LDAP I have also had it running through secure LDAP just without the certificate.  All my settings for the LDAP are right, in fact it works.  I just can't work out how to get it to work with a certificate.

Now before people start dropping guides on me or telling me to go and look at the moodle forums this isn't a moodle issue, this is a networking problem that I need help with.


Our AD has certificate services installed and running, I'm not sure what I could be missing.

Please help.

---

### Post by kreggz on 2009-10-10
What makes you think this is a network issue? 

By a network issue I would say:

Can you ping the domain controller's IP?
Can you ping the domain controller's DNS name?
Are ports open?
Can connect to the open port?
Are you querying the right OU's etc?

---

