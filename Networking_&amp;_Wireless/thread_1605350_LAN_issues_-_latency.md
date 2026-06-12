---
title: "LAN issues - latency"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by matoxxx on 2010-10-25
Hi everybody, 

I am looking for some help regarding small home network issues.

I had setup at home a small private network consisting of cable modem, wireless AP (Realtek 8186 based chipset) and 2 client PC's.

I am connecting desktop PC through LAN and laptop via WLAN (both are up-to-date Lucid). AP was setup for QoS and DoS at default values.

Both clients have good latency to WAN at same rate, without packet loss, and network traffic shaping is working flawlessly as well.

The problem arise when we want to play games over LAN. We have installed Pioneers (Settles of Catan based game) on both machines, and setup a game on one of them (desktop) as localhost, and connected laptop through direct IP/port. The issue is, there is a great delay in gameplay for the connecting machine.

As troubleshooting I had setup the game reversibly on the laptop, and the same problem occured for the desktop PC. When I did ping the machines between themselves

laptop>desktop ping avg. 7ms (more than one would expect) few packet loss
desktop>laptop ping avg. 5000ms more than 60% packet loss

We live in flat-house so I expected there is interference from neighboring wireless networks, but from the SSID broadcasting networks we are alone on our channel. I have checked iptables,and both machines are permissive in all connections. Now I am out of ideas, where the problem might lies in. Any fond people to give me a hint where to start to search ?

---

### Post by carl.davis on 2010-10-25
Hello,

Could you use a wired connection for the laptop and see if the latency remains?

Also, with the laptop wirelessly connected, does moving closer for farther from the AP change the latency?

---

