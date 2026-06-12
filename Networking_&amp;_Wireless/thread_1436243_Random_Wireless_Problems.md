---
title: "Random Wireless Problems"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by quizno50 on 2010-03-22
Hello all,

I'm having random wireless problems using an Asus EeePC900. It works like a champ when I'm at my apartment (no encryption completely open 802.11b). But when I'm on my University's Campus (which uses some kind of user-based encryption/authentication) I have issues when I'm online. I can connect and use the connection just fine for a while, but after time, it starts failing. I try and ping my gateway and get "Destination Host Unreachable". I look through everything I can think of: iwconfig says everything's fine. ifconfig says wlan0 has an IP address and everything's good. I check route, it pops up two really fast, then after a small delay the default GW comes up. Lastly I checked through dmesg and got the following:

```
[ 2144.941016] wlan0: authenticate with AP 00:0f:7d:03:16:92
[ 2144.942514] wlan0: authenticated
[ 2144.942520] wlan0: associate with AP 00:0f:7d:03:16:92
[ 2144.949063] wlan0: RX ReassocResp from 00:0f:7d:03:16:92 (capab=0x431 status=0 aid=129)
[ 2144.949070] wlan0: associated
[ 2176.673838] ath5k phy1: unsupported jumbo
[ 2310.921739] ath5k phy1: unsupported jumbo
[ 2433.493342] ath5k phy1: unsupported jumbo
[ 2472.440174] ath5k phy1: unsupported jumbo
[ 2474.146347] ath5k phy1: unsupported jumbo
[ 2476.167124] ath5k phy1: unsupported jumbo

```

I also notice that even though I'm getting the "unsupported jumbo" thing, for the most part; it keeps working... I'm really lost on this one, let me know if you have any ideas. I'm really thinking the problem has something to do with the encryption, but I'm no expert on that.

EDIT: I forgot to mention, if I disconnect and reconnect with NetworkManager it starts working again, but after time it'll still fall apart...

---

