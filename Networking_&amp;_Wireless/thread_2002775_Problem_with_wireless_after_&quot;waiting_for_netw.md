---
title: "Problem with wireless after &quot;waiting for network configuration&quot;"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by flldom001 on 2012-06-13
Hi all, 

Yesterday I connected to the internet using pppoeconf submiting a username and password for my broadband account. I did this through through my wireless connection to my friend's router. Everything worked fine until I restarted. 

It now tells me on the boot up screen:

"Waiting for network configuration"

"waiting 60 more seconds for network configuration"

and then lets me log in, only to find that there is no wireless (i.e. does not pick up any networks) and I of course cannot connect to the internet.

The version of Ubuntu I am running is 11.10. I would be so grateful for any help.

Thanks
Dom

---

### Post by chrysssl on 2012-06-15
I have the same problem too. I've deleted pppoe configuration files, those pppoe lines from /etc/network/interfaces, made again eth0 dhcp, the only way to go online is to wait 2 more minutes during startup and after that sudo service network-manager restart.
Please tell me what to do.

---

