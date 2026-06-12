---
title: "Internet not working in ubuntu installed in virtual box"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by lalit_IIT on 2011-08-03
Hi,

I have Windows 7 as my host machine and I am behind a proxy for 
accessing the internet.

 I installed virtual box in windows and then ubuntu 11.04 in 
virtual box.
 
I then edited the apt.conf with proxy name
so that I could update, and and was able to do so. 


But now I am not able to connect to internet from ubuntu whereas I am able to connect from windows7.

The error is : could  not resolve proxy name.

Did something went wrong while updating.
What could be the reason.

---

### Post by Beacon11 on 2011-08-03
You shouldn't have to worry about the proxy setting in Ubuntu unless you have virtualbox configured to bridge your network connection. By default, virtualbox uses a NAT. Did you test your connection before you made the change to apt.conf?

---

### Post by idlemind324 on 2011-08-03
Beacon11, if he needs a proxy to connect to the Internet on his normal LAN wouldn't he still need that even in a NAT situation to properly get Internet? When the NAT routes traffic outside of itself it would get stuck trying to get to the Internet where it should be accessing a proxy server. Maybe I'm missing something though.

lalit, Try adding the proxy settings to your browser.

---

### Post by Beacon11 on 2011-08-03
> **idlemind324 said:**
> Beacon11, if he needs a proxy to connect to the Internet on his normal LAN wouldn't he still need that even in a NAT situation to properly get Internet? When the NAT routes traffic outside of itself it would get stuck trying to get to the Internet where it should be accessing a proxy server. Maybe I'm missing something though.

lalit, Try adding the proxy settings to your browser.

Now that you mention it, I'm not 100% certain. I figure there are some system-wide proxy settings you can change in Windows control panel, which would then work with virtualbox. However, you may also be able to go to the Network Proxy settings in Ubuntu and add the proxy info there.

---

