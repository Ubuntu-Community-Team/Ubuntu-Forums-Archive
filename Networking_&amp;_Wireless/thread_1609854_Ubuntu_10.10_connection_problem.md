---
title: "Ubuntu 10.10 connection problem"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by Mrbronz on 2010-10-26
> **sparkzema said:**
> Ok, I had a fresh install of Ubuntu 10.10 after my backtrack 4 install stopped working.(bluetooth messed with hal or something mouse and keyboard wouldnt work) I plug my D-link G-122 (old laptop without built in wifi) and network manager recognized instantly. But whenever I connect to a network I can't get to the internet. It will connect and say its connected, but no internet. It's the exact same thing on my desktop. Any help is appreciated.
Have you had any luck with this?

I have same problem with Dell Inspiron 1545... I have 2 other laptops A gateway and an Advent connecting to the network and to the Internet. But for some strange reason the Dell will not connect to the Internet I can ping the router but nothing on the other-side of it.

My next step is to role back to 10.04

Unless anyone has any ideas

---

### Post by Iowan on 2010-10-26
Ordinarily, I'd point you to a separate thread (might yet - if this takes off). Check the previous request to see if the machine gets an IP address - and if it's using the proper gateway (router?). Pinging the router would suggest the interface has an IP address, but the gateway...?

---

### Post by faheemezani on 2010-10-27
> **Mrbronz said:**
> Have you had any luck with this?

I have same problem with Dell Inspiron 1545... I have 2 other laptops A gateway and an Advent connecting to the network and to the Internet. But for some strange reason the Dell will not connect to the Internet I can ping the router but nothing on the other-side of it.

My next step is to role back to 10.04

Unless anyone has any ideas

I also faced the same problem but somehow managed to get my WiFi connection access to the Internet working fine. Prior to this, result from** ifconfig** confirmed that I had an IP address (DHCP) via WiFi connection. However, I could not access the Internet through Firefox. Judging from this state, I initially thought that there was something wrong with the WiFi router but then my Empathy messaging client could still receive Twitter messages and connect to my YM account - ultimately weird!!

I came to a conclusion that this might have been due to Ubuntu's inability to get hold of the DNS server's IP address (yet to verify). So, I manually set my wireless interface and DNS IP address at **System** > **Preferences** > **Network Connections** and voilà - it worked!

---

### Post by Mrbronz on 2010-10-30
> **faheemezani said:**
> I also faced the same problem but somehow managed to get my WiFi connection access to the Internet working fine. Prior to this, result from** ifconfig** confirmed that I had an IP address (DHCP) via WiFi connection. However, I could not access the Internet through Firefox. Judging from this state, I initially thought that there was something wrong with the WiFi router but then my Empathy messaging client could still receive Twitter messages and connect to my YM account - ultimately weird!!

I came to a conclusion that this might have been due to Ubuntu's inability to get hold of the DNS server's IP address (yet to verify). So, I manually set my wireless interface and DNS IP address at **System** > **Preferences** > **Network Connections** and voilà - it worked!
Thanks Faheem

I did as you suggested and went to **System** > **Preferences** > **Network Connections **and noted that for some reason (Only known to my subconscious) that I had in fact chosen **Automatic(DHCP) Addresses** only in the **IPv4** settings after setting back to **Automatic (DHCP)** disconnecting the wifi connection and re-connecting the wifi I then opened a fire fox and hey presto its working.

Ta very much

MrBronz

---

### Post by Iowan on 2010-10-30
Moved to a new thread so you can mark it [SOLVED] (under Thread Tools) and perhaps help someone else with a similar problem.

---

### Post by Zacinfinite on 2011-03-14
SAME HERE. As soon as I installed 10.10 my internet works no more than 3min. After which I have to restart again.
USB devices also dont work properly. External harddisk shows input/output error.
Certainly Ubuntu 10.10 is not stable for regular user.

---

