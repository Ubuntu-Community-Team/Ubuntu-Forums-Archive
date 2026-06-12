---
title: "Intel 5100 Unable to Connect to Linksys e2500"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by johnathanamber on 2012-02-05
Hey everyone,

I just bought a Linksys e2500 router to replace my, now bricked due to a failed DD WRT flash (a sad sad moment in my life), WRT54GL.

I've already configured both the 2.4GHz and 5GHz wireless networks. I can connect to the 2.4GHz from my other Windows XP desktop, my BB phone, and my other OS, dual boot with Windows 7, on this laptop.

Using the network manager, no error are displayed, it simply doesn't connect using Ubuntu, actually it is Xubuntu Oneiric 64bit. I have an Intel 5100 wireless adapter.

If I go through the terminal with the following commands:
"sudo iwconfig wlan0 essid <SSID> key <WPA KEY>"

The results are as follows:
"bash: !984: event not found"

I did notice that the error seems to reflect that it can't recognize the password due to the "!".

Any thoughts and help would be appreciated.

Systems Specs:
Xubuntu Oneiric 64bit (doesn't connect)
Windows 7 (connects without issue)
Intel 5100 Adapter
Linksys E2500 (Using WPA2 encryption)

Thank you and God bless,
Johnathan

---

