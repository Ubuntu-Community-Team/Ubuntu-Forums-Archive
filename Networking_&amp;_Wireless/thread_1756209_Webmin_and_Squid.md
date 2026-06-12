---
title: "Webmin and Squid"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by checkm8 on 2011-05-12
I read the tutorial on the following link:

[http://doxfer.webmin.com/Webmin/SquidProxyServer](http://doxfer.webmin.com/Webmin/SquidProxyServer)

and I cannot set up proxy authentication appropriately. I have followed the following steps:

1) In authentication programs use webmin default to authenticate users.
2) Under Access Control create an ACL named "Allowed_Users"  of the External Auth type with matching REQUIRED.
3) Under proxy restrictions Deny !Allowed_Users
4) Create a user under proxy authentication.

I know the login works because if I type an incorrect login authentication on the browser will prompt me to type again, but when I type in the correct login, it states:


ERROR
 
The requested URL could not be retrieved
 
--------------------------------------------------------------------------------


The following error was encountered while trying to retrieve the URL: [http://www.google.com](http://www.google.com)

 
Access Denied.
 
Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect.

Your cache administrator is webmaster.
 
Any suggestions?

---

