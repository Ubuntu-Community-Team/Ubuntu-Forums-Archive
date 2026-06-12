---
title: "Configure PuTTY for terminal logon over Sonicwall VPN"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by fiddlerdave on 2010-09-17
Well, dazed and confused. This is about a Windows7 computer trying to use PuTTY to connect to a Linux host tect terminal over the internet on a supplied (and required) Sonicwall Global VPN client.
 
A customer has placed my Linux host behind a Sonicwall router, and has given me a Sonicwall Global VPN connection to log on to this host. It is to log into one of the terminal text mode (not X terminal). (This computer is a machine controller, not using any graphics).
 
I normally use PuTTY for the remote logon, and either through a router port forward or simply opening a port for the host on a router, logging in is no problem over the internet.
 
The customer is insisting on the VPN, and it seems to set up fine. But I cannot connect to the host. I configure PuTTY with the "PEER" IP address shown in the Sonicwall client on my remote computer (Windows7 64 bit) but the connection just times out. However, it does not say "cannot find host" or anything else except the timeout.
 
What am I missing? How can I configure PuTTY to use the VPN connection instead of my usual SSH2 transport? Do I need to do more on my Linux host in this situation? Or get the facility to forward ports specifically (which is like pulling teeth)? Set up a tunnel in PuTTY?
 
 
An oddity - the Sonicwall VPN client software show the "Virtual IP Address" to the same as its own computer's IP address. I thought this Virtual IP was to appear to be on the same LAN to allw communication.
 
Thoughts or educational links appreciated.

---

