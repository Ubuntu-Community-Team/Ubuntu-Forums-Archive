---
title: "Unable to connect to wireless network using WAP/WAP2 in Ubuntu 10.04"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by captomer on 2010-06-06
1 am using Medion akoya E1210 with Ralink RT2860 wireless adapter. I was using Ubuntu 9.10 and could connect to any secure or unsecured wireless network. Recently I upgraded 10.04. Now I can connect to unsecured networks but on secured networks I am being asked time and again pass phrase despite entering it correctly. Can any body help me rectify the problem. I am not expert in handling such issues.

---

### Post by b k on 2010-06-06
> **captomer said:**
>  Recently I upgraded 10.04. Now I can connect to unsecured networks but on secured networks I am being asked time and again pass phrase despite entering it correctly.
 
Hi there, would just like to offer a suggestion.
 
If you have access to your router and if your current setting for wireless network is with TKIP encryption, try perhaps WPA2-PSK authentication with AES encryption.
 
In other words any combination [COLOR=red]without TKIP[/COLOR] encryption.
 
Hope the suggestion works for you.

---

### Post by Mike Owen on 2010-06-06
> **captomer said:**
> 1 am using Medion akoya E1210 with Ralink RT2860 wireless adapter. I was using Ubuntu 9.10 and could connect to any secure or unsecured wireless network. Recently I upgraded 10.04. Now I can connect to unsecured networks but on secured networks I am being asked time and again pass phrase despite entering it correctly. Can any body help me rectify the problem. I am not expert in handling such issues.

I did this for my Linksys WRT130N since to use 802.11n in that router you need the WPA2, WEP will not work.

As has been mentioned, turning off TKIP (Select only AES) for the encryption mostly solves this problem. This is not indigenous to Ubuntu, also Kubuntu and even Fedora 13. Apparently they use common protocol modules.
:P

---

### Post by darkknight56 on 2010-10-12
I'm using Linksys WRT54G2 and my 9.1 system was able to connect to the wireless network.   Now it repeatedly keeps asking me for the passphrase even though it is entered correctly.  I am using WPA2-Personal with AES.

---

### Post by craber on 2010-10-13
I had the opposite experience. TKIP works for me but AES does not :confused:

I could not get the adapter (Netgear N300/USB) to connect to our router  (D-Link DIR-825) using WPA2 and AES. Finally I got it to work after  setting the router to only TKIP encryption.

---

