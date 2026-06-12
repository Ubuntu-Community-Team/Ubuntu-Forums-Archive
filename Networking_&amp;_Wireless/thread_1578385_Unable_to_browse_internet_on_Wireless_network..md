---
title: "Unable to browse internet on Wireless network."
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by hammyj on 2010-09-20
Hi Guys, I have searched for days in an attempt to solve this issue, but I'm all out of searching!

Running Ubuntu 9.10.

I'm connecting to a network via a Belkin F7D1101. The adapter appears to be working fine, as I can see various wireless networks available and I am able to connect to my personal wireless network. 
The problem is that even though I am connected and have a valid IP, I am unable to browse the Internet. I can't even ping the router!

I initially thought it may be an issue with WPA, but I have installed wpa-supplicant and as a means of testing, I turned off WPA on the router, and the issue still stands. 

If you guys need anymore info, let me know. 

Thanks.

---

### Post by Iowan on 2010-09-20
What is the IP address - hopefully not 169.254.X.X (**avahi**)

---

### Post by hammyj on 2010-09-21
No, it's a valid IP address handed out via DHCP.

Very odd.

---

### Post by hammyj on 2010-09-23
Any ideas guys? 

I'm able to connect to a local BT Openzone network without any problems. I've turned off security on the router and attempted it without any WPA/WEP keys but the problem still remains.

---

### Post by grahammechanical on 2010-09-23
If you can connect to someone else's wireless network and to your router then Ubuntu is doing what it is supposed to do. Can you connect to the router's set up program using a web browser? Could it be that the router does not have the correct address for your ISP or the correct username and password for yourself as a customer of that ISP? Did you reset the router by any chance?. That puts the settings back to the factory default settings which may not include the ISP connection details.

regards.

---

### Post by hammyj on 2010-09-23
I agree that it does initially appear to be a problem with the router rather than Ubuntu. 

However, we have  other machines connected without any problems via wireless, and 2 connected via cable (Including my Ubuntu build which will not browse the net when on wireless). 

Even when connected to the wireless network, and I'm given a correct IP, I am unable to ping my Ubuntu machine from other nodes on the network. 

I am unable to connect to the routers admin panel when connected wirelessly, I'm also unable to ping the router. 

We are using Cable Virgin Media if this helps at all.

---

### Post by himanshumarwaha on 2011-01-06
Hi 

I have just downloaded 10.10 yesterday and was liking it so far, until i did an update and some 220 applications got updated. Ever since I am unable to browse internet on wifi. It was working fine before the update. I can browse when connected to ethernet, but not on wifi
My network connections as follows:
ADSL modem --> Linksys WRT54G wifi router

if i connect directly to the modem, internet works!
I have tried resetting the DNS on the computer as per on the modem but no luck!

It works when i log on to win7 which was my original OS. Also wifi works smooth on my pda and smart phone, its only ubuntu its not working on!

Please help.

---

### Post by PatchesTheCaveman on 2011-01-06
There is a broken update to the Linux kernel that causes problems with many devices, including several different kinds of wireless network adapters.

To see if you have this faulty update and fix it, see this post:
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

---

