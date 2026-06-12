---
title: "How to Configure PPPOE"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by eawedat on 2010-03-07
Its so strange
when i Disconnect my internet on Windows XP(Host)
it gets disconnected also in Ubuntu(Guest)

its like related thing via VirtualBox
How can i configure pppoe username & password in Ubuntu and Connect
so it would not be independent?
even i disconnect net on xp it would not disconnect in Ubuntu?


how to check out if my Ehernet card is installed at all?

win:
[IMG]http://img144.imageshack.us/img144/2015/41375218.gif[/IMG]
 
thanks.

---

### Post by Charly85551 on 2010-03-08
Hi, you need to understand that your XP is the hosting device to install an internet connection with your ISP and identify your machine as the one holding your ID via the PPPoE-protocol. If you disconnect your XP is saying goodbye to your ISP. The Ubuntu-software/virtual box does not have your ID-settings to talk to the ISP and subsequently connections are refused.
It would be different if you have a router since all PPPoE-functions are within the router (that is why you need to enter all your ID-details into the router). The rest is internal communication in your network. Your machines are identified by the so-called MAC-address of your network card to which normally an IP-address is allocated via DHCP-function in the router.
Hope this helps a bit
cheers
Charly85551

---

