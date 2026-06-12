---
title: "Ubuntu 10.04 + Wireless + SMB share/ping/SABnzbd connection from windows times out"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by lorands on 2010-05-26
All,

I am running an x64 AMD Ubuntu 10.04 clean install. I am using a USB wireless device (Ralink 3070 compatible) connecting to a WPA2 AES network. The system has two SMB windows shares and also has SABnzbd configured to run listening on the network on port 8100.

If I'm using the system itself, I can access the internet all the time as well as notice that I have no problem downloading from newsgroups and browsing the web at the same time (the connection is not saturated). When attempting to access the system from any of the other computers on the network I find I run into a problem. If the system has just recently connected to the AP/network via wireless, I can ping it, http to SABnzbd's web-config, or even access the SMB shares.

After a period of ~20-60 minutes (not sure, seems random!) it becomes inaccessible. It is still completely operational however it can not be accessed from an external system any more. If I force it to reconnect to the AP, then I will be able to access it from a remote system again for a random amount of time - rinse and repeat. If I plug the system into the Ethernet directly (rj45, hard-wired) I don't get this problem at all.

There is no firewall / iptables set up. Please help, it's driving me insane.

---

### Post by jph000 on 2010-06-08
lorands' post from a week ago sounds like the same problem I encountered today.

Ubuntu 10.04 LTS PC is on wireless local area network (WLAN). WLAN uses WPA2 Personal. PC's IP is 192.168.1.100. Problem is reproducible. Network presence is okay for an hour to an hour and a half (around 60 to 90 minutes) and then PC is unreachable via ping from another computer on the same WLAN. However, Internet access on PC in question still works, using Firefox. Using the wireless icon in the menu bar to disconnect and then reconnect to the same wireless LAN restores network presence, that is, the PC can again be successfully ping'd from another PC on the same LAN.

PC running Ubuntu is dual bootable into Ubuntu or Windows XP Pro using separate internal hard drives. Windows XP Pro boot is configured the same as Ubuntu for WLAN. Windows XP Pro PC presence is stable, that is, pinging the PC remains okay over hours. Also, PC is set to never sleep in both cases.

---

### Post by lorands on 2010-07-13
I guess no one else has come across this error?

I'm going to try with a different wireless adapter - don't know what else to do. Any suggestions on a working out-of-the-box adapter from say [www.dealextreme.com](www.dealextreme.com) that's relatively cheap and works without needing any driver modifications?

---

