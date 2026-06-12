---
title: "Maxon BP3 ext on 10.10 not working"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by 63john0 on 2010-12-04
Hi this is my first post here.
I did a quick search but could not find a answer to my problem.
I can get the telstra maxon bp3-ext working on ubuntu 9.04 as that is what i am using now.
But I cannot get it to work on ubuntu 10.10.
Any one have any solution to this problem?
As I would like to move up to the latest version but i need the internet to work.
Why won't my settings from 9.04 work in 10.10?
What settings should i be using in Ubuntu 10.10 for the maxon BP3-ext modem.
Thanks.
John

---

### Post by 63john0 on 2010-12-05
Just tried the modem on Ubuntu 10.04.1 and all works fine.
So why does it not work on Ubuntu 10.10?

---

### Post by RedDogInCan on 2011-01-09
I'm also having problems getting my Telstra Maxon BP3 working with NetworkManager on 10.10.  I can get it to work using Sakis3G but NetworkManager fails whilst trying to establish the PPP connection.

My connection is with Telstra Mobile, which is different from Telstra Bigpond that other users have had success with.  The main difference is Telstra Mobile users a different APN (telstra.internet) and doesn't require a userid/password to connect.

Unfortunately NetworkManager isn't the easiest thing to debug.

---

### Post by PatchesTheCaveman on 2011-01-10
If you select *I can't find my provider and wish to enter it manually* and choose *My provider uses GSM technology* in the Mobile Broadband setup wizard you will be able to manually enter an APN.

---

### Post by RedDogInCan on 2011-01-10
Not sure what you are talking about.  Does NetworkManager have a setup wizard?  I just created a new network connection and entered the APN directly.

---

