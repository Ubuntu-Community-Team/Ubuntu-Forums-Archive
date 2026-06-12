---
title: "Ubuntu and Windows not getting along"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by Natalio on 2011-08-27
Hi everyone,

I have two computers and a wi-fi router. A notebook with Ubuntu 10.04 and a desktop with Windows 7. Whenever the notebook is on, the desktop starts having horrible Internet speed, and eventually disconnects. If I turn the notebook off (or disconnect from the network) it starts working fine again. Both computers connect to the router via wi-fi.

I should also note that the connection runs flawlessly on Ubuntu.

Any thoughts?

Thanks!

---

### Post by northd_tech on 2011-08-27
I'm assuming that you do not mean that you are having dual boot issues with the notebook (as in the Ubuntu notebook does NOT have Windows 7 installed on it).

Have you considered assigning a static IP address to the Win7 desktop (instead of using automatic IP addressing)?  That might make the Win7 wireless connection more reliable:

[http://portforward.com/networking/static-win7.htm](http://portforward.com/networking/static-win7.htm)

Also, depending upon your wireless router, you can put the Win7 desktop and Ubuntu laptop wireless MAC addresses in a "recognized" or "allowed" list which usually speeds up connection speeds (and increases security immensely).  The downside is that many routers "lock out" any guest wireless connections when the "allowed list" is enabled.

EDIT:  what brand and model of wireless router are you using?  Perhaps there is a router setting that only allows one connection at a time for security reasons (and apparently the Ubuntu laptop is somehow taking priority over the Windows 7 desktop wireless possibly due to antenna strength, higher Win7 "overhead," etc).

---

### Post by Natalio on 2011-08-27
> **northd_tech said:**
> I'm assuming that you do not mean that you are having dual boot issues with the notebook (as in the Ubuntu notebook does NOT have Windows 7 installed on it).

Have you considered assigning a static IP address to the Win7 desktop (instead of using automatic IP addressing)?  That might make the Win7 wireless connection more reliable:

[http://portforward.com/networking/static-win7.htm](http://portforward.com/networking/static-win7.htm)

Also, depending upon your wireless router, you can put the Win7 desktop and Ubuntu laptop wireless MAC addresses in a "recognized" or "allowed" list which usually speeds up connection speeds (and increases security immensely).  The downside is that many routers "lock out" any guest wireless connections when the "allowed list" is enabled.

Your assumptions are correct: I do not have a dual boot, but two different computers.

I will try assigning a static IP right now and see how it goes. I don't know about MAC addresses, could you please link me to some resources about how to do that in case the static IP thing doesn't work?

Thank you very much!

---

### Post by northd_tech on 2011-08-27
> **Natalio said:**
> 
I will try assigning a static IP right now and see how it goes. I don't know about MAC addresses, could you please link me to some resources about how to do that in case the static IP thing doesn't work?

It might be a lot faster/easier if I know the make and model of your wireless router to get some specific info/page numbers/chapter(s) for your hardware, but see these articles to get the general idea of what would be involved:

The MAC Address
An Introduction to MAC Addressing 
[http://compnetworking.about.com/od/networkprotocolsip/l/aa062202a.htm](http://compnetworking.about.com/od/networkprotocolsip/l/aa062202a.htm)

Enable MAC Address Filtering on Wireless Access Points and Routers
Improve home network security
[http://compnetworking.about.com/cs/wirelessproducts/qt/macaddress.htm](http://compnetworking.about.com/cs/wirelessproducts/qt/macaddress.htm)

[http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)

---

