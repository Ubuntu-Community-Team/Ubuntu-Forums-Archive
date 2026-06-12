---
title: "Automating GSM reconnection"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by joelgsf on 2009-09-11
I am using Ubuntu 9.04 and my Internet connection is through a Huawei  HSDPA E220 Modem, wich is readly recognized by network manager and works fine. My problem is with reconnecting the modem when the connection goes down. I have to intervene using the mini-applet available in the panel. The major problem is that the machine it is installed in serves as the Internet gateway for my home network and may be working unatended. I would like to find a way to enable it to reconnect automatically when it goes down but couldn't find it yet. Inside network manager I can set it to **connect automatically**, what it does, but there is no option for **reconnecting automatically**. My question is, can it be done by any other means?
Thank you all for any assistance.

---

### Post by joelgsf on 2009-09-21
As I could get no answer to this question, here or elsewhere, I decided to step down from NM, with respect to Wideband GSM connections, and configured wvdial to do the job, which it is doing as expected - connects at boot time (through rc.local call) and reconnects automatically in any event which may cause the connection hangup (through wvdial.conf configuration option). I'm very very satisfied now.
Maybe, someday, with a new version of NM, I will try it again, if I can control the connection as I need.
That's why I marked as SOLVED this thread. Because my connection problem has been solved, though NM control has not.
Only one problem is residual - how to tell NM not to bother with GSM connections, as it is being cared for by wvdial. When I log in it prompts me for configuring a new GSM connection. If anyone has the answer I'll be pleased to hear about.
Cheers.

---

