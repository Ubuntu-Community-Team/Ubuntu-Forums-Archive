---
title: "[Networking] Server Hosting Problem"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by 0akash0 on 2011-05-08
Dear Geniuses,

Hi, I am using Ubuntu 10.10 AMD64 (a bit dated, I know). 

Background Info:

I have installed MONO, Mysql server, apache 2, and other sundries. Using NaviCat for Database. I wanted to host a game server coded in java. Used the terminal to execute Jar. It is expected to run under windows, but I thought it would not be a problem to run in ubuntu. The game server uses database form navicat.

Network Info:

Random IP, connection to server through 2 routers: Wired (ADSL2+) > Wireless > Computers. Required ports are (seemingly) open. ISP: MTNL Mumbai.

Problem:

Once the server is running, it notifies that the ports are open, and it is accepting incoming connections. However, not even me from my own computer on which the server is hosted can access it through the game.

I tried hosting the same on a windows machine. When it was connecting through Hamachi to Windows machine, it was working. Under similar setup of Ubuntu (direct IP), it does not work on windows either. So I figured it was a network related issue.

Question:

How can I make it so that the remote clients can connect to my computer using nothing but IP? If that is not possible, is there an alternative to Hamachi for VPN? Is there a good cross platform VPN without restrictions?

Is the problem specific to my ISP / Computer? If I shift to a VPS, will I still face this problem? I am considering VPS only because I think there may be something wrong with my ISP / Computer / Network Setup.

Please Help.
Thanking you in advance.

EDIT: Further Additional Info:

My guess it that, the client software is not capable of finding exactly which computer the server is running on. If Hamachi IP is specified, it works fine, as the IP corresponds to the the server directly. My Random IP simply means any of the computers connected to the wireless router.

---

