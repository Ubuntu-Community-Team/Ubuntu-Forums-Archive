---
title: "BCM4311 and iwconfig"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by devosion on 2009-06-28
I've been using my Broadcom card on my laptop for several versions of ubuntu now. Currently im running xubuntu 9.04 and using the network manager applet with b43-fwcutter flawlessly. Earlier I played around with Slackware only to become frustrated with iwconfig. Now that i've installed xubuntu, and tried to use openbox and iwconfig, im finding I have the same issues I had with iwconfig as I did in Slackware. 

The problem is that when I attempt to setup iwconfig the settings do not seem to work. Currently my /etc/network/interfaces is setup like this.

> 
iface wlan0 inet dhcp
wireless_essid xxxx
wireless_mode Managed
wireless_key xxxx


It's a very simple configuration for the time being. When I check to see if iwconfig has taken the changes, after restart, it remains blank. And only when I set the option from the command line do they change, but i'm always having issues with iwconfig taking the password (ASCII). Strangely enough, when I run iwlist wlan0 scan via terminal it reports the device doesn't support scanning. This isn't obviously the case because under the network manager app in xfce I can see a full list of all available networks. 

I would really like to spend some time with more minimalistic distributions of linux, or at the very least enjoy the functionality of the likes of fluxbox or openbox, but until I can setup iwconfig I won't be able to. And without an available ethernet connection my only option is wireless. Please assist.

---

### Post by kevdog on 2009-06-29
wireless_key

Its either of the format 
s:<ascii password>
<hex key>

So if you want to use ascii its assuming the password is fred:

wireless_key s:fred

---

