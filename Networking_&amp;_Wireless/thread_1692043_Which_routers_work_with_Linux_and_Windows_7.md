---
title: "Which routers work with Linux and Windows 7"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by Sunrock on 2011-02-20
I just installed the Cisco Linksys E3000 router on my primary hard disk.  I have my PC setup to boot to either Windows 7 on my primary hard disk or Ubuntu on my secondary hard disk.  I contacted Cisco and they told me that they do not support Linux.  That was my fault for not reading the router documentation. Anyway, I guess I just wasted my money unless someone could help me with this router.  If not, can someone recommend a good router that works with both Windows 7 and Ubuntu?  I would appreciate any help.  Thanks!

---

### Post by inobe on 2011-02-20
the software that comes on the cd you get is not supported, lets get that straight ;)

you could still configure almost any router without the software from your web browser on any operating system that has a web browser.

besides, the software cd is basic bloatware and would never install it on a windows machine.

> Minimum Requirements

    * Internet Browser: Internet Explorer 6, Safari 3, or Firefox 2 for **Optional Browser Based Configuration**

---

### Post by YesWeCan on 2011-02-20
> **Sunrock said:**
> I just installed the Cisco Linksys E3000 router on my primary hard disk.  I have my PC setup to boot to either Windows 7 on my primary hard disk or Ubuntu on my secondary hard disk.  I contacted Cisco and they told me that they do not support Linux.  That was my fault for not reading the router documentation. Anyway, I guess I just wasted my money unless someone could help me with this router.  If not, can someone recommend a good router that works with both Windows 7 and Ubuntu?  I would appreciate any help.  Thanks!
+1 to inobe.
What Cisco Customer Suppport really mean is that they are in cahoots with Microshaft and do not wish to admit that their router works perfectly well with linux PCs. :p
I have two Cisco routers and they work perfectly and can be configured without any limitations via their browser interface.

---

### Post by zacktu on 2011-02-20
If you're unsure of what to do with the browser interface, go ahead and install the software CD in Windows 7 and follow the instructions in the manual to configure your router (or maybe there's a wizard).  You will want to set the SSID and your WPA encryption key.  Take notes on the values you assign for SSID and the encryption key along with anything else that you modify.  After the router is working fine with Windows 7, then enter those same values in your linux wireless setup panel.

---

### Post by Sunrock on 2011-02-21
Thanks for all the replies.  After I read the first two replies, I rebooted my PC and I logged into Ubuntu for the first time since I installed the new Cisco router.  To my amazement, Ubuntu automatically installed the new Cisco router. YesWeCan, you were right.  The Cisco router works perfectly.  After I saw that the router  was working, I right-clicked on the Network Manager icon and I selected "Connection Information."  In the "Connection Information" window, I noticed that it displayed "Security: None."  Does this mean that I need to update the security settings like creating a password, etc.?  If so, I need some instructions.  Thanks!

---

### Post by bodhi.zazen on 2011-02-24
> **Sunrock said:**
> Thanks for all the replies.  After I read the first two replies, I rebooted my PC and I logged into Ubuntu for the first time since I installed the new Cisco router.  To my amazement, Ubuntu automatically installed the new Cisco router. YesWeCan, you were right.  The Cisco router works perfectly.  After I saw that the router  was working, I right-clicked on the Network Manager icon and I selected "Connection Information."  In the "Connection Information" window, I noticed that it displayed "Security: None."  Does this mean that I need to update the security settings like creating a password, etc.?  If so, I need some instructions.  Thanks!

I saw your thread in the security section.

This is not really a question about Ubuntu, or even Windows, it is a question about how to configure your router.

I suggest you start by reading the router documentation. Most routers have built in information / help once you log into them.

---

### Post by YesWeCan on 2011-02-24
> **Sunrock said:**
> Thanks for all the replies.  After I read the first two replies, I rebooted my PC and I logged into Ubuntu for the first time since I installed the new Cisco router.  To my amazement, Ubuntu automatically installed the new Cisco router. YesWeCan, you were right.  The Cisco router works perfectly.  After I saw that the router  was working, I right-clicked on the Network Manager icon and I selected "Connection Information."  In the "Connection Information" window, I noticed that it displayed "Security: None."  Does this mean that I need to update the security settings like creating a password, etc.?  If so, I need some instructions.  Thanks!

You need to configure the router. For example, you may want to add a security password/key to your wireless network so no one else can access it.

zaktu's method is easy and will work using Windows.

You can also configure the router using Ubuntu. The router has its own web page. You can access it using a browser like Firefox. In the url you put the IP address of the router, typically something like 192.168.1.1

You'll need to read the router manual for details and to get the default admin password for the router (which you should also change).

---

### Post by Sunrock on 2011-02-25
Thanks for all the replies.  Between reading the router documentation and contacting the router manufacturer, I found out that the default router security was sufficient.  When the router was initially installed, I change the default router password.  Thanks again!!

---

