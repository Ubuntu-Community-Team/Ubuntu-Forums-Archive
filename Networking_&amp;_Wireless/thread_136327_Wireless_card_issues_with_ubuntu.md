---
title: "Wireless card issues with ubuntu"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by RjBanker18 on 2006-02-25
Hi, well first of all i try to put my wireless card into managed more using
sudo iwconfig ath0 mode managed

But i cannot connect to my wireless network even though it appears.  its a WEP 128bit encryption and i gave my wireless card the ESSID and WEP key, i know its supposed to work b/c i get full connection in windows to my router and in ubuntu i can see the network and attempt to connect to it. 

In another troubleshooting attempt i typed in...
iwlist scan 

i get all the right information but the only odd thing is that is is always in Mode:Master after i try to put it into managed mode.  i can put it into monitor mode so obviously it is not completely stuck in Master mode.

I guess my real questions are..Why can't i connect to my wireless router?
Why is it in Master mode when i specifically told it to goto managed mode?

**EDIT**
Ok well i just found out that my DHCP server is not giving DHCP information over wireless connections.  It is giving DHCP for wired connections but not wireless.  I have my main internet line going into a server then into a wireless router.  Any suggestion on how to get it to work? Please I need help!!!
Hopefully i have given enough info. to troubleshoot it.

---

