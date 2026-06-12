---
title: "how to configure terminal proxy??"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by Bahdour on 2012-12-16
Hi.. I’m having trouble with configuring proxy settings. I'm working in an active directory domain with Windows 2008 functional level. We connect to the internet through ISA 2006. When I configure Firefox, the web navigation works fine.
 
But when I try to apply system-side proxy settings, it doesn’t work. I tried to add the following to /etc/bash.bashrc :
```
export http_proxy=http://username:password@proxyIP:port/
export https_proxy=http://username:password@proxyIP:port/
export ftp_proxy=http://username:password@proxyIP:port/
```
 
 
But it didn't work for me. Something is confusing me. Usually in Windows Authentication we specify the user account in two ways:
1) domain\username
2) [EMAIL="username@domain.com"]username@domain.com[/EMAIL]
 
Linux GUI applications would accept this but would the terminal accept it!! “\” is a windows separator but in Unix/Linux we use “/”. Moreover, in the syntax mentioned in the example above, “@” is used to separate user credentials and the proxy. I don’t think that we can use @ in the password or in the username.
 
I tried then to use ntlmaps and configured the gnome Network Proxy tool to use localhost with the port used in ntlmaps (5865). Then added the following lines to /etc/wgetrc
```
https_proxy = [http://localhost:5865/](http://localhost:5865/)
http_proxy = [http://localhost:5865/](http://localhost:5865/)
ftp_proxy = [http://localhost:5865/ ]("http://localhost:5865/")
```
 
But it didn't work also. Even firefox couldn't get internet access using ntlmaps. Anyway windows doesn't use NTLM anymore. It uses Kerberos. But I thought to try and see the result.
 
Does anyone knows how to solve this issue? :(

---

### Post by Bahdour on 2012-12-25
hi.. I've posted my issue a week ago but no one has replyed.. if anyone knows how to solve this issue, please let me know.

---

