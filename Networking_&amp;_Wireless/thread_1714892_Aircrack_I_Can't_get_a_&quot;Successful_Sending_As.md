---
title: "Aircrack: I Can't get a &quot;Successful Sending Association Request&quot;"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by WLLD on 2011-03-26
Hello everyone.
So I have this problem for days with the aireplay-ng ... after typing the following
Code

sudo aireplay-ng -1 0 -a F4:EC:38:xx:xx:xx -h 00:11:22:33:44:55 mon0

I keep having this problem 
Code

The interface MAC (00:21:00:xx:xx:xx) doesn't match the specified MAC (-h).
	ifconfig mon0 hw ether 00:11:22:33:44:55
13:41:59  Waiting for beacon frame (BSSID: F4:EC:38:..:..:..) on channel 1

13:41:59  Sending Authentication Request (Open System)
13:41:59  Authentication successful
13:41:59  Sending Association Request
13:41:59  Got a deauthentication packet! (Waiting 3 seconds)

13:42:02  Sending Authentication Request (Open System)
13:42:02  Authentication successful
13:42:02  Sending Association Request
13:42:02  Got a deauthentication packet! (Waiting 5 seconds)
....
....
if anyone knows what's wrong ... thanks

---

