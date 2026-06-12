---
title: "Intermittently Lose Connection - Frequently - Not a problem on Windows"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by LeHerp on 2011-10-30
I'm dualbooting between Windows and Ubuntu and have encountered a problem with my internet connection that is only apparent on Ubuntu. I will intermittently lose connection and be forced to either disconnect then reconnect to my router or delete the connection altogether and reenter the security key etc.

This is my network setup, if that helps. I really have no idea why it's doing it, possibly a missing driver.

[IMG]http://imgur.com/MRhXh[/IMG]

It can go for long periods and be fine but then I can get disconnected 4-5 times in as many minutes.

Thanks for the help.

---

### Post by HermanAB on 2011-10-31
Using WiFi or Ethernet?  Some older (mainly Broadcom) WiFi devices have bad device drivers in Linux.  The only solution is to get a different WiFi dongle.

---

### Post by LeHerp on 2011-10-31
> **HermanAB said:**
> Using WiFi or Ethernet?  Some older (mainly Broadcom) WiFi devices have bad device drivers in Linux.  The only solution is to get a different WiFi dongle.

Wireless. Ideally, I wouldn't want to do that. It just seems illogical that it happens in such a random way.

---

### Post by macflav on 2011-10-31
It's been happening to me also. I don't remember having this issue with 11.04 (Natty). PS: I'm using 11.10.

---

### Post by PKTB on 2011-10-31
I'm experiencing this a couple times a day as well since the do-release-upgrade to 11.10. Ubuntu Server, dual wired ethernet, cable, acting primarily as a router. After it upgraded, during the bootup, it now tells me that it is waiting for a network configuration response. This goes on for a couple minutes before falling through to the normal blank screen. Logging in I find that the ISC DHCP server hasn't started. I'll restart that and bind (to be safe), which works fine. Running sudo dhclient ETH# will half work. It gets an ip, and routing resumes after a second, but it hangs on the "RTNETLINK answers: File exists" line, seemingly, for all of eternity. Been researching this for a couple days now and the only hints I have might have something to do with a LINKDELAY setting in a file that no longer exists.

update: no new information on the problem. I installed 11.04 w/dnsmasq to a different harddrive and remade the router, basically.

---

