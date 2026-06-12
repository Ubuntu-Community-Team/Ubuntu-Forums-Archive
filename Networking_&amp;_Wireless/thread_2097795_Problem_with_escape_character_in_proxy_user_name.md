---
title: "Problem with escape character in proxy user name"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by alm on 2012-12-24
Hi.

After about 4 years of happily (VERY HAPPILY) using ubuntu I am facing a wall.

My company has changed the network configuratin, now we use a proxy with user name and password authentication. I get a "blabla@blabla.com" username for that proxy.

Firefox configuration was easy and works ok.
Configuring system proxy is a nightmare because of the "@" in the user name. I have try to escape it several ways and in several files but still no success. Now, I can navigate the internet, but I cannot do apt-get install, update, etc ...

Please, help!

---

### Post by alm on 2013-01-30
No point on scaping with \ or with %40 
This are same of my tries that didn't work:  :mad:

export http_proxy=http://thisismyusername:thisismypasasword@proxy.whatevercompany.com:8080/ 4
export http_proxy=http://thisismyusername\@company.com:thisismypasasword@proxy.whatevercompany.com:8080/ 4
export http_proxy=http://thisismyusername\\@company.com:thisismypasasword@proxy.whatevercompany.com:8080/ 4
export http_proxy=http://thisismyusername/@company.com:thisismypasasword@proxy.whatevercompany.com:8080/ 4
export http_proxy=http://thisismyusername%40company.com:thisismypasasword@proxy.whatevercompany.com:8080/ 4
export http_proxy="http://thisismyusername'@'company.com:password@proxy.whatevercompany.com:8080/"
export http_proxy="http://thisismyusername'@'company.com:password@proxy.whatevercompany.com:8080/"
export http_proxy="http://thisismyusername`echo @`company.com:password@proxy.tcpsi.es:8080/


Finally I "resolved" it using a kind of tunneling in my own laptop with cntlm. I am writing this for me to remember it and for anybody with the same problem.


To me, it works this way:
- cntlm is up an running on your laptop listening to a port.
- When cntlm recives a request, it adds your user name and password as configured in cntlm, and then forwards your request to yourcompany/university/whateveryourare proxy.
- The point is that when you configure in cntlm where is your company proxy, your user name for that proxy and your password, you do it in several lines and it parses it correctly even if you (like me) have an @ (at sign) in your user name, or in your password. This way, when cntlm redirects your recuest it adds your user name and password properly.



This is how I achive this:
-> sudo apt-get install cntlm

-> sudo gvim /etc/cntlm.conf :
Proxy	your_company_proxy_server_ip:8080
Listen	1001
(for this example, I am assuming that your company server proxy listens on 8080 and that port 1001 is free on your laptop)

-> export http_proxy=http://127.0.0.1:1001
-> export https_proxy=http://127.0.0.1:1001
-> chromium-browser

:popcorn:

:-({|=

:twisted:

---

