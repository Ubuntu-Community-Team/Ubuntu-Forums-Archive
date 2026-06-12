---
title: "Have direct to modem connection, not through switch"
date: 2006-04-19
forum: Networking &amp; Wireless
---

### Post by AndyCampbell on 2006-04-19
This is my first post so please be gentle.  I have both a XP box and one running 5.10 and I wanted to be able to switch back and forth.  I got a KVM and now I'm trying to get both on the network at the same time.  I bought a ethernet switch at CompUSA and here's the problem.  If I connect the PCs to the switch I get green lights for both PCs but the Ubuntu box can't find the network.  The XP one can.  If I connect the Ubuntu box direct to the modem it works fine.  I have tried connectting through the switch with the XP box off, still no connection through the switch.  No changes in settings in either PC, it's just the Ubuntu box won't connect through the switch, only directly through the modem.  I have done a few searches and can't find anything that directly applies to my problem or just missed it.  It's just strange to me. Why it will connect direct to the modem but not through the switch like the XP box will.

---

### Post by worty on 2006-04-20
Welcome to the boards!
I'm by no means an expert, but I'm confused as to what's going on here. Could you give us some more information? 

Are you trying to go online?
Do you have a direct connection or do you need to use pppoe?
What do you mean by connect direct to the modem?

---

### Post by AndyCampbell on 2006-04-20
Thanks for the welcome.  First let me say that Ubuntu is the best distro that I have used and I've tried a few.  Out of the box it found all my basic hardware and got my network connection up and working right away.  Sure the scanner won't work but the digital camera will.  That's more than I can say for other distros.  Anyway, to the problem at hand.  My internet is cable and my connection is through eth0.  When I say direct connect I mean I plug one end of my ethernet cable into the NIC at the back of the box and the other end into the cable modem.  That works fine.  Ubuntu finds my network connection and I'm online.  The problem is when I use the switch.  I plug the cables from the XP and Ubuntu boxes into the switch and the switch into the modem and only the Windows box sees a network connection.  Ubuntu doesn't see the connection at all  The lights are on on the switch for the Ubuntu connection but Ubuntu can't see or find it.

---

### Post by AndyCampbell on 2006-04-20
Found the fix and it had nothing to do with Ubuntu.  All I had to do is pay Cox $6.95 a month for a second IP address.  Now both PCs are online through the switch at the same time.

---

