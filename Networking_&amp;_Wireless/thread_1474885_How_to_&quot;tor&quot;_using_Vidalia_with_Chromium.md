---
title: "How to &quot;tor&quot; using Vidalia with Chromium in Ubuntu 9.10?"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by jiapei100 on 2010-05-06
Hi, all:

My situation:

> Ubuntu:  9.10
internet browser:  Chromium
tor tool:   Vidalia 0.2.6

I can see that Vidalia is working fine.
It shows the status
> Connected to the Tor network!


I'm wondering if anybody can give me hint on
how to let my browser Chromium bypass the blocks 
and reach some websites using "tor" based on Vidalia?

Thank you very much.


Best Regards
JIA

---

### Post by tango_ninja on 2011-03-05
> **jiapei100 said:**
> Hi, all:

My situation:



I can see that Vidalia is working fine.
It shows the status



I'm wondering if anybody can give me hint on
how to let my browser Chromium bypass the blocks 
and reach some websites using "tor" based on Vidalia?

Thank you very much.


Best Regards
JIA

Tor project now recommends using **polipo** instead of vidalia.  Once tor and polipo are installed, you can use the proxy network by configuring the proxy settings in chrome/chromium.  Actually just documented this procedure today.  See here:  [How to configure google chrome for tor]("http://justplainobvious.blogspot.com/2011/03/how-to-configure-google-chrome-for-tor.html").

---

