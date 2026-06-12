---
title: "help with proxy"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by mosquetero on 2009-09-12
Hi all!!

I want my Ubuntu to give connection to the internet to another computer. To do that, I am trying to use a proxy in my Ubuntu, specifically: squid 3.0. 1st question: do you know an easier solution??

I have configured it and my other computer but when I try to connect to the internet in the other computer I received the next message:

ERROR

The requested URL could not be retrieved

The following error was encountered:

[LIST]
[*]Access Denied
[/LIST]

Access control configuration prevents your request from being allowed at this time.

I googled the problem and I found that I had to change the squid.conf and write "transparent":

```

http_port 7777 transparent

```

But the problem is still there. I haven't changed any value of the squid.conf, just the port and I have added transparent.

Any idea?

Thank you in advance

---

### Post by mosquetero on 2009-09-12
I solved it! I stopped using squid and start using bfilter which is simplier but easier to use. Now it works :D

---

