---
title: "Strange Wifi Problem No MAC ID Repeater"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by VictorMature on 2013-01-20
I am running a Broadcom router in repeater mode with DD-WRT, and I have no problems connecting through the repeater with both Windows XP (dual boot same adapter)  and also with an Android ICS tablet.

When I scan the network with Linux (Xubuntu 12.10 and Fedora 17 LXDE, also with another DD-WRT router "site scan"), I see two instances of the repeater network, and one of the instances will have the correct MAC ID and the other will have a MAC ID that is all nulls.

When I try to connect to either displayed network, it tries to associate with the null MAC ID network and times out.  Here is an excerpt from the system log:

Jan 20 11:51:50 -M2S kernel: [  108.409049] wlan1: authenticate with 00:00:00:00:00:00
Jan 20 11:51:50 -M2S kernel: [  108.424902] wlan1: send auth to 00:00:00:00:00:00 (try 1/3)
Jan 20 11:51:50 -M2S kernel: [  108.628547] wlan1: send auth to 00:00:00:00:00:00 (try 2/3)
Jan 20 11:51:51 -M2S kernel: [  108.832263] wlan1: send auth to 00:00:00:00:00:00 (try 3/3)
Jan 20 11:51:51 -M2S kernel: [  109.035973] wlan1: authentication with 00:00:00:00:00:00 timed out

I tried removing NetworkManager and installing WiCd, but it does the same thing even if I tell it to never connect to the null MAC ID network and automatically connect to the one with the proper ID.

Obviously, there is some sort of problem on the DD-WRT side, but since Windows and Android connect, I'm looking for advice on how to get Linux to ignore the bogus network on the client side.

---

