---
title: "Ubuntu 8.10 sees wireless networks but not mine"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by Derko on 2009-03-14
I installed Ubuntu 8.10 on my laptop with Intel 5300AGN adapter.
Windows Vista on the same laptop sees and connects to my home wireless network, but Ubuntu sees other wireless networks but not mine.
I have U.S. Robotics Wireless MAXg Router (USR5461)and this is set to Method:  	WPA2 (PSK)
Encryption: 	TKIP and AES

It confuses me that Windows XP works and Ubuntu not, so router and Intel adaper seems ot work together. Why not in Ubuntu ?

Please help me out.

Derko

---

### Post by sgosnell on 2009-03-14
Is the router broadcasting the SSID?

---

### Post by inobe on 2009-03-14
the very first thing i thought !

it's common even in windows to not locate a broadcast ssid...........

been there' done that :)

you may need to manually enter the ssid and setup the security' especially if it doesn't find your network after a reboot.

---

### Post by Derko on 2009-03-14
This is what my router reports:
 
Wireless
Wireless: 	Enabled
Network name: 	code1312
Broadcast name: 	Enabled
Mode: 	Access Point
WDS restrictions: 	Disabled

So broadcast is on and Windows sees code1312.

Derko

---

### Post by inobe on 2009-03-14
what do you see when you right click the wireless and select edit connections and click wireless tab....... ?

---

### Post by mikewhatever on 2009-03-14
Try changing the channel your router uses.

[http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945](http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945)

---

### Post by Derko on 2009-03-15
mikewhatever wrote:

>Try changing the channel your router uses.
>[http://www.ubuntu.com/getubuntu/rele...20Intel%203945](http://www.ubuntu.com/getubuntu/rele...20Intel%203945)

And that did the trick. I changed the router's channel from 13 to 15 and it worked !

Thank you.

Derko

---

### Post by Derko on 2009-03-15
Detail: I mean from 13 to 10.

---

### Post by sgosnell on 2009-03-15
OK, good.  It doesn't matter which channel worked, because it's different every time.  It depends on how much interference you're getting from other devices.

---

