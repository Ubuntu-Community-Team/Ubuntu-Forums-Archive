---
title: "problem using xchat through squid"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by orudie on 2013-03-06
I am having a problem with squid proxy server and xchat as well as kvirc. 

This is the error I see in xchat and kvirc when it is trying to connect to proxyip: port 
HTTP/1.0 403 Forbidden
Proxy traversal failed.

The same proxy server information works just fine when I set it up in the web browser.

**[COLOR="#FF0000"]sudo dpkg -l | grep squid[/COLOR]**
ii  squid-langpack                      20100628-1                   Localized error pages for Squid
ii  squid3                              3.1.6-1.2+squeeze3           A full featured Web Proxy cache (HTTP proxy)
ii  squid3-common                       3.1.6-1.2+squeeze3           A full featured Web Proxy cache (HTTP proxy) - common files

**[COLOR="#FF0000"]squid access.log[/COLOR]**
TCP_DENIED/403 3387 CONNECT irc.freenode.net:6667 - NONE/- text/html

Thanks in advance.

---

### Post by tomerc on 2013-03-07
Hi,

In order to tunnel through your squid proxy to irc server, it should be configured to support CONNECT method and also to allow connection to port 6667.

In order to check whether your squid is configured to support the CONNECT method, simply try surfing through it to an HTTPS site , and see if you are able to pass through or get 403 error in your browser.
AFAIK by default squid does not allow connecting to port 6667 and you need to alter its "Safe_ports" acl to allow it.

Good luck.

---

### Post by orudie on 2013-03-07
Thanks for the quick reply. 

in squid.conf I added port 6667 to acl Safe_ports like so: 

**[COLOR="#FF0000"]acl Safe_ports port 6667        # irc[/COLOR]**

However, I still get the same error in irc client

**[COLOR="#FF0000"]xchat client: [/COLOR]**
HTTP/1.0 403 Forbidden
Proxy traversal failed.
Stopped previous connection attempt (pid=2100) 

**[COLOR="#FF0000"]squid access.log:[/COLOR]**
TCP_DENIED/403 3376 CONNECT irc.dal.net:6667 - NONE/- text/html


Just to add some information. I used the same proxy server information in the web browser, and I seem to be able to go to https sites just fine including [https://www.google.com](https://www.google.com) and [https://mail.google.com](https://mail.google.com)

---

