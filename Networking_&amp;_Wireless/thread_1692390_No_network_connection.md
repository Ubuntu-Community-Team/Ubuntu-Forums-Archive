---
title: "No network connection"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by pbstar25 on 2011-02-21
Hey Everyone,

I have a dual boot system Ubuntu 10.10 and Windows 7 Ultimate. I have been running Ubuntu for 4 months and windows for 1 month. I hadn't had a network issue with either system until Friday. I booted into ubuntu and while it was booting some red text flashed on the screen but it was too quick to read. When I logged in and tried to get on the internet I couldn't get to any pages. So I tried just to talk to my router and I couldn't do that either. I rebooted into windows and my network/internet works fine. Any ideas about what could have changed? I don't recall doing anything that would have changed my network settings. I could be wrong about this but I seem to remember getting a system update the last time I was successfully online so I don't know if there could have been something in the update that caused this.

Thanks in advance for the help!

---

### Post by mihaimm on 2011-02-21
Some details would be helpful... wifi/eth? What's Network Manager saying?

---

### Post by pbstar25 on 2011-02-21
Sorry

Its hardwired.

What do you mean, what is network manager saying? 
     -I have no IP address

Thanks

---

### Post by pbstar25 on 2011-02-21
I have no idea if this helps but under "network connections" the only one listed is "Auto eth0" and under the "last used" column it says "never". I cannot say for sure that this ever said anything different but "Auto eth0" has certainly been used before.

---

### Post by mihaimm on 2011-02-21
Well... considering Ubuntu 10.10 you should have a little icon that looks like a disconnected Wifi thing on the top-right corner. 

When clicking on that you should have a list of devices (not devices really, but you should have Wired Connection -> Auto eth0). When clicking on Auto eth0 it should try to reconnect to the network. 

If that doesn't work, open a terminal, type into it 'tail -f /var/log/messages' and do that again (click on the Auto eth0 on Network Manager). Then spill the logs here ;).

---

### Post by pbstar25 on 2011-02-21
When I click on that I see "Wired Network" and below that "disconnected" and they are both greyed out.

---

### Post by pbstar25 on 2011-02-21
I am not sure why this fixed it but I just right-clicked on the network icon, uncheck "Enable Network" and then rechecked "Enable Network" and I am up an running.
 
Thank you for the help

---

