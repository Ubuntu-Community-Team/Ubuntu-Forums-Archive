---
title: "Unable to re-activate D-Link DWL G520+ card"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by DarkStarDeity on 2006-05-04
After much frustration, swearing, and very nearly testing out the aerodynamic properties of my computer, I finally got my wireless card working on the new Ubuntu system I've just installed (yes, I'm a totally green user). Nothing I tried seemed to work - installing firmware, using ndis-wrapper, upgrading my distro via a wired connection, even installing the latest Dapper release. Annoyingly, the Network Manager would tell me that the connection was active, but since I couldn't even ping the router, I knew that was a lie. In the end, what worked was doing a completely clean install of Breezy (I'd originally installed Hoary as that was the disk I had at the time from when I'd meant to do this six months ago). Then it all just worked out of the box *facedesk*

The problem I have at the moment, though, is that I cannot re-activate the connection mid-session (eg, after changing properties to enable WEP). The connection I get at start-up is the only connection I get. Rebooting seems to be the only way to re-connect after the card has been deactivated. (In retrospect, this might account for the problems I had getting eg ndis-wrapper working in the first place.) I know I can modify the /etc/network/interfaces file to enable WEP and I'm going to try that this weekend, but I would like to sort the problem out as I don't wish to have to reboot just to reconnect after for instance a dropped connection. 

Sorry if this is already in the forum somewhere, I did search but could not find anything (although I did find a frightening number of people with my card with problems with disconnecting due to inactivity, which is why I'd like to sort this  problem out).

---

### Post by DarkStarDeity on 2006-05-05
OK, I found at least a partial solution - using ifup/ifdown wlan0 or ifconfig wlan0 up/down on the command line rather than the Network Administrator GUI tool. Sometimes I still had to reboot to re-establish a connection, but I can't say what was different about the these times. 

And I've tested re-connecting after dropping the modem connection and it both auto-reconnects and I can use these command-line utils to re-connect, so that is a weight off my mind.

---

### Post by jml on 2006-05-05
I'm glad you found a solution.  I've read on these forums that the Network Manager Application can sometimes have problems configuring a wireless card.  The solution listed was to do what you did, open a terminal and run the commands at the command line.

---

### Post by DarkStarDeity on 2006-05-05
Only a partial solution - the connection dropped for some reason (and not due to  inactivity - I was still browsing the web!)  a couple of hours after I posted that and only a reboot could get it back up. So if anyone is able to offer suggestions for that problem I'd be grateful.

---

