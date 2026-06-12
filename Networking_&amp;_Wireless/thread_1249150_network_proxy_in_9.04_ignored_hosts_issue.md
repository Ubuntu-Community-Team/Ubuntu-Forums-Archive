---
title: "network proxy in 9.04 ignored hosts issue"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by trmentry on 2009-08-25
hello,

hopefully someone can help me out.  i'm using the network proxy settings in ubuntu 9.04.  

i have the proxy setup and it works fine, but there are a few things I need to not use the proxy on.  so i put in 
*.example.com 
for the domain names, but there are some just by ip blocks.

for example in the enterprise I work at there are a lot of 10.x.x.x servers not in dns.   so I tried to add, 10.0.0.0/8 but i still couldn't reach the 10.x.x.x server that I wanted.  I added in the /32 for the server and it worked fine.

however with the amount of servers out there this will get unwieldy.

is there an issue with the network proxy and a certain prefix length?  if so is there a work around?

thanks

---

### Post by trmentry on 2009-08-25
anyone?

---

