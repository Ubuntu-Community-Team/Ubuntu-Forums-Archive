---
title: "WPA supplicant and dhclient issue"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by mosestruong on 2006-05-10
I'm currently using wpasupplicant to connect to a network with EAP-PEAP and TKIP. I can get connected sometimes, but most of the time I have to either wait quite a long time or run `sudo dhclient` in order to get an IP address.

I think the problem is that dhclient starts after wpasupplicant, but before the connection is established. Are there any way to get dhclient to start only after WPA has finished setting up? Thanks.

---

### Post by ssalman on 2006-05-10
Just a suggestion, well maybe two :).
   
  You can write a script that greps &#8220;wpa_cli status&#8221; output for a &#8220;connected&#8221; message, and then invokes &#8220;dhclient&#8221;, if not connected yet, sleep for a sec and then try again (using a loop). Didn&#8217;t try this my self as I opted for static IP address to make this process easier and faster, but I did have this problem before.
   
  Another possible solution is to use the /etc/networking/interfaces file and setup the wpasupplicant call in &#8220;preup&#8221;, and then the dhclient call in the &#8220;postup&#8221;, that didn&#8217;t work as smoothly as I thought it would.
   
  Hope this helps.

---

