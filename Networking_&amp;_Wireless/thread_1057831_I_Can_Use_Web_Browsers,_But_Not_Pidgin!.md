---
title: "I Can Use Web Browsers, But Not Pidgin?!"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by person9 on 2009-02-02
Hi.

At home, I connect to my wireless network (secure) and my boyfriend's home's wireless network (secure). Both work fine with everything.

At campus, I tried to connect to the WiFi. It is NOT a secured network (i.e. no WEP key or anything). This is my first day trying it on Ubuntu. It works fine on Vista, for the record. (I dual boot). 

At the moment, I am connected to the network, and I can use Opera and Firefox just fine. The weather is showing up correctly on my top panel. However, Pidgin is just sitting there with a dumb plug, saying it's connecting. I've restarted, and also disconnected and tried again. All it does is sit there "connecting".

Pidgin works fine at home, and messaging is working fine on Vista. I can connect to AIM and MSN through Meebo.com.

Any ideas? Is it a setting? Simple fix? Complex issue?
Thanks!

---

### Post by sp0nge on 2009-02-02
I'm not sure if this will work, but I thought I'd offer my 2 cents!

You may try updating it through Synaptic, or uninstalling altogether and reloading pidgin.

---

### Post by kbutcher5 on 2009-02-02
> **person9 said:**
> 
Pidgin works fine at home, and messaging is working fine on Vista. I can connect to AIM and MSN through Meebo.com.

This is most probably because your network administrator at your school, has either:
A) Misconfigured the network
B) Blocked some of the ports pidgin needs to be able to run

---

### Post by Neural oD on 2009-02-02
agreed - check that you are not running through a proxy

---

### Post by person9 on 2009-02-02
I'm not sure if this would offer any clues, but Pidgin works fine on Vista. I used to use it on there before I got Ubuntu on this as well.

Proxy = Don't know what that is, so I may or may not be on one. I've never heard anything about that here, and the network is very flexible and unrestricted, I don't think they have a whole lot of regulating stuff (ex. I know of some schools that block anyone on their network from using IM programs, going to certain websites (facebook, myspace), etc even if its on their own computer). Under the proxy settings on Pidgin, it's blank.

I'll try to update Pidgin with Synaptic and see if that works. Thank you!

---

### Post by person9 on 2009-02-02
No. It didn't help. 

It just keeps "connecting" and finally gives up, with this message: > Could not connect to authentication server:
Connection timed out

---

### Post by person9 on 2009-02-02
Fixed it! I changed the port from 5190 (or similar) to 443, suggested in another thread. Thanks anyway!

---

