---
title: "Need to Automate PPTP connectivity from Linux to Windows"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by michwill on 2009-08-16
Hi All,

I'm in need of setting up cron-based VPN connectivity from Ubuntu "Jaunty" to a Windows-based VPN over PPTP for incremental DB synchronization. Using the default Network Manager and PPTP module everything seems to work fine. However, I have 2 issues:

1) Despite checking "Use this only for resources", I still lose my local internet connection and am routed through their servers.

2) As a result of 1 I have need to automate connecting to and disconnecting from the VPN in order to perform various tasks as the machine is at the office and I am not.

Much of the information I'm finding on PPTPing from Linux to Windows involves the use of GUI Network Manager, etc. However, I need to perform these steps from the command line for the sake of automation. Can anyone point me to a quality bit of documentation for this specific case?

Best.

---

### Post by arthur.m on 2009-08-16
Hi, read this, it may help

[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

Regards,

Arthur

---

### Post by michwill on 2009-10-05
It would appear the information there is very dated.  Are there any more current/relevant pieces of documentation?

---

