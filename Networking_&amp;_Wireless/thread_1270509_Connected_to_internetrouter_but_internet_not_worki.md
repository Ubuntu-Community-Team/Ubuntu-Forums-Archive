---
title: "Connected to internet/router but internet not working"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by xDiiaZz on 2009-09-19
Hello, I have been trying to get my internet working for a computer which I recently booted with Ubuntu 9.04 so I'm new. It has been at least 8 hours altogether for me trying to get the internet to work.
 
The thing at the top that shows the networks (I'm guessing this is the Network Manager) shows 2 green lights but it keeps circling around it, meaning it's not actually working, no signal. Then I edited my wireless connection and under the "Ipv4 Settings" tab I changed the "Method" to "Shared to other computers." The internet/ router was connected and I got a signal but for some reason, I tried going on the internet and the pages don't work.
 
If you don't know yet, I connect to the internet using Wi-Fi and I have two other computers that connect to the internet. Back to my Ubuntu computer I use a Belkin 11Mbps Wireless USB Network Adapter to connect to the router.
 
I have tried connecting to someone else's network and it worked, I could connect to the internet with it.
 
BTW, I have a 128bit WEP encryption for my Wi-Fi and I have MAC address control on but this isn't the problem. I also use the Wireless channel 11 for my router.
 
Please help! Thank you!
 
 
 
 
I don't know what to do, it seems that the internet should work but it doesn't. Like I said before when I had Automatic DHCP, there is a connection but no signal. It just keeps circling and circling, never getting a signal. I don't know what's the problem.
 
I think there's a problem with the DHCP thing or the part where it is trying to do IP configuring.

---

### Post by Iowan on 2009-09-20
Static address or DHCP? Probably not your solution, but [this]("http://ubuntuforums.org/showthread.php?t=1156441") fixed my wired network problem.

---

### Post by lswb on 2009-09-20
Change the edit you made for IPv4 sharing back to DHCP. Most routers act as DHCP servers for their local net, you would know if you changed it (Or if someone else set up the router, ask them)

You mentioned that you are using MAC filtering, I assume you have done this on the router. Make sure that you have it set for the MAC of the wifi adapter on the ubuntu system and not an ethernet or other MAC on the same computer.

When you enter the WEP key, if it is hex string, make sure that you have checked off "WEP 40/128 bit Key" as the type rather than "WEP 128 bit passphrase"

---

