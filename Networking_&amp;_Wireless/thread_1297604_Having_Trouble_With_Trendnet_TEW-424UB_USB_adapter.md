---
title: "Having Trouble With Trendnet TEW-424UB USB adapter"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by sir_robert007 on 2009-10-21
Hey I've been having trouble getting a Trendnet TEW-424UB USB adapter to work in Ubuntu 9.04 64-bit after performing system updates. When I first installed Ubuntu on my system, I connected the adapter, connected to my network via WPA2-PSK encryption and the adapter worked just fine, but after I performed system updates, I was unable to connect to my network. The nm-applet indicated that the adapter was trying to connect to the network, but after a while a box popped up saying "Authentication required by wireless network". It provided areas where you can enter the encryption method and the password to the network. The encryption was already set to WPA2-PSK and the password to my network already entered, so I clicked connect. It tried again to connect but the same box popped up. I even tried restarting but I still keep getting the same result. I should mention that during system updates, the update manager updated the linux kernel from 2.6.28.11 to 2.6.28.15. Would this be the cause of the problems I'm having?
 
_Comp Specs_
Ubuntu 9.04 64 bit
AMD Phenom II X4 810 2.6 Ghz
4 GB ram
Trendnet TEW-424UB USB adapter (Realtek RTL8187B chipset)

---

### Post by zs735 on 2009-10-30
I am having the same issue; i can see the network and have put the wpa key but it does not connect.

---

### Post by zs735 on 2009-11-01
Got mine to work. I had to download latest version of ndiswrapper. Thereafter, i was pleasantly surprised. I followed the notes in sourceforge.net in setting it up.
I had airlink before and could never get that to work.
Check your mac address if you are filtering on the router as well. wlan0's address needs to be copied.

---

