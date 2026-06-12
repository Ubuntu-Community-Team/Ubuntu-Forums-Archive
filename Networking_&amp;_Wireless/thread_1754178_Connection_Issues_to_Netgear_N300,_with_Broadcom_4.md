---
title: "Connection Issues to Netgear N300, with Broadcom 4328"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by bhaarat316 on 2011-05-09
I'm having issues connecting to my Netgera N300 router with my Broadcom 4328 card.  I got the wireless card to work after going through a bunch of sites and looking for a solution.  I don't even know what I did, since I'm very new to this.  

Anyways my wireless can search, then it ask me for my password so I change it to the WPA2-PSK, enter password and it just never connects.  It then repeats the password process.  Also can't seem to install the STA driver I get the error /var/log/jockey.log. 

I'm pretty sure i'm running 10.10.

Edit: I'm running 10.04 and want to update it as well.

---

### Post by AllanM on 2011-07-16
Hi. I have exactly the same issue on an hp 4515s using broadcom 4322. I'm on 11.04 and can see the choice of wireless networks fine but when I try and connect to my router with the correct password it never completes. The wireless indicator sweeps bottom to top but then keeps prompting or a password. A galaxy tab and (spit) win7 sony connect fine. Hmmm. Will keep searching for an answer. Good luck. Allan.

---

### Post by pakidevil on 2011-07-16
lets first check, what release you got ...

[COLOR=Red][B]lsb_release  -a 


[/B][/COLOR]it will tell you what release you are using.

---

### Post by Tenorman on 2012-01-08
I'm having the exact same issue with ubuntu 11.04 32-bit.  I'm just trying out the usb netgear on my laptop at the moment, but want it to work on a pc that I'm getting tomorrow, which will have the same install of ubuntu put on it.

---

### Post by Tenorman on 2012-01-08
I have also just tried the Netgear N300 on a netbook running ubuntu 11.10, and got exactly the same result - repeated requests for the wpa encryption key and no connection.  The method I used both times was to install the Broadcom bcm43xx drivers using ndiswrapper.  The device is recognised by each machine, and will pick up several wifi signals from me, neighbours,etc, but will not recognise the wpa encryption key - it is correct btw, as the built-in wireless cards on both machines use the same key and connect with no problems.

---

