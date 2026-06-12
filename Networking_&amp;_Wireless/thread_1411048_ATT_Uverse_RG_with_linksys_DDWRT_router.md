---
title: "ATT Uverse RG with linksys DDWRT router"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by Cyked on 2010-02-19
I have ATT uverse internet only but obviously still using the ATT Residential Gateway.

My current setup is this:
Internet > uverse RG > linksys running ddwrt bridged in another room

I have an XP machine and an Ubuntu box wired to the linksys, which then wirelessly connects to the RG in another room.  Originally I had both machines as static IP 1.101 and 1.102.  The RG IP is 192.168.1.2, so its no the default 0.1 or whatever.  The linksys IP is 1.1 with the gateway as 1.2.  Both machines were configured with the gateway as 1.2.  For whatever reason only ONE "client" would show in the RG client list.  Usually it was the XP machine.  Even so, I would config the firewall rule for that client to fwd port 80, ssh, 3389, etc to this client.  If both machines were on it would sometimes route to the XP machine and sometimes to the ubuntu machine.  This was annoying, but usually the XP machine was off while not at home, so it was a non-issue.  

Last night I changed the XP machine to be DHCP.  It grabs the exact same information that I had set the static info to be, except it grabs 1.103-105 sometimes.  When I did this BOTH machines did in fact show up as separate clients in the list on the RG.  So I configured the XP machine with only the RDP port and left the other client (ubuntu alone).  Cool, no issues, everything works fine.  Both machines are on, I can always ssh in, always hit apache.  I can always RDP to the XP box (this was while testing, I just did this last night).

Now, this morning NOTHING shows as a client on the RG.  However, I was able to RDP to the windows box, but can't hit apache or ssh.  So I reboot the XP machine and wait a bit.  In the mean time my wife logged in, so I have to wait a bit longer (maybe 20 min total from the reboot to trying again).  She logged off, went to work, and I can't get to anything now, not even RDP to the XP machine.  

What I want to do is get BOTH machines to show up as separate clients in the RG client list AT ALL TIMES.  Is this something that won't work given that I'm running ddwrt?  I thought bridging was supposed to make everything on the network think and act like the wired/wireless clients on the ddwrt router were actually wired/wireless to the primary router.

At any rate, looking for solutions because this has been really frustrating and I feel like every time I sneeze something new comes up with this config and the ATT RG/linksys starting acting different than they were the previous day.

FWIW, I do have a second wrt54g that I've tried playing around with with little success with both ddwrt and tomato.

Any thoughts?  Is it a config issue or is the RG and as long as I have that and its an ATT device I'll have to live with it.

---

