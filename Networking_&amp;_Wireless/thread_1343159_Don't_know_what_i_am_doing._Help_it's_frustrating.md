---
title: "Don't know what i am doing. Help it's frustrating"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by dendan on 2009-12-01
I have just installed ubuntu9.10 on a hp pavilion dv6000,previously running windows home premium. i can connect to the internet via my ethernet cable from my xbox360, but i do not know how to connect wirelessly.
Please i do not know what to do if you give me short answers like download driver. I am new using linux. I have been on madwifi and ndwiswrapper but do not have a clue. I click on my network manager icon and i see 

Wired Network
Auto eth0
Disconnect
VPN Connections >

I thought i was going to see my home network but nothing.

---

### Post by bkratz on 2009-12-01
> **dendan said:**
> I have just installed ubuntu9.10 on a hp pavilion dv6000,previously running windows home premium. i can connect to the internet via my ethernet cable from my xbox360, but i do not know how to connect wirelessly.
Please i do not know what to do if you give me short answers like download driver. I am new using linux. I have been on madwifi and ndwiswrapper but do not have a clue. I click on my network manager icon and i see 

Wired Network
Auto eth0
Disconnect
VPN Connections >

I thought i was going to see my home network but nothing.


Do you know what is your wireless card?  If not, go to Applications--Accessories--terminal  a small screen will open up. type in    lspci -nn     (LSPCI in lower case) and either copy and paste the output here or look at it carefully to determine wireless card details. Then close that window.   Are you running 32 bit ubuntu or 64 bit?


While in the terminal you might as well post the outputs of   lshw -C network  (That is LSHW in lowercase note capital C) and iwlist scan  .

---

