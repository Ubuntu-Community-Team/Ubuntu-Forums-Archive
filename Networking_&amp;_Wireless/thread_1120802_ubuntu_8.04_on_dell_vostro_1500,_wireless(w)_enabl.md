---
title: "ubuntu 8.04 on dell vostro 1500, wireless(w) enabled but not seeing wireless networks"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by elnuk on 2009-04-09
hello all. i just installed ubuntu on dell vostro 1500.i have wireless(wl) enabled but can't find any wireless networks.pls do i need to install anything to make wireless work.i really need the wireless but i am completely new to ubuntu so keep responses simple please.thanks

---

### Post by michael37 on 2009-04-09
> **elnuk said:**
> hello all. i just installed ubuntu on dell vostro 1500.i have wireless(wl) enabled but can't find any wireless networks.pls do i need to install anything to make wireless work.i really need the wireless but i am completely new to ubuntu so keep responses simple please.thanks

First, how do you know that your wireless is enabled?

A common problem on Dell laptops is Fn-F2 which disables wireless in hardware unseen to Ubuntu -- it will looks like the wireless driver works but you can't see wireless networks.

A few other ideas: 
Check in System/Administration/Hardware Drivers and see if you need to enable any drivers related to your wireless

If you have any other OS on this computer, boot into it and verify that you can see wireless networks there.

---

### Post by superprash2003 on 2009-04-09
also post output of **iwlist scanning** from the terminal

---

### Post by elnuk on 2009-04-09
hey superman,i typed iwlist scanning on the terminal. my result is

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

dont understand much of this but i hope it helps u to help me. checking out ur tutorial now.thanks

---

### Post by elnuk on 2009-04-09
i typed iwlist scanning on the terminal. my result is

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.




i also typed iwlist and got 

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 


dont understand much of this but i hope it helps u to help me. checking out ur tutorial now.thanks

---

### Post by elnuk on 2009-04-09
i typed iwlist scanning on the terminal. my result is

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.




i also typed iwlist and got 

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 


dont understand much of this but i hope it helps u to help me. checking out ur tutorial now.thanks

---

### Post by superprash2003 on 2009-04-10
have you tried the hardware drivers part as mentioned by the other poster?? if that doesnt work .. try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

---

