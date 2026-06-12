---
title: "no ACKs with aireplay-ng (aircrack-ng)"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by zenek89 on 2010-03-12
hello I'm having an issue with **aircrack-ng**, when I use an **aireplay-ng** I don't get any _**ACKs**_ from my network. 

I'm using a **RNX-EASYN1** with a **rt3070** chipset on **ubuntu 9.10**
That's my command:
[HTML]aireplay-ng -0 15 -a 00:1E:52:7A:87:42 -c F8:1E:DF:31:C3:4B ra0[/HTML]and that's what comes up after:
[HTML]18:32:25  Waiting for beacon frame (BSSID: 00:1E:52:7A:87:42) on channel 11
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
18:32:32  Sending 64 directed DeAuth. STMAC: [F8:1E:DF:31:C3:4B] [ 0| 0 ACKs]
[/HTML]this one is for **my** network, but I tried it for some **other** networks just to check if there's something wrong with my network. But I didn't get any **ACKs** anyway. 

I'm not very familiar with **aircrack-ng**, because **I just started** to play with it, please if there's somebody who's good with using an **aircrack-ng**, **PLEASE HELP ME**.

---

### Post by zenek89 on 2010-03-13
anybody who could help? Please..

---

### Post by brickhead248 on 2010-03-13
sorry, i just started using aircrack yesterday (it's great isn't it!) but don't you use fake auth to get the ACKs? try using attack mode 1 for a bit

---

### Post by reyals140 on 2010-03-14
I never get any acks but the client still gets deauthenticated which is all you need to generate a handshake....
/shrug

---

### Post by zenek89 on 2010-03-14
well, I tried it a couple times, and I got some ACKs.. but didn't get a handshake anyway.  Now when I tried to mess with my drivers I can't get the airodump-ng to work yo ](*,)

---

### Post by zenek89 on 2010-03-16
now my rt3070 chipset works but when I enter airodump-ng it finds only STATIONS but not any of networks. Any guesses? I have at least about 10 networks around me which are shown by the WICD but airodump-ng doesn't show any. I know that I got of from the topic and sorry for that, but I'm trying to get it to work for a couple days already :/

---

### Post by ThatBum on 2010-04-16
You might want to try the GUI for aircrack this guy came up with: GRIM WEPA.

[http://code.google.com/p/grimwepa/](http://code.google.com/p/grimwepa/)

---

### Post by zenek89 on 2010-05-09
but can I use GRIMWEPA for WPA with PSK ?

---

### Post by Kangarooo on 2010-12-02
Yes ucan and also try Wifite i found here [http://ubuntuforums.org/showpost.php?p=9949043&postcount=2](http://ubuntuforums.org/showpost.php?p=9949043&postcount=2)

---

