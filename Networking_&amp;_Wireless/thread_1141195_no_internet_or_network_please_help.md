---
title: "no internet or network please help"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by monkeyslayer56 on 2009-04-28
the other day i rebooted my ubuntu 9.04 PC and now it can't connect to the network BUT it gets a ip address from DHCP when i use firefox i get server not found and when i ping it gives ping: sendmsg: Operation not permited
i flushed my iptables and but i think the problem might be in my /etc/network/interfaces as there was only the loopback in it i manuely added 
auto eth1
iface eth1 inet dhcp

i do not know if that was the right thing to put or not but i have restarted both my pc and the network connections but it will not connect i know the network cable is working fine because i have plugged it into my laptop and it worked fine and when i went to windows it also worked fine there.
please somebady anybody help me

---

### Post by monkeyslayer56 on 2009-04-28
i do not know how it got fixed but it is working now what i did was afater addding my nic to the interfaces file i removed several emulators (dos and atrie i think) and lirc i rebooted and now my network manager says no devises but i am on the INTERNET (i am posting from my desktop this time insted of my laptop) so im happy as long as it works

---

### Post by ktechman on 2009-04-28
Mark thread as solved please

---

### Post by Iowan on 2009-04-28
The old [SOLVED] is [gone]("http://ubuntuforums.org/showthread.php?t=1044714"), but I saw something about using a tag to mark it.

---

