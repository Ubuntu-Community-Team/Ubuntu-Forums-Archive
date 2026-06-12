---
title: "University network"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by mattwestm2 on 2013-08-20
Hello,

I am able to connect to my university wireless network with xubuntu, however, it works fine with Windows 7 and my Android phone. I believe it to be a certificate issue. However, their instructions make no mention of a security certificate (which is usually obtained automatically using Windows). BTW, wifi works fine at home on my router and on public wifi networks.

When I try to connect, it will usually "think" for about 30 seconds, then prompt me for my username and password. This process continues time after time. I am 100% sure that my username and password are correct.

My university calls for the following settings:


[LIST]
[*]Wireless Security:** WPA2 Enterprise**
[*]EAP Method: **PEAP**
[*]Key Type: **Automatic (Default)**
[*]Phase2 Type: **MSCHAPV2**
[*]Identity: ***domain\username***
[*]For the password, type your Active Directory password.
[*]If you see PEAP version option, choose PEAP version 0.
[*]Leave all other options at the default settings.
[/LIST]

---

### Post by Rsxhawk on 2013-08-29
Sounds like they're doing 802.1x over the wireless which does use a Certificate.  I've never connected an ubuntu wireless client to an 802.1x wireless network, but I imagine it should authenticate you the same way as a windows client would.  Only way to know for sure would be to run a wireshark trace on your ubuntu machine or have your school check the active directory security audit logs on the domain controller to see why your Ubuntu client is failing.  If you know your same AD credentials work on Windows 7 and on your Android phone, then I doubt its a username/password issue.  I'm pretty sure there is a way to monitor your ubuntu clients syslog to see what its doing during the connection attempt.

---

