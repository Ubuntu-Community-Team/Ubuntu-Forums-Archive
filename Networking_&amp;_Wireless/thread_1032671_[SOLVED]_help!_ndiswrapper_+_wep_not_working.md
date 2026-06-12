---
title: "[SOLVED] help! ndiswrapper + wep not working"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by fibo112358 on 2009-01-06
Hi,

I installed my new wireless pci card, and the driver I installed using ndiswrapper. The driver/card is working, and I can connect through Ubuntu when WEP is turned off. However, when I try to put in my WEP key it won't connect.

In XP, I can connect with WEP enabled. I don't have anymore ideas to try, and for some strange reason, no one on any of the forums is replying to my posts.

1. the chipset id is 10ec:8190 and the card is a Trendnet tew-643pi wireless-n

2. i'm running ubuntu 8.10 on an external hard drive connected to my dell dimension 4600.

3. the driver file is called net8190p.inf

Thank you, I'm in urgent need of help here. Otherwise I've wasted $30 and a lot of time.

---

### Post by llamakc on 2009-01-06
You need to be patient. (I was redirected here after your post about the forum not responding.) 

If you would prefer a quicker answer, I recommend checking out IRC.

---

### Post by albinootje on 2009-01-06
> **fibo112358 said:**
>  The driver/card is working, and I can connect through Ubuntu when WEP is turned off. However, when I try to put in my WEP key it won't connect.


Can you try wicd instead of Network Manager ?
See here :
[http://wicd.sf.net](http://wicd.sf.net)

---

### Post by fibo112358 on 2009-01-07
Ok, I installed wicd and here is the latest:

1. I can connect with my wired eth0 connection.

2. I can connect wirelessly when I disable WEP.

3. I reenabled WEP with a new 128bit hex key, so in wicd under essid I go to advanced->(Hex) WEP with encryption enabled box checked.

Still no connection, and I'm sure my key is correct. I checked my /etc/network/interfaces file and it only shows 

auto lo
iface lo inet loopback

in concordanance with the troubleshooting guide for wicd. If you suggest that I try wpa security, I'm going to need some guidance...I really appreciate it!

---

### Post by albinootje on 2009-01-07
> **fibo112358 said:**
>  If you suggest that I try wpa security, I'm going to need some guidance...I really appreciate it!

First of all WEP is insecure, since quite a while it can be "cracked" relatively easily.

And what's the problem with setting up WPA ?
I assume you're using a wifi-router box, or a DSL-router/modem with wifi ?

---

### Post by fibo112358 on 2009-01-07
I know it's more secure and I've no problem with it, except that when I saw the wpa option and configuration, it didn't look straightforward. It has the following parameters:

group key interval: (set to 3600 default) i guess i leave this alone

802.x (checked)
  server ip address:
  port:
  secret:

psk string (not checked)...what is this? password...it says enter between 8 and 63 characters

I guess I don't mind playing with this, I just don't know what it means so how can I isolate the problem?

---

### Post by fibo112358 on 2009-01-07
on wicd, i also noticed that there are two wpa options

1/2 wpa (passphrase)
1/2 wpa (preshared key)

now does psk on my router stand for preshared key? i assume that i will choose 1/2 wpa (preshared key).

---

### Post by fibo112358 on 2009-01-07
Ok, I connected with wpa! Thanks for suggesting this, you saved my card I was about to send back.

---

### Post by albinootje on 2009-01-07
> **fibo112358 said:**
> Ok, I connected with wpa! Thanks for suggesting this, you saved my card I was about to send back.

Cool! :) Can you mark this thread as SOLVED ? Thanks.

---

