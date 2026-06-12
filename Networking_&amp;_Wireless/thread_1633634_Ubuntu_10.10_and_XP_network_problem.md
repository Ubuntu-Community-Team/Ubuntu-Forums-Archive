---
title: "Ubuntu 10.10 and XP network problem"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by aeh on 2010-11-29
Hi

I just installed Ubuntu 10.10 on my laptop along with Vista (which was there previously) and it works ok, wireless works and I'm able to access my main computer (XP). I have yet another computer (computer 2) connected to the same network (by cable, not wireless), and I just installed Maverick as well as the U studio version, both 10.10. But from this machine I cannot access the xp machine! I could when I had 9.04, just click on the network icon and so on. The permissions are ok on the XP machine so the problem must be within computer 2....   Suggestions?

Cheers

A

---

### Post by aeh on 2010-11-29
Well I tried my laptop, wireless works perfectly, I can access XP shared folders, but with a wired connection the laptop cannot access them. 'Failed to retrieve share list from server' is what it says.

---

### Post by pricetech on 2010-11-29
Install Samba system-config-samba in Synaptic.  See if that helps.

---

### Post by aeh on 2010-11-30
Didn't work. I did a sudo ufw disable, then I was able to see the MSHOME folder, but clicking on it I got a box asking for MSHOME username and password, needless to say I didn't get past it. There was a WORKGROUPS folder also, when clicked on it produced a folder of that very same ubuntu machine. The laptop on wireless has no problems at all seeing my XP machine. Nor did the previous wired ubu installs. Apart from being wireless, of course, what does the wireless connection do differently from the wired?

---

### Post by cybergnome on 2010-11-30
The MSHOME workgroup that requested Username and Password, is the proper display for the XP home network.  The WORKGROUP display is for non-Microsoft networks, hence Ubuntu shows up here.  You should be able to log on with your username and password for the account that you used on XP to enable sharing.  As I recall, you can't authorize sharing over the network in XP from an account that doesn't have administrative privileges.

The more basic test to determine that the wired connection is good, is PING.  If you can't ping the host (XP) over the wired connection, the connection itself, i.e, cables, ports, adapter, etc., are suspect.  Start here.  Once you can ping the host successfully, you can move to network configuration issues.

---

### Post by aeh on 2010-12-01
PING gives absolutely nothing. The wired connection must work since I'm able to connect to the internet (but somehow not to the other computers). Suggestions?

---

### Post by aeh on 2010-12-02
Correction: PING works but has to be done from the command line, but still no joy....

---

### Post by aeh on 2010-12-02
I get as far as being asked for a MSHOME password, wonder what that is? It sure ain't my own password..

---

