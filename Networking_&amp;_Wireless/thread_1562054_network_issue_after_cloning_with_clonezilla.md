---
title: "network issue after cloning with clonezilla"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by dwvm3 on 2010-08-27
Hello,
I have a strange problem with Ubuntu 10.04. I use several identical PC's (Atom N330 with NVidia Ion from Foxcon). To setup the PC's, I installed Ubuntu 10.04 on one machine. This machine works perfect. Then I save the disk with Clonezilla and restore it to the other machines.

From time to time, the clones don't have a (wired) networck connection. The network manager says "disconnected" and trying to reconnect does not work. Then I discovered that suddenly there are two network interfaces, the one from the "mother machine" and a new one called "automatically generated interface" or, on some other clones, "eth1" or "eth2". This extra interfaces are there since the firt boot of the clones. If I reboot a clone, then it gets it network back, but from time to time it comes up with no network.

To solve this problem I deinstalled network-manager and gnome-network-manager and edit /etc/network/interfaces on the "mother machine" as follows:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

Then I reboot the machine. Network is working, so I use Clonezilla to make clones from the "mother machine".

But the clones don't know eth0

if i type "sudo dhclient eth0" the message is

*eth0: ERROR while getting interface flags: No such device*

Then I try "sudo dhclient eth1" and that is working. On some machines only eth2 works. If I edit /etc/network/interfaces and change eth0 to eth1 or eth2 the network on the clone machines works permanently correct.

So why is the network interface changing? 
I spend hours in searching in forums for a solution but did not find the source of this issue. Can anyone help?

Thanks in advance

---

### Post by Iowan on 2010-08-27
You may need to edit */etc/udev/rules.d/70-persistent-net.rules* and change the line with the original MAC address - or delete the line (after making a backup of the file) and let it get regenerated.

---

### Post by dwvm3 on 2010-08-27
That's it, Thank you very much.

---

### Post by Iowan on 2010-08-27
Good news - if it ***stays*** fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---

### Post by ratcheer on 2010-08-27
You are doing well - I never could get Clonezilla to work, at all.

Tim

---

### Post by dwvm3 on 2010-08-28
> **Iowan said:**
> Good news - if it ***stays*** fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

Yes, I restarted the clones about 30 times and the network was always reachable. Only three times an error message occurred saying that the applet is not working. In this case, the network manager icon in the tool bar (the two arrows) is not shown, but the network is still working. So I think it's SOLVED.:)

---

