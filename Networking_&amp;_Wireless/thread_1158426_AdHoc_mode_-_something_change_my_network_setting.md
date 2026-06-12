---
title: "AdHoc mode - something change my network setting"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by TheMrOrange on 2009-05-13
Hi all!
I'm goona be mad!
I want to connect two Ubuntu 8.10 laptops in AdHoc mode 802.11a channel 64 using Intell pro wireless ABG 3945, driver iwl3945 but something change my settings![FONT=Courier New, monospace][SIZE=1]
[/SIZE][/FONT]
this is what i did:
[FONT=Courier New, monospace][SIZE=1]# iwconfig wlan0 mode ad-hoc[/SIZE][/FONT][FONT=Courier New, monospace][SIZE=1]
# iwconfig wlan0 channel 64[/SIZE][/FONT][FONT=Courier New, monospace][SIZE=1]
# iwconfig wlan0 essid &#8220;myNet&#8221;[/SIZE][/FONT][FONT=Courier New, monospace][SIZE=1]
# ifconfig wlan0 192.168.1.11 netmask 255.255.255.0[/SIZE][/FONT] 

for the other laptop: [FONT=Courier New, monospace][SIZE=1]192.168.1.12

[/SIZE][/FONT]everything seems to be ok but after few seconds something change settings in 11b and I can't ping between laptops!

I think some kind of process is modifying my network setting but I can't understand which!

Help please!

tnx a million!!!!

---

