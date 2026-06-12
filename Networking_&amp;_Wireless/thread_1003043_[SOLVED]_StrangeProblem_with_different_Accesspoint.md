---
title: "[SOLVED] StrangeProblem with different Accesspoints"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by prefec2 on 2008-12-05
I have a new Dell vostro 1510 notebook (actually I have to configure and set up two vostro 1510) with a Broadcom BCM4312 802.11b/g WLAN chip. It works perfectly with one accesspoint (Fritzbox based Speedport W701) however it does not work with a D-LINK and another Fritzbox.

All accesspoints are set up in the same way:
Encryption Type: WPA/WPA2 Personal
Alg: TKIP CCMP

I've searched the net, but I cannot find anything which explains the problem. I did run wpa_supplicant with debug option -dd for all accesspoints. 

I could find the following differences:

== log of the working AP ==
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
== end ==
== log of not working AP ==
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 16 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
== end ==

and later the not working AP produces

== begin ==
RSN: Ignored PMKID candidate without preauth flag
== end ==

I would appreciate any suggestions which might help me to solve this puzzle. I attached both logs as further documentation

Thanks
  Reiner

---

### Post by jmoorse on 2008-12-07
Just a thought:

Verify the second AP is using WPA/TKIP (as the first is).  It looks as if it is trying WPA2.  When in doubt, upgrade the firmware.  D-Link has had some crappy firmware releases...

Also is the last AP using Shared Authentication instead of Open?

---

### Post by prefec2 on 2008-12-09
You are absolutely right. The other APs are using WPA2. I switched them now back to WPA TKIP. However I am a little bit surprised because the network-manager asks for a key (psk) for WPA+WPA2.

So I will look into the issue and try to fix WPA2 support if possible.

---

