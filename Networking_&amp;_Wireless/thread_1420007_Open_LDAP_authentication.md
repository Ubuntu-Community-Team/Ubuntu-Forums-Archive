---
title: "Open LDAP authentication"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by iavellino on 2010-03-02
Hey everyone!

I'm new in the forums, but not new to Ubuntu
I've been searching the forums for how to authenticate Ubuntu against an Open LDAP server, but nothing very helpful has come up for version 9.10

Well, my questions are the following:

1) Can you login to Ubuntu authentication against the LDAP server, in the login screen? (like you do in windows when you login to a domain)


2) I've installed ldap-auth-client and done the configuration, but how do I start the client and authenticate?!

Our server is Open LDAP V2 running samba, so that windows machines can authenticate
We are migrating to Ubuntu and LDAP is a must, so this issue is very important for our Institute

well, thanks in advance and I hope I made my concern clear, I'll explain again if this is not the case

Thanks!!!!

Nacho

---

### Post by HyperionQc on 2010-04-06
I have the same problem: can't login with LDAP.
I tried many thing that I saw. 
These pages looks great 
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
[http://beginlinux.com/server_training/server-managment-topics/1017-ldap-client-on-ubuntu-804](http://beginlinux.com/server_training/server-managment-topics/1017-ldap-client-on-ubuntu-804)
but it doesn't work (well, for me. Maybe I changed too many files everywhere)
Once you get trought the installation (and answer all the questions) I can't figure how to get theses questions again. Is there some place you can edit them?

If someone can help, Thanks!

---

### Post by HyperionQc on 2010-04-13
Well, I finally manage to do something. The connection error was caused by a missing certificate (!) and also by an error when configuring ldap.conf.
I was doing the change on /etc/ldap/ldap.conf. when I "cp" this one with the /etc/ldap.conf it worked perfectly.
There's also the path to the certificate that we need to put in the ldap.conf file.

TLS_CACERT /*path*/
tls_reqcert allow

With this, I'm able to authentificate with the LDAP to login to the computer. But there was a bunch of error occuring. Needed to put an extra line in /etc/pam.d/common-session to create the home directory when login 
session required pam_mkhomedir.so skel=/etc/skel
(I also put "session optional pam_foreground.so" at the end of this file, I don't know if it change something)

Well, I hope it will help someone somewhere sometimes.:P

Edit : Oh yea, theses sites help me too : 
[http://tuxnetworks.blogspot.com/2010/03/ldap-client-howto-804-lts.html](http://tuxnetworks.blogspot.com/2010/03/ldap-client-howto-804-lts.html)
&
[http://www.openldap.org/pub/ksoper/OpenLDAP_TLS.html#5.2](http://www.openldap.org/pub/ksoper/OpenLDAP_TLS.html#5.2)

---

