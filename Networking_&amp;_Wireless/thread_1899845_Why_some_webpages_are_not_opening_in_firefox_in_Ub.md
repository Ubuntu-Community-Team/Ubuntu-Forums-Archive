---
title: "Why some webpages are not opening in firefox in Ubuntu 10.04?"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by Sayantan_Hore on 2011-12-24
Hi,

I have installed Ubuntu 10.04 on my desktop. I have successfully  connected my BSNL broadband and can access internet. I have upgraded to  Firefox 8. The problem is some webpages are not opening in firefox.  Pages like - yahoo.com, flickr.com, ubuntu forum pages etc and lots  others are not opening but loading infinitely. I have also installed  google chrome. But same thing is happening there also. My modem is  configured in bridge mode. Please help.

Thanks
Sayantan Hore:confused:

---

### Post by lovinglinux on 2011-12-24
Try to browse a page that doesn't load, using the IP. For instance try Yahoo at [http://98.139.102.145](http://98.139.102.145)

If the page loads, then most likely you have a DNS issue. Then you could try a different DNS provider like OpenDNS or Google DNS.

You could also try [DNS Flusher](https://addons.mozilla.org/en-US/firefox/addon/dns-flusher/)

---

### Post by Sayantan_Hore on 2011-12-25
I couldn't run DNS flusher because firefox addon page is also not opening. I tried [http://98.139.102.145]("http://98.139.102.145/") but it shows "[SIZE=1]**Sorry, the page you requested was not found.**"[/SIZE]

I issued two commands::

sudo aptitude install nscd

sudo /etc/init.d/nscd restart

but still no luck.

What can I do now?

---

### Post by lovinglinux on 2011-12-25
> **Sayantan_Hore said:**
> I couldn't run DNS flusher because firefox addon page is also not opening. I tried [http://98.139.102.145]("http://98.139.102.145/") but it shows "[SIZE=1]**Sorry, the page you requested was not found.**"[/SIZE]

That means the site is actually opening and you indeed have a DNS issue. The addresses are simply not resolving. you need to check your router configuration or try a different DNS server.

---

### Post by Sayantan_Hore on 2011-12-26
I tried Open DNS and Google DNS both as stated in
[http://www.liberiangeek.net/2010/08/change-dns-information-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/08/change-dns-information-ubuntu-10-04-lucid-lynx/)
but still the problem persists. My router is connected in bridge mode and I am using a pppoe dialer. It works fine in Windows 7. I have dual boot. It worked fine in Ubuntu too at the beginning. Ubuntu suggested some system updates. I performed those and then upgraded firefox from 3.6 ( default with ubuntu 10.04 ) to 8.0. Then the problem started.
Now what do you suggest?

---

### Post by lovinglinux on 2011-12-27
Try to disable ipv6 in Firefox.

[http://www.webgapps.org/tutorials/firefox/troubleshooting/connection-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/connection-issues-and-solutions)

---

### Post by Sayantan_Hore on 2011-12-28
Thanks. I have disabled ipv6 by editing /etc/default/grub file and also from firefox settings. Now ubuntuforums pages are opening. But other pages like yahoo.com, flickr.com, mozilla addon pages are still having the same problem. What next?

---

### Post by bvkmohan on 2011-12-28
1. Perform a sys clean up and try.
 
ddin't work ?
 
2. If you happen to have a router check its security settings and make them default. (you can never know)
 
didn't work ?
 
3. Do a traceroute to those sites and check where they are getting blocked 
 
(found the blockade ?)
3.1 try someother sites which are working 
 
(passing through the blockade ?) 
3.2 that node is blocking the sites you've mentioned
 
(if all sites are passing through fine?) go to 4
 
4. check in your friends PCs who are using the same ISP
 
worked ?
 
start from 1 again.

---

### Post by Sayantan_Hore on 2012-01-01
I tried everything but failed. Formatted hard drive and again installed Ubuntu 10.04. The problem persisted. Pages not opening but loading infinitely. I cannot change my router configuration because it would create problem in windows 7. I again formatted hard drive and installed ubuntu 11.10, the latest one this time. Now it appears to be working. Pages are slow loading but opening. I didn't disable Ipv6 in ubuntu 11.10. But still it is working. Ubuntu 10.04 is installed on my friends laptop. It works OK there. But I didn't like the Unity interface in Ubuntu 11.10. Gnome 2 is good for me. So I need to go back to 10.04. Can you please suggest something?

---

