---
title: "Internet Connection Settings - TCP/IP in Ubuntu 8.04"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by LindaLou on 2009-08-28
Am running 64 bit Ubuntu 8.04 on my PC, FF as my browser. I was unable to get an internet connection with FF- Server Not Found - and had the "tech" come over.  He was able to get the internet up again, but only on my laptop that runs Windows XP.  He changed the TCP/IP IP Address, Subnet Mask, Gateway Address, DNS Server, DNS Secondary.  Being unfamiliar with Linux OS he left the office and I took on the task.    
I went into System > Administration > Network Settings and altered the settings to match my laptop. Went to Connections tab > Properties > altered the settings here and chose Static IP Address. 

In actual fact, it took several the settings stuck!  I would try the Internet and nothing. Go back into Newtwork Settings and everything was back to the original.
Seems to work ok, FF is slow, but I'm not sure if it is the Internet being slow or FF slow or what.  Some pages don't load  and I get the "server not found try again".  When I click on Try Again, the page loads.  Pages such as Gmail, BBC headlines, CNET.com. Nothing out of the ordinary. (I have phobias of surfing the net and never stray to far from "home".)

However,after my altered settings I no longer can check the Connection Information from the Internet icon.  Connection Information is now grayed out. I would like to know how I can get that [Connection Information] higlighted again.  As well, I would like to know if I performed the proper steps, did I miss some and/or is there a simplier way to resolved the Internet issue I had.

---

### Post by Iowan on 2009-08-28
Part of the issues sound like DNS problems. For the connection information, I'll need to check some of my bookmarks for 8.04 static addresses (when I get home). 
IS this a home system (where you might have access to the router) or is it an IT-controlled network (at work)?

---

### Post by LindaLou on 2009-08-28
I have only one PC and my laptop so router is the answer to your question.  

I set it to Static IP as the Automatic didn't work.  The tech left me with 3 options for the address (one for the laptop and one for the PC).  I have been able to get them both running now farily decently but still am not able to view Connection Information from the Network icon - this option is still grayed out.

---

### Post by Iowan on 2009-08-28
Here are some of the static address links I found for Hardy/Intrepid:
[http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html")
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")
[Here]("https://www.opendns.com/start/device/ubuntu") is one for OpenDNS.

---

### Post by LindaLou on 2009-08-29
Thanks so muchIawan for great links!  I took a quite peek at [www.cyberciti.biz/tips/howto-...iguration.html](www.cyberciti.biz/tips/howto-...iguration.html) and the IP settings look similar to what I have set up.  I'll take a look on Monday, when I'm back at work.  I'm going to to some searching to see if I can find anything out about the "graying out" of Connection Information from the System Icon. A bit strange.  I know that I can still access this information from System > Administration etc but I would like to know how I made it unavailable.

---

