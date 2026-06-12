---
title: "Interface through proxy HELP!!"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by phamash on 2012-04-28
First I want said that my english is not good, but I try to explain the most clear possible
I have a server with 2 interfaces and I want make anonymous all the traffic through the server, something like this

Eth0 (internet acces) -------server with vidalia---------------wlan0 (clients)

Soo. I have created a adhoc wifi, and this intercafe give internet to the clients but I want change the configuration to make shomething like this

eth0------server------vidalia-----------wlan0

I want change the configuration only in the server, I tried with squid3 without results, and I won't change or add a local proxy in each machine of the clients, I want redirect all the traficc of wlan0 through 127.0.0.1:9050
Please help me

---

