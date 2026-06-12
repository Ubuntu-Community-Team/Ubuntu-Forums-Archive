---
title: "Share Internet Connection With Xbox 360"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by rizlmilk on 2009-06-06
I know this has been covered hundreds of times throughout these forums, and I can honestly say I have tried the majority of the suggestions in those topics over the dozen times I've tried to do this, but I guess I need some personal help to solve this problem. Any help would be appreciated.

I have my desktop that has a wireless internet connection. I want to share the connection with my Xbox 360 through an ethernet cable. I'm using 9.04 and I have Firestarter installed, which is currently telling me that eth0 is not ready.

Here is my wireless connection information, for what it's worth:
IP Address: 192.168.1.101
Broadcast Address: 192.168.1.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.1.1

---

### Post by spyderpride on 2009-08-27
It's been a couple months, have you got this working yet?

Here's what I did:

After trying everything and having nothing work, I pretty much gave up on reading instructions.  I just so happen to be looking around in System>Preferences>Network Connections>"Edit" Auto eth0 when I realize there is a setting for "Shared to other computers" in the Ipv4 settings tab.  Set it to that, restarted computer and xbox, xbox then connected to xbox live.  Actually there was one little hangup, I had to set xbox to use my router IP for DNS.  Automatic, other than that.  The only problem now is that it is saying my NAT is "Moderate", and I've tried everything again, can't get that worked out.

Let me know if this helps at all.

EDIT: Oh yeah, I would uninstall Firestarter if I were you, it caused nothing but problems for me. Make sure ufw is enabled.

---

### Post by Dlambert on 2011-07-02
This worked great in Ubuntu 11.04. Thank you very much. :KS:KS:KS:KS:KS 5/5

---

