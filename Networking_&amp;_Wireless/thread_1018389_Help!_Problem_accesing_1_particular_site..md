---
title: "Help! Problem accesing 1 particular site."
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by ucary2 on 2008-12-22
Problem regarding accessing one particular site(king.com). It's a game site. Problem details is listed below.

- in the browser(firefox) navigation bar
   the location bar displays a different description for king.com. It displays smartbro...portal(our isp provider portal)when scrolling in the location bar for the list of url addresses all the other sites have right descriptions.Look at the image below: 
 
-when I tracert king.com in cmd prompt. It displays the following result. Look at the image below.


-the smart bro ip address(169.254.1.1) is also inaccessible and displays no description in location bar
See the image below.

The possible cause of the problem:
- I have reformatted my hard disk
- I have installed vonage phone device

Please help me with this query. Thanks in advance.

---

### Post by dmizer on 2008-12-22
Do you have another router in addition to your Vonage phone device?

How is your network physically configured (what is plugged into what)?

---

### Post by ucary2 on 2008-12-22
No router is connected with it. Smartbro cable(my isp provider)is connected to WAN port of vonage devige and an ethernet cable plugged in the LAN port of vonage is then plugged to ethernet port in my PC. Firefox is configured to have direct connection to the internet. I did not use manual proxy configuration.

---

### Post by dmizer on 2008-12-22
Try switching to OpenDNS DNS servers: [https://www.opendns.com/homenetwork/start/device/ubuntu](https://www.opendns.com/homenetwork/start/device/ubuntu)

Note: be sure to follow the directions under "To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:"

---

