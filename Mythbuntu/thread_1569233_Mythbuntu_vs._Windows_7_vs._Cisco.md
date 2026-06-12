---
title: "Mythbuntu vs. Windows 7 vs. Cisco"
date: 2010-09-06
forum: Mythbuntu
---

### Post by wilma92010 on 2010-09-06
Hi There!

I had to replace my router, have a new Cisco/Linksys e1000 router.   Everything is connected and my Win 7 and Mythbuntu have internet.

Things are just peachy except for one thing.   I can't ping/vnc/ssh from windows 7 to mythbuntu unless I go "outside," meaning via my external IP address (but generally keep this disabled via the router).   So 192.168.1.8 (Win 7 via DHCP) cannot ping 192.168.1.12 (Mythbuntu via manual).   Mythbuntu can ping Win 7.   

I suspect that there is some Win 7 application is blocking this (sorry if this makes the post off-topic), but don't know what it would be.  Firewall is disabled and I've tested without anti-malware/anti-virus.  

Any suggestion would be appreciated.

Wilma

---

### Post by ian dobson on 2010-09-06
Hi,

run ipconfig on your windows box, run ifconfig on your ubuntu box and compare the results subnet mask.

Can both boxes ping your router? Can your ubuntu box ping your windows box?

Regards
Ian Dobson

---

### Post by wilma92010 on 2010-09-06
Hi Ian,

Yes, both boxes can ping the router (192.168.1.1 :)) and the mythbuntu box can ping the Windows 7 box. 

The netmask for both is 255.255.255.0.  

Wilma

---

### Post by ian dobson on 2010-09-06
Hi,

Then something is abit screwed up in Windows. If you can ping your router then the basic networking is OK. Do you have a switch you can use to see if windows can ping ubuntu when no router is available.

Or can you try manually setting your windows ip address.

Regards
Ian Dobson

---

### Post by Chewiesw on 2010-09-07
I recently had issues with Windows 7 and Mythtv.

Check your Windows 7 - Network and Sharing Center settings

Check that you have _Turn on network discovery_ on

and

Turn off password protected sharing

---

