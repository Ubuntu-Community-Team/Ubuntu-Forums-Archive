---
title: "Ubuntu 10.04 Lucid Lynx"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by JohnDoe365 on 2010-05-17
A lot of people have the problem to find themselves with Lucid Lynx 10.04 and experience massive issues when connecting to wireless - me too.

As a service, here some relevant links which promise relief:

Disable IPv6
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)
Disable IPv6 in firefox
[http://ubuntuforums.org/showthread.php?t=1472356&highlight=disable+ipv6](http://ubuntuforums.org/showthread.php?t=1472356&highlight=disable+ipv6)
manually disable auto bandwith mediation of WiFi
[B]sudo iwconfig wlan0 rate 54M
(replace wlan0 with your actual WiFi device)
[/B]Disable 802.11n on your router

I tried all of them, and none reliably worked. Every solution which required re-association wtih the AP helped for some time, but nothing helped for long.
First, don't let yourself fool by the disable IPv6 trap - while it is "enabled" it is acutally not used by Lucid!

I have a clean install of Kubuntu 10.04 on an AMD64 Laptop with Broadcom STA driver:
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

However I can reliably stabilize my connection for some time either by manually disabling WiFi with the hardware switch or disabling WiFi by software means and re-activating. This brings speed at par with Kubuntu 9.10 until some time.

Can anybody confirm this behaviour? If so I will file a bug at launchpad.

PS: At bootup my laptop fan speeds consideralby up for ca. 5 Minutes or so. This has already been the case with Kubuntu 9.10. I _think_ I notice the first severe drop of WiFi speed as soon as the laptop fan suddenly stops spinning, which might suggest the whole issue is power save related.

---

