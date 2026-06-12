---
title: "a question about WEP 40/128-bit (what's the real key?)"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by shva on 2009-04-25
I tried to connect to the encrypted wireless under command line. My target network is encrypted with WEP 40/128-bit. What I did is:

# ifconfig wlan0 up
# iwlist wlan0 scan ( and I see my target wireless network is there)
# iwconfig wlan0 essid "My_Network" key s:0123456789
# dhclient wlan0

But it did not work, dhclient just could'nt get in touch with the router.

I heard that WEP allows keys like:

64-bit: 5 characters
128-bit: 13 characters
256-bit: 29 characters

But here mine is 10-character, which was what I used to connect to wireless with Ubuntu Network Manager, successfully. So can anybody tell me what is the real key of my WEP? Thank you a lot.

---

### Post by chili555 on 2009-04-25
# 40-or 64-bit ASCII WEP code has 5 characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters

Only if your key is ASCII should you precede it with **s:**. Since you have 10 characters, we know it's HEX.

Finally, as far as I know, very few vendors have implimented 256-bit WEP and I have never seen it implemented in Ubuntu. I suspect people that want a more secure connection have moved to WPA.

---

