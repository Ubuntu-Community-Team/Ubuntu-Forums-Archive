---
title: "New to linux, trying to setup multiple network connections"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by theasian100 on 2009-07-02
Hi there ubuntu forum, I installed Ubuntu onto an old desktop of mine so i could use it, and my question is, how do i setup multiple/how do i find network connections? I've tried reading the "help" section on the Network menu and i've been searching and trying for about two days now, Can anyone help me out here? I would like to set this up because my dad uses this computer and all he does is use the internet, Please help me Thanks.

---

### Post by Boondoklife on 2009-07-02
Are you refering to wifi or wired connections, can you give a lil more info.

---

### Post by Iowan on 2009-07-02
Are you looking for multiple *concurrent* connections - or just need to be able to connect to *different* networks?

---

### Post by theasian100 on 2009-07-03
Sorry about the lack of information, forgot i was rambling on, Im talking about Wifi, like if you look on a XP Pc, and you go to connections and you see a list of internet connections you can connect to wheather they be locked or not.



yeah, Im trying to get it so that i am able to connection to Different connections in case if my main one is out

---

### Post by Sjeti on 2009-07-03
Yea, you should have a wireless icon on your gnome panel.
Click on it and it should pop up your available networks. 

Now if you have your card installed and it isn't showing up in your panel, pull up a terminal and type ifconfig.  Give that output to us.  If nothing shows up pull up type in 'lspci -v' and find the one that looks like your network adapter and give us the info.

---

### Post by theasian100 on 2009-07-03
yeah, the thing is that its only picking up my main connection, And i don't think its because of where the PC is placed either, I have my netbook right next to it and it picked up about 9 different connections
and the Ubuntu Desktop only picks up one connection, is it the card fault? I'd tell you the model but right now i can't open it, is it possible that it''s the card is not strong enough?

---

### Post by superprash2003 on 2009-07-03
post output of **sudo iwlist scanning** from the ubuntu terminal(Applications->Accessories)

use copy paste method to paste outputs here

---

### Post by theasian100 on 2009-07-05
I did the "sudo iwlist scanning" and this is what popped up

le Interface doesn't support scanning.

wmaster0 interface doesn't support scanning.
wlan0 Scan completed :
Cell 01 - address 00:24:b2:2F:09:Ba
Essid: "Uber Noob"
Mode: master
Frequency: 2.462 ghz (channel 11)
Quality=50/11 Signal Level= -60dbm
encryption key :on
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : PSK
Bit Rates: 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9Mb/s; 12 Mb/s; 48 Mb/s

Extra:tsf=000000008018ca6f

Eth0 Interface doesn't support scanning

---

### Post by theasian100 on 2009-07-06
bump

---

### Post by puppywhacker on 2009-07-07
if "sudo iwlist scanning" only found one cell and the network icon found only one access point as well it means the rest of the access points were too weak to pick up. you can tweak a bit with the txpower settings on the card using iwconfig. But I doubt it will produce useful connections.
```
iwconfig wlan0 txpower auto
```

---

### Post by theasian100 on 2009-07-07
I see,
Would this card be able to plug in and use?
[http://www.frys.com/product/4833770?site=sr:SEARCH:MAIN_RSLT_PG](http://www.frys.com/product/4833770?site=sr:SEARCH:MAIN_RSLT_PG)

Im trying to get this done soon so i won't have to worry about anything :/

---

### Post by Boondoklife on 2009-07-08
I always liked this site for looking at if hw will work.
[http://www.linux-drivers.org/network.html](http://www.linux-drivers.org/network.html)

---

### Post by irv on 2009-07-08
> **theasian100 said:**
> yeah, the thing is that its only picking up my main connection, And i don't think its because of where the PC is placed either, I have my netbook right next to it and it picked up about 9 different connections
and the Ubuntu Desktop only picks up one connection, is it the card fault? I'd tell you the model but right now i can't open it, is it possible that it''s the card is not strong enough?
I replaced the gnome network manager with wicd network manager and it fines all the network connections no matter where I am. I am at home right now, and if all my neighbours have there networks on line, I can see five of them. Right now I and the hotel across the street are on line and here is what I am seeing. See screen shot.
[ATTACH]120346[/ATTACH]
I never saw the other connections when I was using Gnome network manager. I think wicd works much better. Give it a try, if you don't like it you can always go back.

---

### Post by theasian100 on 2009-07-08
So i just went to frys and they didn't have the card i wanted, it was discontinued. I bought the next card, The DWA - 552, I installed in card into my computer and Now I'm stuck, I downloaded the Madwifi zip from my netbook and put it on a flash drive, The flash drive is now in my Ubuntu desktop, What do I do now?

---

### Post by irv on 2009-07-11
> **theasian100 said:**
> So i just went to frys and they didn't have the card i wanted, it was discontinued. I bought the next card, The DWA - 552, I installed in card into my computer and Now I'm stuck, I downloaded the Madwifi zip from my netbook and put it on a flash drive, The flash drive is now in my Ubuntu desktop, What do I do now?

If you downloaded a zip file, are you sure you have a Linux driver or a windows driver in the zip. I am not sure what you are trying to do? If you put in the new card I would think that ubuntu would know you made the change and you might have to chance a configuration file somewhere but not load a driver. Maybe I am missing something here, or maybe I am wrong?

---

