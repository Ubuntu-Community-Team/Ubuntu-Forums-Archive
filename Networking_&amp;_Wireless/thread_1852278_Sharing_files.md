---
title: "Sharing files"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by luckymoonboy1 on 2011-09-29
OK, here is my problem. I am trying to share files via an Ethernet connection from a win7 laptop and an ubuntu 11.04 desktop. Now before people yell at me to go and get samba, here is where the problem lies. I have samba, and the packages for file sharing. And my file sharing works every 1 in 8 times. Last night i was able access my ubuntu shares from my win7 laptop but not the other way around. Now, only the next day, with no change in setting there is not even any packet transmission being received by the win7 computer. Now i have been messing with every single tutorial i can find and none of it helps. Most show that there is a samba button under system or some other location. i have no such button, anywhere. I installed samba through the software center when i had the internet on the ubuntu computer, and last night when it said i didnt have it i manualy downloaded it and installed it and it made it all work. However today, it is once again not working. I am utterly lost. I have tried a million and one setting adjustments and tutorials and it is all starting to blur together. If anyone knows of any logs or something i need to post, tell me and i will. I really, really, need to get this resolved.

Also, if i adjust it so that the IP addresses are the same, windows alerts me to the IP conflict, receives 60 packets from the ubuntu computer and stops doing anything.

---

### Post by collisionystm on 2011-09-29
All you had to do in ubuntu was right click the folder and hit share. On your windows machine go to start, in the search box type run, hit enter. In the runbox type \\ipofubuntu

---

### Post by luckymoonboy1 on 2011-09-29
THANK YOU!!! Now, just out of curiosity, why will that work but but it won't show up in my Network folder?

---

### Post by collisionystm on 2011-09-29
Because windows likes to use netbios aka wins. Ubuntu does not support that. I'm on an iPhone so it's hard to explain lol

---

### Post by luckymoonboy1 on 2011-09-29
Oh, ok, kool, Thanks again. This is a life saver.

---

### Post by sandrodz on 2011-10-20
> **collisionystm said:**
> Because windows likes to use netbios aka wins. Ubuntu does not support that. I'm on an iPhone so it's hard to explain lol
samba supports wins.

---

### Post by capscrew on 2011-10-20
> **sandrodz said:**
> samba supports wins.

Samba supports the use of WINS in only in some instances.  WINS is NOT NETBIOS though.  NETBIOS can use a WINS server to maintain the database of NETBIOS names to IP addresses.  On a single segment LAN you do not need WINS and Samba discourages it.  Windows also does not use a WINS server for single segment LAN's.  Both systems use b-node configuration (bcast) to exchange NETBIOS names.  The Master Browse List is maintained by one of the hosts on the LAN (by election) but it is not a WINS server either.  Complicated, but it works.  :-)

---

### Post by capscrew on 2011-10-20
> **collisionystm said:**
> Because windows likes to use netbios aka wins. Ubuntu does not support that. I'm on an iPhone so it's hard to explain lolYou're right Ubuntu does not have a need for NETBIOS, but Samba does.  Windows at this point (W7) also only uses NETBIOS for legacy apps.

Samba can convert DNS names into NETBIOS names (in 2 different ways) and all Samba and Windows shares (SMB/CIFS) still ultimately use NETBIOS names to resolve IP to COMPUTER names (NETBIOS) for share browsing.

---

