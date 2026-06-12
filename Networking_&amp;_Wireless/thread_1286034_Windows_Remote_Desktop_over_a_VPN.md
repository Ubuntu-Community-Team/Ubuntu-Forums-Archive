---
title: "Windows Remote Desktop over a VPN"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by zak89 on 2009-10-08
Greetings all,

I am trying to set up a remote desktop connection to a work computer on a VPN. I have gotten a connection to the VPN (from my Ubuntu installation), and I am now trying to setup a remote desktop client (trying tsclient right now) so I can use my remote Windows PC on the VPN. 

The only issue I have is that I don't know how to "tell" tsclient that I want the rdesktop connection made over my VPN connection. I am assuming that one of the options on tsclient's configuration dialog should have the vpn gateway address, but I don't know which.

Here are the tsclient options I am wondering about:

"Computer:" - Hmm? Would this be the local ip address of the remote machine?

"Domain:" - Would this be my vpn gateway address? Like "vpn.myvpn.com"?

"Client Hostname:" - What's the difference between the "Client Host Name" and "Computer"? 

"Protocol File:" - Don't have one; I'm assuming this is optional?

I'd appreciate a little help on this issue, as it's the only way I can use my Ubuntu installation for work. Thanks!

---

### Post by spd106 on 2009-10-09
You only really need to enter the hostname or IP address of the computer you want to connect to in the Computer Name box then click connect, the other boxes are optional.

The protocol file allows you to store the settings you would use to connect, which makes it quicker/easier next time or allows you to distribute the settings to others.

---

