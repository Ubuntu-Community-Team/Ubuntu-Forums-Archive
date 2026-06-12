---
title: "Wicd wont update SSID's"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by crucialhoax on 2009-12-10
Hello all,

I was tinkering with a new router I just purchased WRT54GL. I flashed it with dd-wrt mini and changed the SSID to omega, no one has that in my area, easy to identify. Well anyway, when I change it to anything else like back to defaults, Wicd still shows omega. I also have another wireless router in my house, a DIR-615. Its SSID is beta. and whatever I change its SSID to it stays the same in Wicd as well. The reason I'm asking is because if I dont change it back to 'beta' or 'omega' it wont connect. Wicd stops at verifying access point... Why is that? Any tips hints? I want to learn why this is happening. Any help is appreciated :)

System:
Ubuntu 9.10
BCM4322 Wifi Card with broadcom drivers
Wicd 1.6.2.2

---

### Post by crucialhoax on 2009-12-14
Anyone?

Also, it randomly drops connection (wireless) as well.

---

### Post by crucialhoax on 2009-12-16
bump...

---

### Post by Guitar John on 2009-12-16
> **crucialhoax said:**
> 
Also, it randomly drops connection (wireless) as well.

Just out of curiosity, why Wicd rather than Network Manager.  I am asking because I had similar problems during my brief fling with [Zenwalk]("http://www.zenwalk.org/"), which uses Wicd by default.

---

### Post by crucialhoax on 2009-12-17
Network manager was limiting my speed to >100kb/s and thats unacceptable. Other than that it never really dropped or anything, it was just really slow. Wicd allows normal operation but it has 2 flaws. For some reason it won't update my AP information and it drops connection sometimes. Never during a download though, its always when my system is at idle.

---

### Post by Guitar John on 2009-12-19
> **crucialhoax said:**
> Network manager was limiting my speed to >100kb/s and thats unacceptable. 

REALLY!?
Mine is at 36Mb/s, at the moment.  I wonder why that is?  Maybe,the Broadcomm Drivers.  Anyway, I wish I new what to tell you about your issue with Wicd.  I am hoping someone will chime in here.

---

### Post by crucialhoax on 2009-12-22
Yeah, I hope so too. Wicd is all screwed up. It says I'm on channel 4 when I'm really on channel 2, it won't update SSID's it just seems like its not getting the correct info or something.

---

### Post by crucialhoax on 2009-12-23
I switched back to gnome-network-manager and the speeds are so slow. It says the connection speed is 54mb/s but I am only downloading at <200kb/s. So I either get a stable connection with network manager but slow speeds or use wicd and have high speeds but drop every few days. How can I fix this? I know there has to be someway to fix this.

I'm using a BCM4322 wireless chip, the broadcom hybrid linux driver, and network-manager.

Please someone help!

---

### Post by crucialhoax on 2009-12-31
Hello,

I went back to wicd and I think I'm starting to understand that wicd is just a front end GUI to iwconfig and ifconfig. So I started messing with iwconfig to get the channel settings correctly. iwonfig is in the 'Managed' mode and Wicd is displaying I'm on channel 4, my wifi router is set to channel 2. Iwconfig is saying channel 4 as well as iwlist. So how is it that my router is set to channel 2 but my Ubuntu is telling me channel 4?

---

### Post by crucialhoax on 2009-12-31
Bump,

I just had it disconnect on me for no reason. I've checked all of the logs, even the wicd.log and nothing seems abnormal. I have no clue why it keeps disconnecting. the good thing is that it re-connects right away.

---

### Post by crucialhoax on 2010-01-05
to the tizzzzop

---

