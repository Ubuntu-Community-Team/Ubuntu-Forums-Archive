---
title: "Problem Browsing Windows 7 Shares via Samba"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by phane on 2011-04-04
Someone recommended I start this in it's own thread to try to get more help.

I've followed the guide [here]("http://ubuntuforums.org/showthread.php?t=1169149") already, and posted most of this info starting on [post 512]("http://ubuntuforums.org/showthread.php?t=1169149&page=52").

The general idea is that I was able to browse all of my shares on my Windows server and print to the printer until a few weeks ago, when it all suddenly stopped working for no explicable reason.  The server is running Windows 7 Home Premium SP1 x64, all linux computers are running Ubuntu 10.10 x64.  At one point, my Xoom couldn't connect either, but that issue seems to have resolved itself, all Windows computers and my PS3 can connect to the shares just fine.

My network layout is set up like this:
```
Internet <--> Ooma <--> IP Cop <--> Switch <--> LAN
                                       ^
                                       |
                                       v
                                     E3000 <--> WLAN
```

I can't browse either via LAN or WLAN using 4 different Ubuntu 10.10 x64 computers.  I tried disconnecting IP Cop from the switch so it was just raw LAN and it still doesn't work.  I can manually connect using Connect to Server and manually inputting the IP address and share name, but whenever I browse to Windows Networks it shows absolutely nothing, even after manually connecting.  After connecting via IP address manually, I can connect via hostname, but if I unmount all the connections, hostname won't work anymore.  Pinging the hostname works fine.  The hostname is defined through IP Cop's DNS, not through WINS.

All smb.conf settings are default except for changing the workgroup to match the server.  I've tried the other settings in the above tutorial and they made no difference.  This config WAS working across the board 3 weeks ago.

I don't have Windows Live Assistant installed, I set up the sharing settings in windows properly, I've tried disabling Windows Firewall altogether and don't run any third party software firewalls.

---

