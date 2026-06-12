---
title: "issues with aircrack on rt3070 chipset (ubuntu 9.10)"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by zenek89 on 2010-03-12
no **ACKs** with** aireplay-ng** (aircrack-ng)
hello I'm having an issue with **aircrack-ng**, when I use an** aireplay-ng** I don't get any **ACKs** from my network.

I'm using a **RNX-EASYN1** with a **rt3070** chipset on** ubuntu 9.10**
That's my command:
[HTML]
aireplay-ng -0 15 -a 00:1E:52:7A:87:42 -c F8:1E:DF:31:C3:4B ra0
[/HTML]

and that's what comes up after:
[HTML]
18:32:25  Waiting for beacon frame (BSSID: 00:1E:52:7A:87:42) on channel 11
18:32:25  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:26  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:26  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:27  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:27  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:28  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:28  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:29  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:29  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:30  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:30  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:31  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:31  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:32  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
18:32:32  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs][/HTML]

this one is for **my** network, but I tried it for some **other** networks just to check if there's something wrong with my network. But I didn't get any **ACKs** anyway.

I'm not very familiar with **aircrack-ng**, because I just started to play with it, please if there's somebody who's good with using an **aircrack-ng**, **PLEASE HELP ME**.

---

