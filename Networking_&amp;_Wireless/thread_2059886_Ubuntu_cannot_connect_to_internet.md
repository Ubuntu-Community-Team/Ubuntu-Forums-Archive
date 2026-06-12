---
title: "Ubuntu cannot connect to internet"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by ranger1021994 on 2012-09-19
I have Netgear DGN2200v3 and i am running 12.04 64bit
Here's the scenario :

---->When i start my router at Ubuntu's boot,i can connect to internet perfectly.After finishing my work i shut my PC down but keep the router on because of wifi.

---->However at next boot(considering my router to be on before pc boot),i cannot connect to internet unless i restart my Ubuntu..




Any ideas why this is happening ??

---

### Post by vandorjw on 2012-09-19
Whether or not you connect via wireless or wired shouldn't have anything to do with this problem since internet works when you start the computer, then start the router?

Since you have an ADSL router, do you enter you login information (provided by your telecom provider) at router, or do you have it set up using ubuntu's network manager?

If you haven't already, configure your router at [http://routerlogin.net](http://routerlogin.net)
Next,set Ubuntu to use DHCP automatic IPv4

See, what I think happens is that the information for your internet connection is stored on the computer. The router is not set to keep the connection alive, so when the computer goes down the router no longer knows your username and password, and it is not smart enough to ask for this information when the computer is powered back on.

But I am not 100% sure.

---

### Post by ranger1021994 on 2012-09-19
My friend....when i said that i can connect to internet when router is switched on after pc boot,it means that i have properly configured my login id and password...else i wouldnt have been getting the internet.

I have already set it to automatic DHCP

Nopes...the router remembers the login info (ps: i have broadband ..sorry dat i forgot to mention it in question)..so the login info is stored in the router lest my wifi wouldnt have been working with my pc down.

---

