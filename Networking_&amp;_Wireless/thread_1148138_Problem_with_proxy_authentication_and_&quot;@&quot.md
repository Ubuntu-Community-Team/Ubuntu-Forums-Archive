---
title: "Problem with proxy authentication and &quot;@&quot; sign"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by moskva on 2009-05-04
Hi

At work we run a proxy server that requires proxy authentication, now i'm sure that i can get it fixed with the editing the following file /etc/apt/apt.conf

and inserting the following lines:

Acquire::http::Proxy "http://username:password@proxyserver:8080";
Acquire::ftp::Proxy "ftp://username:password@proxyserver:8080";

the problem is that my password has the "@" sign in it, something like this pass@123 (not the real password just example) and we have to have an "@" sign in our password, this is stuffing me around when i want to get updates for ubuntu using the "sudo apt-get update"
command,i keep on getting the following error 

Could not resolve '123@bluecoat'

Hope there is someone that is willing to help.

Thank You in advance.

moskva

---

