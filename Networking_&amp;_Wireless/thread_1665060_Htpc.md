---
title: "Htpc"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by hop-sings on 2011-01-11
I want to access my ubuntu HTPC portable hard drive with my windows 7 laptop, so I can watch the movies on my HTPC around the house. I am very new to ubuntu and to networking, is there a simple step by step explanation on how to do this? 

or should I just buy a new router that can connect to a hard drive?

Thank you for you help

---

### Post by s31523 on 2011-01-11
This has been discussed a lot on various forums, including here.

For example, a quick search for 'samba' yielded this thread:
[http://ubuntuforums.org/showthread.php?t=1661741&highlight=samba](http://ubuntuforums.org/showthread.php?t=1661741&highlight=samba)

Search Ubuntu forums and other resources using your favorite search engine. 

Basically you will need to enable some Windows 7 sharing options so that Windows 7 will be able to see other Windows computers.  Then you will need to set up a Samba share on your Ubuntu htpc.

You could also install WinVNC and remote connect from your Windows7 laptop to the htpc.  To make things easier, should you go this route, you may want to configure your htpc with a static IP address.  My 'servers' on my home network I have set to static IPs so I can then add their IPs to the /etc/hosts file so I can use their hostnames.

good luck

---

