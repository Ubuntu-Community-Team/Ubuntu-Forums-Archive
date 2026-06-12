---
title: "Wired Network Disappeared"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by RogerDavis on 2010-07-02
On the next reboot after the latest updates to 10, I have no wired internet connection. If I look under Network Connections, there is no wired connection listed. I can't get a new one working.

I don't use wireless on this machine, no card, etc.

Using the same machine booting Windows on a different hard drive, it works fine.

How can I revive the Ubuntu wired connection?

Thanks!

---

### Post by Iowan on 2010-07-02
IF you right-click NM icon, does it show networking enabled? (Other threads have mentioned that updates sometimes disable networking.) If networking is enabled, check **sudo lshw -C network** to verify your interface still has an alias and driver. **ifconfig -a** should show all available interfaces, but if it doesn't show on NM, it might not be in **ifconfig** either.

---

### Post by RogerDavis on 2010-07-02
using "sudo lshw -C network", I get NETWORK DISABLED.

Please note that I'm not anywhere near a wizard with terminal commands, I found this somewhere else and tried it.

---

### Post by RogerDavis on 2010-07-02
DUH...  I'm embarassed it's so simple, but to help others :

The networking icon at the top right of the screen showed disabled when right-clicked.  This happened shortly after the last update, I didn't do it myself.  Is this the "NM" you mentioned?

To fix - click ENABLED.  Works fine now...

---

### Post by Iowan on 2010-07-02
:oops: Yeah... NM = Network Manager. That's the "networking icon" you mentioned. Shame on me for being too lazy to type it out... Glad you found a solution. 
If it STAYS fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

---

### Post by RogerDavis on 2010-07-30
I see now with the passage of time that it occasionally turns itself off when the machine is turned off.  When I start it again, the network is awol.

---

