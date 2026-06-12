---
title: "Ubuntu 10.04 LTS Can't Load Some Web Pages"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by dclerk on 2010-11-10
Hi:
The problem appeared recently. For some web pages, the browser is permanently stuck in a Loading state. It occurs for a number of web browsers: Firefox, Chrome, Opera

Wireshark indicates that a TCP sgement has been lost. Attempts at reloading the web page result in the same error. The web sites in question appear to be functional - no problem loading them from a Windows machine.

Linux kernel:
Linux Aragorn 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linu

Here is the Chrome error I get: Error 7 (net::ERR_TIMED_OUT)
Chrome version: 7.0.517.44

An example of a site where I get problems: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
Now, if I attempt to to click on the Access Free Documentation link from this site, I will get the Error 7 response from Chrome.

Firefox will show "Loading" forever, if I attempt to Access Free Documentation

The problem was present BEFORE I installed Chrome.

I notice that the web site in question that causes problems ( Access Free Documentation link) is:
[https://help.ubuntu.com](https://help.ubuntu.com)

Perhaps the issue has to do with https?

Any suggestions for how to troubleshoot/solve this issue will be much appreciated.

Thanks
Don

---

