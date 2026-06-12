---
title: "hostapd landing page"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by irose123 on 2011-11-23
I have a working wifi AP using hostapd on Ubuntu 10.04 LTS.

Currently connected clients must manually start a browser and try to open a page before they are redirected to a login page. How do I force a landing page to open automatically on connection, such as happens when connecting iOS devices like iPod, iPhone or iPad to a public wifi hotspot?

Thanks.

---

### Post by irose123 on 2012-03-22
hello? anyone there?

---

### Post by tiglin1989 on 2012-03-22
cannot understand the problem, pl give proper idea

---

### Post by irose123 on 2012-03-22
What I basically want to know is: how can I show a 'landing page' that appears automatically when a wifi connection is made to my Ubuntu machine running hostapd? Currently i have to rely on a user starting a browser session manually.

However, if you connect to a public wifi hotspot using an iPhone/iPod/iPad, then you will frequently see a web page come up AUTOMATICALLY from the wifi settings page after the connection has been successfully made, usually asking you to login. This 'landing page' is what I'm after, how can I do this? Currently I have to rely on users starting up their browser manually.

---

### Post by drkrimson on 2012-05-23
I think the 'landing page' you are referring to is really a login page?
probably spawned as a side effect of some radius/eap system....

That, plus a transparent proxy so you can inject your page into any webrequest, is how I set it up...

For me it 'auto-popups' when I return the same (internal) ip address for all servers...

goodluck!
T

---

### Post by irose123 on 2012-05-24
Yes, that's what I'm after. How exactly did you set it up? I'm not sure what you mean by a transparent proxy. What packages have you had to install and configure to do this?

I'm using dnsmasq to perform DHCP and DNS lookup, configured as I think you have to return the same (internal) ip address for all servers. Plus hostapd to handle 802.11 connections.

Could you let me know some details about how to set this up on my Ubuntu 10.04 LTS box?

Thanks.

---

